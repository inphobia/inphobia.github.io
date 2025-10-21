---
date: 2025-10-21T02:48:03+02:00
title: dskfw
description: dskfw
params:
  eid: dskfw
---
# flashing disk firmware

## get detailed disk info
you'll see this disk is currently running firmware `na55`

```
>storcli64.exe /c0/e0/s12 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = Show Drive Information Succeeded.


Drive /c0/e0/s12 :
================

------------------------------------------------------------------------
EID:Slt DID State DG      Size Intf Med SED PI SeSz Model            Sp
------------------------------------------------------------------------
0:12      1 JBOD  -  13.972 TB SAS  SSD -   -  512B X670_S164315TATE -
------------------------------------------------------------------------

EID-Enclosure Device ID|Slt-Slot No|DID-Device ID|DG-DriveGroup
UGood-Unconfigured Good|UBad-Unconfigured Bad|Intf-Interface
Med-Media Type|SED-Self Encryptive Drive|PI-Protection Info
SeSz-Sector Size|Sp-Spun|U-Up|D-Down|T-Transition


Drive /c0/e0/s12 - Detailed Information :
=======================================

Drive /c0/e0/s12 State :
======================
Shield Counter = N/A
Media Error Count = N/A
Other Error Count = N/A
Predictive Failure Count = N/A
S.M.A.R.T alert flagged by drive = N/A


Drive /c0/e0/s12 Device attributes :
==================================
Manufacturer Id = NETAPP
Model Number = X670_S164315TATE
NAND Vendor = NA
SN = S40TNY0M105275
WWN = 5002538B09134AB3
Firmware Revision = NA55
Raw size = 13.972 TB [0x6fc7cd2af Sectors]
Coerced size = 13.972 TB [0x6fc7cd2af Sectors]
Non Coerced size = 13.972 TB [0x6fc7cd2af Sectors]
Device Speed = 12.0Gb/s
Link Speed = 12.0Gb/s
Negotiated Physical Link Rate = 12.0Gb/s
Sector Size = 512B
Config ID = NA
Number of Blocks = 30005842607
Connector Name = C3   x1


Drive /c0/e0/s12 Policies/Settings :
==================================
Enclosure position = 0
Connected Port Number = 8(path0)
Sequence Number = 0
Commissioned Spare = No
Emergency Spare = No
Last Predictive Failure Event Sequence Number = N/A
Successful diagnostics completion on = N/A
SED Capable = N/A
SED Enabled = N/A
Secured = N/A
Needs EKM Attention = N/A
PI Eligible = N/A
Certified = N/A
Wide Port Capable = N/A
Multipath = No

Port Information :
================

-----------------------------------------
Port Status Linkspeed SAS address
-----------------------------------------
   0 Active 12.0Gb/s  0x5002538b09134ab1
-----------------------------------------


Inquiry Data =
00 00 07 12 c5 00 10 03 4e 45 54 41 50 50 20 20
58 36 37 30 5f 53 31 36 34 33 31 35 54 41 54 45
4e 41 35 35 30 4d 31 30 35 32 37 35 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 a0 0c 60 05 c0
ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
56 46 54 35 57 46 41 51 32 32 31 31 30 38 5f 48
5f 30 f0 f8 30 56 30 30 53 41 4d 53 55 4e 47 20
```

## upload new firmware
updating to fw version `na56`

```
>storcli64.exe /c0/e0/s12 download src=X670_S164315TATE.NA56.LOD mode=7
Starting microcode update.please wait...
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = Firmware Download Succeeded.
```

## check
na56 is active now

```
>storcli64.exe /c0/e0/s12 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = Show Drive Information Succeeded.


Drive /c0/e0/s12 :
================

------------------------------------------------------------------------
EID:Slt DID State DG      Size Intf Med SED PI SeSz Model            Sp
------------------------------------------------------------------------
0:12      1 JBOD  -  13.972 TB SAS  SSD -   -  512B X670_S164315TATE -
------------------------------------------------------------------------

EID-Enclosure Device ID|Slt-Slot No|DID-Device ID|DG-DriveGroup
UGood-Unconfigured Good|UBad-Unconfigured Bad|Intf-Interface
Med-Media Type|SED-Self Encryptive Drive|PI-Protection Info
SeSz-Sector Size|Sp-Spun|U-Up|D-Down|T-Transition


Drive /c0/e0/s12 - Detailed Information :
=======================================

Drive /c0/e0/s12 State :
======================
Shield Counter = N/A
Media Error Count = N/A
Other Error Count = N/A
Predictive Failure Count = N/A
S.M.A.R.T alert flagged by drive = N/A


Drive /c0/e0/s12 Device attributes :
==================================
Manufacturer Id = NETAPP
Model Number = X670_S164315TATE
NAND Vendor = NA
SN = S40TNY0M105275
WWN = 5002538B09134AB3
Firmware Revision = NA56
Raw size = 13.972 TB [0x6fc7cd2af Sectors]
Coerced size = 13.972 TB [0x6fc7cd2af Sectors]
Non Coerced size = 13.972 TB [0x6fc7cd2af Sectors]
Device Speed = Unknown
Link Speed = 12.0Gb/s
Negotiated Physical Link Rate = 12.0Gb/s
Sector Size = 512B
Config ID = NA
Number of Blocks = 30005842607
Connector Name = C3   x1


Drive /c0/e0/s12 Policies/Settings :
==================================
Enclosure position = 0
Connected Port Number = 8(path0)
Sequence Number = 0
Commissioned Spare = No
Emergency Spare = No
Last Predictive Failure Event Sequence Number = N/A
Successful diagnostics completion on = N/A
SED Capable = N/A
SED Enabled = N/A
Secured = N/A
Needs EKM Attention = N/A
PI Eligible = N/A
Certified = N/A
Wide Port Capable = N/A
Multipath = No

Port Information :
================

-----------------------------------------
Port Status Linkspeed SAS address
-----------------------------------------
   0 Active 12.0Gb/s  0x5002538b09134ab1
-----------------------------------------


Inquiry Data =
00 00 07 12 c5 00 10 03 4e 45 54 41 50 50 20 20
58 36 37 30 5f 53 31 36 34 33 31 35 54 41 54 45
4e 41 35 36 30 4d 31 30 35 32 37 35 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 a0 0c 60 05 c0
ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
56 46 54 35 59 46 41 51 32 35 30 37 30 31 5f 48
5f 30 8d 09 30 56 30 30 53 41 4d 53 55 4e 47 20

```

## powercycle
flashing the firmware should be an online operation (so without impact), i do recommend
powercycling either the disk or preferably the pc. this means shutting down your device and
powering it back up. a reboot alone might keep the disk powered on, which we don't want.


