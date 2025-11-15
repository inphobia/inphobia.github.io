---
date: 2025-09-26T02:40:54+02:00
title: reformatting drives to usable sector sizes
description: reformatting drives to usable sector sizes
params:
  eid: redist
---
# reformat

## data be gone
> [!warning]
> it goes without saying that all formatting actions are pretty
> destructive for the data on the disk. the format commands will
> wipe a drive completely with no hope of recovering the data.

but still, don't use this if sanitize disks.

> [!NOTICE]
> this needs a hba, a raid card will eat whatever instructions you
> send and spits them back out in his image, this is what arrives at
> the disk

raid card modes like jbod or passthrough often say then won't intercept
commands, tried it with the cards i have but i could not get it to work.
some raid cards can be flashed to use a hba firmware and enable passthrough,
but that's a story for another time and place.

## determining the current sector size

### by using sg_format.exe
> [!NOTE]
> in this syntax sg_format.exe is safe to use. it will not destroy
> data

```
sg_format.exe PD3
    NETAPP    X371_S164A960ATE  NA54   peripheral_type: disk [0x0]
      Unit serial number: S5JENE0R504188
      LU name: 5002538b0156bb30
Mode Sense (block descriptor) data, prior to changes:
  Number of blocks=1875385008 [0x6fc81ab0]
  Block size=520 [0x208]
Read Capacity (10) results:
   Number of logical blocks=1875385008
   Logical block size=520 bytes
No changes made. To format use '--format'. To resize use '--resize'
```

current blocksize:
> [!NOTE]
> Logical block size=520 bytes

### by using smartmontools

for usage of smartmontools see {{< elink "smartmon#show-all-statistics-smartmon-understands" "here" >}}

you'll need to use either `smartctl.exe -a` or `smartctl.exe -x` to
enable this output.

you're looking for the lines starting with:
- `Logical block size:`
  - size presented to the operating system
- `Physical block size:`
  - native size the disk uses

if the logical and physical sizes match only physical will be shown.

- 512byte logical, 4k physical:
    ```
    Logical block size:   512 bytes
    Physical block size:  4096 bytes
    ```
- 4k logical, 4k physical:
    ```
    Physical block size:  4096 bytes
    ```
- 520byte logical, 4160byte physical:
    ```
    Logical block size:   520 bytes
    Physical block size:  4160 bytes
    ```

4160byte is seldom mentioned but straightforward:
just like 4k native drives can use 512byte, the
same goes for 520byte: here to native size equivalent is 4160byte.

you can [reformat to this](#back-to-520-or-4160) as well, which is mostly useless in the context here.

### by using storcli

storcli {{< elink "storcli#hangs-and-aborts-to-quick" "hangs easily" >}}, this includes when 520byte disks are attached. i recommend the 2 previous options.

calling {{< elink "storcli" "storcli" >}} with the argument `/c0 show` will have the
sector size under the heading SeSz.

```
-------------------------------------------------------------------------
EID:Slt DID State DG       Size Intf Med SED PI SeSz Model            Sp
-------------------------------------------------------------------------
0:12      1 JBOD  -   13.972 TB SAS  SSD -   -  512B X670_S164315TATE -
3:1       4 JBOD  -  894.253 GB SAS  SSD -   -  4 KB X371_S164A960ATE -
-------------------------------------------------------------------------
```

## reformatting to a different blocksize
we have the option to reformat to 512byte or 4k. you can either check
the datasheet of the drive or trust what
[smartmontools](#using-smartmontools)
says.

- 4k (preferred)
  - the modern standard
  - you can theorycraft how this is faster, in reality this you won't notice even in benchmarks
- 512byte (fallback)
  - when your controller or expander does not support 4k
  - for legacy boot options

### changing to 4k
this uses switch `--size=4096`

```
>sg_format.exe  --format --size=4096 PD3
    NETAPP    X371_S164A960ATE  NA54   peripheral_type: disk [0x0]
      Unit serial number: S5JENE0R504188
      LU name: 5002538b0156bb30
Mode Sense (block descriptor) data, prior to changes:
  Number of blocks=1875385008 [0x6fc81ab0]
  Block size=520 [0x208]

A FORMAT UNIT command will commence in 15 seconds
    ALL data on PD3 will be DESTROYED
        Press control-C to abort

A FORMAT UNIT command will commence in 10 seconds
    ALL data on PD3 will be DESTROYED
        Press control-C to abort

A FORMAT UNIT command will commence in 5 seconds
    ALL data on PD3 will be DESTROYED
        Press control-C to abort

Format unit has started
Format unit in progress, 6.86% done
Format unit in progress, 13.85% done
Format unit in progress, 20.84% done
Format unit in progress, 27.84% done
Format unit in progress, 34.83% done
Format unit in progress, 41.82% done
Format unit in progress, 48.81% done
Format unit in progress, 55.81% done
Format unit in progress, 62.80% done
Format unit in progress, 69.79% done
Format unit in progress, 76.78% done
Format unit in progress, 83.78% done
Format unit in progress, 90.77% done
Format unit in progress, 97.76% done
FORMAT UNIT Complete
```

### changing to 512 byte
this uses switch `--size=512`

```
>sg_format.exe  --format --size=512 PD6
NETAPP    X371_S164A960ATE  NA54   peripheral_type: disk [0x0]
Unit serial number: S5JENE0R502224
LU name: 5002538b01564070
Mode Sense (block descriptor) data, prior to changes:
Number of blocks=1875385008 [0x6fc81ab0]
Block size=520 [0x208]

A FORMAT UNIT command will commence in 15 seconds
ALL data on PD6 will be DESTROYED
Press control-C to abort

A FORMAT UNIT command will commence in 10 seconds
ALL data on PD6 will be DESTROYED
Press control-C to abort

A FORMAT UNIT command will commence in 5 seconds
ALL data on PD6 will be DESTROYED
Press control-C to abort

Format unit has started
Format unit in progress, 6.93% done
Format unit in progress, 14.00% done
Format unit in progress, 21.07% done
Format unit in progress, 28.13% done
Format unit in progress, 35.19% done
Format unit in progress, 42.26% done
Format unit in progress, 49.32% done
Format unit in progress, 56.38% done
Format unit in progress, 63.45% done
Format unit in progress, 70.50% done
Format unit in progress, 77.56% done
Format unit in progress, 84.62% done
Format unit in progress, 91.69% done
Format unit in progress, 98.75% done
FORMAT UNIT Complete
```

### back to 520 or 4160
dumb idea unless you have a very specific reason. windows will not be able to write data t
these disks.

you can use `--size=520` and `--size=4160` should you need have a need to. i haven't tested
if the system the drive originally came will accept them again. i'd say chances are slim.
