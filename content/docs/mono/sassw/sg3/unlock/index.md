---
draft: true
date: 2026-01-02T03:39:33+01:00
title: protection stuff
description: protection stuff
params:
  eid: unlock
---
# TODO

## for t10-pi, t10-dif and t10-dix

check - see type 2 protection
```
sg_readcap.exe -vl PD8
    read capacity(16) cdb: [9e 10 00 00 00 00 00 00 00 00 00 00 00 20 00 00]
Read Capacity results:
   Protection: prot_en=1, p_type=1, p_i_exponent=0 [type 2 protection]
   Logical block provisioning: lbpme=0, lbprz=0
   Last LBA=1953525167 (0x74706daf), Number of logical blocks=1953525168
   Logical block length=512 bytes
   Logical blocks per physical block exponent=0
   Lowest aligned LBA=0
Hence:
   Device size: 1000204886016 bytes, 953870 MiB, 1000.2 GB
```


get rid of


`sg_format.exe --format --fmtpinfo=0 -v PD8`

`--pfu=0` also needed?

