---
title: non obvious limitations
description: non obvious limitations
params:
  eid: oops
---
# unexpected limitations

## no sata 1.5gbps support (optical drives)
starting from the 9300 series broadcom no longer mentions support for 1.5gbps sata, only 3gbps & 6gbps. this should not be an issue for disk drives, but optical drives (cd, dvd, blu-ray) most often use 1.5gbps connections.

## no sata 3gbps support
broadcom's 9600 series only supports 6gbps sata

## alternative sata support
you can add a {{< elink "82885t" "adaptec 82885t" >}} and restore that

## lto (tape) support
broadcom states the 9500 series should support lto drives but they do not explicitly test this. the 9600 series however has no current nor plannned support for lto drives (likely due to not supporting "transport layer retries").

## 528byte disks
show up in storcli as ubad with 512byte:
`38:2     59 UBad  -        0 KB SAS  HDD     -   -  512B ST300MM0048      -`

smartctl doesn't help a lot either:

```
smartctl.exe -x /dev/sddb
smartctl 7.5 2025-04-30 r5714 [x86_64-w64-mingw32-w11-b26200] (AppVeyor)
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               SEAGATE
Product:              ST300MM0048
Revision:             N0A1
Compliance:           SPC-4
LU is fully provisioned
Rotation Rate:        10500 rpm
Form Factor:          2.5 inches
Logical Unit id:      0x5000c5009ed1e48b
Serial number:        W0K06N9G0000K733A5VJ
Device type:          disk
Transport protocol:   SAS (SPL-4)
Local Time is:        Sun Oct 19 20:41:04 2025 RDT
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Enabled
Read Cache is:        Enabled
Writeback Cache is:   Disabled

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Format status indicates no format since manufacture
Current Drive Temperature:     28 C
Drive Trip Temperature:        60 C

Manufactured in week 08 of year 2017
Specified cycle count over device lifetime:  10000
Accumulated start-stop cycles:  54
Specified load-unload count over device lifetime:  300000
Accumulated load-unload cycles:  2040
Read defect list: asked for grown list but didn't get it
Vendor (Seagate Cache) information
  Blocks sent to initiator = 140701
  Blocks received from initiator = 34169611
  Blocks read from cache and sent to initiator = 3826
  Number of read and write commands whose size <= segment size = 7304
  Number of read and write commands whose size > segment size = 0

Vendor (Seagate/Hitachi) factory information
  number of hours powered up = 47823.47
  number of minutes until next internal SMART test = 59

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:     230781        0         0    230781          0          0.072           0
write:         0        0         0         0          0         17.556           0

Non-medium error count:        2


[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
SMART Self-test log
Num  Test              Status                 segment  LifeTime  LBA_first_err [SK ASC ASQ]
     Description                              number   (hours)
# 1  Background short  Completed                   -       3                 - [-   -    -]
# 2  Background short  Completed                   -       2                 - [-   -    -]
# 3  Background short  Completed                   -       2                 - [-   -    -]

Long (extended) Self-test duration: 1900 seconds [31.7 minutes]

scsiPrintBackgroundResults Failed [medium or hardware error (serious)]
Device does not support General statistics and performance logging

Protocol Specific port log page for SAS SSP
relative target port id = 1
  generation code = 0
  number of phys = 1
  phy identifier = 0
    attached device type: expander device
    attached reason: SMP phy control function
    reason: power on
    negotiated logical link rate: phy enabled; 12 Gbps
    attached initiator port: ssp=0 stp=0 smp=1
    attached target port: ssp=0 stp=0 smp=1
    SAS address = 0x5000c5009ed1e489
    attached SAS address = 0x500a0980085b31e1
    attached phy identifier = 18
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 0
    Phy reset problem count = 1
relative target port id = 2
  generation code = 0
  number of phys = 1
  phy identifier = 1
    attached device type: expander device
    attached reason: SMP phy control function
    reason: unknown
    negotiated logical link rate: phy enabled; 12 Gbps
    attached initiator port: ssp=0 stp=0 smp=1
    attached target port: ssp=0 stp=0 smp=1
    SAS address = 0x5000c5009ed1e48a
    attached SAS address = 0x500a098007ea8759
    attached phy identifier = 18
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 0
    Phy reset problem count = 1
```


see Block size=528
```
sg_format.exe  --format -s 512 PD105
    SEAGATE   ST300MM0048       N0A1   peripheral_type: disk [0x0]
      << supports protection information>>
      Unit serial number: W0K06N9G0000K733A5VJ
      LU name: 5000c5009ed1e48b
Mode Sense (block descriptor) data, prior to changes:
  Number of blocks=557874778 [0x21407e5a]
  Block size=528 [0x210]
```
