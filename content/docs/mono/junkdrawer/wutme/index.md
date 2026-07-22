---
date: 2025-09-27T00:09:36+02:00
title: current setup
description: current setup
params:
  eid: wutme
---
# what am i actually running

workflows have a note of what the initial hardware was when i started, but parts
get swapped in and out ofcourse. so here i'll give an overview of the full setup
i'm running. don't expect this to be updated daily. it will be updated when
noteworthy changes happen. if none happen i'll update it every 3 months or so.

the history of this page (and the rest of the site) is kept on github, last change date is on the bottom of the page.

## battlestation
 - windows 11 pro 25h2 26200.8894
 - amd ryzen 7 9800x3d
 - scythe mugen 6 black edition
 - {{< elink "x670e" "asrock x670e pg lightning motherboard" >}}, uefi 4.10
 - 2 m.2 sn850x black 8tb drives, fw 638211wd
 - asrock challenger radeon rx 9060 xt oc 16gb
 - antec p20ce case (includes 3 120mm fans)
 - 3 arctic p14 pwm pst case fans
 - {{< elink "topre" "realforce 1 105key iso layout" >}}

### cleaned it just for this picture
![](likenew.jpg)

## sas specific - permanent setup

these devices are always installed and powered up

### hba

{{< elink "b9500-16e" "broadcom 9500-16e" >}}

```
Model = HBA 9500-16e
Firmware Package Build = 38.00.00.00
Firmware Version = 38.00.00.00
Bios Version = 09.75.00.00_38.00.00.00
NVDATA Version = 38.00.00.14
PSOC FW Version = 0x006E
PSOC Part Number = 14790
Driver Name = ItSas35
Driver Version = 2.61.87.00
```

### storcli

{{< elink "storcli" "storcli" >}}

`CLI Version = 007.3703.0000.0000 Jan 16, 2026`


### external to internal sas converter
{{< elink "ieconv" "startech sff86448plt2" >}}
#### connect with a 0.5m cable
![looks like this](inout.jpg)

### internal sas drive

```
------------------------------------------------------------------------
EID:Slt DID State DG      Size Intf Med SED PI SeSz Model            Sp
------------------------------------------------------------------------
0:12      1 JBOD  -  13.970 TB SAS  SSD -   -  4 KB X670_S164315TATE -
------------------------------------------------------------------------

Manufacturer Id = NETAPP
Model Number = X670_S164315TATE
NAND Vendor = NA
Firmware Revision = NA56
Raw size = 13.970 TB [0xdf87ffff Sectors]
Coerced size = 13.970 TB [0xdf87ffff Sectors]
Non Coerced size = 13.970 TB [0xdf87ffff Sectors]
Device Speed = 12.0Gb/s
Link Speed = 12.0Gb/s
Negotiated Physical Link Rate = 12.0Gb/s
Sector Size = 4 KB
Config ID = NA
Number of Blocks = 3750232063
Connector Name = C3   x1
```


### sg3utils

am using a {{< elink "arise" "self built" >}} version of {{< elink "sg3utils" >}}
based on git commit https://github.com/doug-gilbert/sg3_utils/commit/dc19214f48edf5a652ed9351f8f2e9489ff046d4

### smartmontools

 {{< elink "smartmon" "smartmontools" >}}

version

```
smartctl pre-8.0-446 2026-05-20 [x86_64-w64-mingw32-w11-25H2] (GHA Build)
smartmontools release pre-8.0-446
smartmontools git revision c44c74b2c3dc dated 2026-05-20 at 15:00:48
smartmontools build host: x86_64-w64-mingw32
smartmontools build with: C++11, GCC 14-win32, MinGW-w64 12.0.0, GNU libstdc++ 20250315
reproducible build SOURCE_DATE_EPOCH: 1779289248 (2026-05-20 17:00:48)
```

## sas specific - adhoc

these devices get powered on when needed.

### netapp ds224c diskshelfs
 - 3 shelves
 - 2 power supplies each
 - 2 iom12a fw0401 each
 - around 50 x371 sas ssd drives

### optical tower
wip
