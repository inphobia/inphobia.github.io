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
