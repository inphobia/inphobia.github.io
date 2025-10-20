---
date: 2025-10-20T03:05:27+02:00
title: revive
description: revive
params:
  eid: revive
---
# TODO

going from lenovo fw 0.62 to 0.63

## find expander
```
>storcli64.exe /c0/eall show
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Properties :
==========

---------------------------------------------------------------------
EID State Slots PD PS Fans TSs Alms SIM ProdID        VendorSpecific
---------------------------------------------------------------------
  0 OK        8  1  0    0   0    0   0 VirtualSES
  2 Fault    25 11  2    4  11    0   2 DS22412IOM12A x48-0.10.10.0
 14 OK       24  4  2    4   2    1   1 AEC-82885T    PMCSIERA D
---------------------------------------------------------------------

EID-Enclosure Device ID |PD-Physical drive count |PS-Power Supply count
TSs-Temperature sensor count |Alms-Alarm count |SIM-SIM Count| ProdID=Product ID
```
eid 14 in this case

## check current config
```
>storcli64.exe /c0/e14 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Enclosure /c0/e14  :
==================

Information :
===========
Device ID = 14
Position = 0
Enclosure Type = SES
Status = OK
FRU Part Number = N/A
Enclosure Serial Number =    50000d1704770b3e
ESM Serial Number = N/A
Enclosure Zoning Mode = N/A
Partner Device ID = Unavailable
Device Type = Enclosure
EnclLogicalID = 0x50000D1704770B00


Inquiry Data :
============
Vendor Identification = ADAPTEC
Product Identification = AEC-82885T
Product Revision Level = B062


EnclSasAddress :
==============

-------------------------
Index SAS address
-------------------------
    0 0x50000D1704770B3E
-------------------------


Properties :
==========

------------------------------------------------------------------
EID State Slots PD PS Fans TSs Alms SIM ProdID     VendorSpecific
------------------------------------------------------------------
 14 OK       24  4  2    4   2    1   1 AEC-82885T PMCSIERA D
------------------------------------------------------------------


EID-Enclosure Device ID |PD-Physical drive count |PS-Power Supply count
TSs-Temperature sensor count |Alms-Alarm count |SIM-SIM Count| ProdID=Product ID
```

## update firmware
```
> storcli64 /c0/e14 download src=aec82885t.bin
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = Expander FW update is in progress. It takes several minutes to complete
```

## wait 5 minutes

## powercycle expander

## check
```
>storcli64.exe /c0/e2 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Enclosure /c0/e2  :
=================

Information :
===========
Device ID = 2
Position = 0
Enclosure Type = SES
Status = OK
FRU Part Number = N/A
Enclosure Serial Number =    50000d1704770b3e
ESM Serial Number = N/A
Enclosure Zoning Mode = N/A
Partner Device ID = Unavailable
Device Type = Enclosure
EnclLogicalID = 0x50000D1704770B00


Inquiry Data :
============
Vendor Identification = ADAPTEC
Product Identification = AEC-82885T
Product Revision Level = B063


EnclSasAddress :
==============

-------------------------
Index SAS address
-------------------------
    0 0x50000D1704770B3E
-------------------------


Properties :
==========

------------------------------------------------------------------
EID State Slots PD PS Fans TSs Alms SIM ProdID     VendorSpecific
------------------------------------------------------------------
  2 OK       24  4  2    4   2    1   1 AEC-82885T PMCSIERA D
------------------------------------------------------------------


EID-Enclosure Device ID |PD-Physical drive count |PS-Power Supply count
TSs-Temperature sensor count |Alms-Alarm count |SIM-SIM Count| ProdID=Product ID
```
