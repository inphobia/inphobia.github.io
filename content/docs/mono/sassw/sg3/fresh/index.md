---
date: 2025-10-20T02:55:31+02:00
title: fresh
description: fresh
params:
  eid: fresh
---
# TODO

## find drive

`PD24            <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R504438`

## upload drive firmware

```
sg_write_buffer.exe -b 4k -m dmc_offs_save -I X371_S164A960ATE.NA55.LOD PD24
```

## sg_scan might not show updated firmware directly


## powercycle
flashing the firmware should be an online operation (so without impact), i do recommend
powercycling either the disk or preferably the pc. this means shutting down your device and
powering it back up. a reboot alone might keep the disk powered on, which we don't want.
