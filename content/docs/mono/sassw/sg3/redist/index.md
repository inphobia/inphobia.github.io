---
date: 2025-09-26T02:40:54+02:00
title: reformatting drives to usable block sizes
description: reformatting drives to usable block sizes
params:
  eid: redist
---
# todo flesh out

## option1: format 512
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

## option2: format 4k
```
>sg_format.exe  --format --size=4096 PD7
NETAPP    X371_S164A960ATE  NA54   peripheral_type: disk [0x0]
Unit serial number: S5JENE0R502223
LU name: 5002538b01564060
Mode Sense (block descriptor) data, prior to changes:
Number of blocks=1875385008 [0x6fc81ab0]
Block size=520 [0x208]

A FORMAT UNIT command will commence in 15 seconds
ALL data on PD7 will be DESTROYED
Press control-C to abort

A FORMAT UNIT command will commence in 10 seconds
ALL data on PD7 will be DESTROYED
Press control-C to abort

A FORMAT UNIT command will commence in 5 seconds
ALL data on PD7 will be DESTROYED
Press control-C to abort

Format unit has started
Format unit in progress, 6.82% done
Format unit in progress, 13.78% done
Format unit in progress, 20.73% done
Format unit in progress, 27.68% done
Format unit in progress, 34.63% done
Format unit in progress, 41.58% done
Format unit in progress, 48.53% done
Format unit in progress, 55.47% done
Format unit in progress, 62.42% done
Format unit in progress, 69.37% done
Format unit in progress, 76.31% done
Format unit in progress, 83.25% done
Format unit in progress, 90.20% done
Format unit in progress, 97.15% done
FORMAT UNIT Complete
```
