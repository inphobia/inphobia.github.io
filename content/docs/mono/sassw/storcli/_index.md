---
title: storcli
description: storcli
bookCollapseSection: true
params:
  eid: storcli
---
# storcli
> [!TIP]
> storcli will only interact with broadcom controllers and
> devices connected to those.

storcli is the tool to interact with your broadcom card.

## why
needed for most interaction like:
- updating fw
- checking controller
- checking disks



## where
can be downloaded from [https://www.broadcom.com/][].
make sure your version somewhat matches your firmware. i'm using "storcli sas3.5 p36" with a 9500-16e running uefi p36.

[https://www.broadcom.com/]: https://www.broadcom.com/

## how
unzip the file, the binaries are a few levels deep in the windows directory.

## naming
while broadcom refers to this program as "storcli", the actual binary can also be called storcli64 or storcli2, as you can see in several examples.

## bugs

### hangs and aborts to quick

whenever storci encounters a situation that differs from what it expects, even by a small amount, it tends
to stop printing output.
this makes troubleshooting quite frustrating now and then

example 1: sas expander has issues connecting

{{% details title="expected output: working expander and drive still shown" open=false %}}
```
>storcli64 /c0 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Basics :
======
Controller = 0
Adapter Type =   SAS3816(A0)
Model = HBA 9500-16e
Serial Number = SPE4909773
Current System Date/time = 10/09/2025 01:25:00
Concurrent commands supported = 6656
SAS Address =  500062b2205fea80
PCI Address = 00:01:00:00


Version :
=======
Firmware Package Build = 36.00.00.00
Firmware Version = 36.00.00.00
Bios Version = 09.71.00.00_36.00.00.00
NVDATA Version = 36.00.00.14
PSOC FW Version = 0x006E
PSOC Part Number = 14790
Driver Name = ItSas35
Driver Version = 2.61.82.00


PCI Version :
===========
Vendor Id = 0x1000
Device Id = 0xE6
SubVendor Id = 0x1000
SubDevice Id = 0x4070
Host Interface = PCIE
Device Interface = SAS-12G
Bus Number = 1
Device Number = 0
Function Number = 0
Domain ID = 0


Pending Images in Flash :
=======================
Image name = No pending images


Status :
======
Controller has booted into certificate provision mode = No
Package Stamp Mismatch = No


Supported Adapter Operations :
============================
Support more than 8 Phys = Yes
Support Enclosure Enumeration = Yes
Support Allowed Operations = Yes
Support Multipath = Yes
Support Security = Yes
support EKM = No
Support Secure Boot = Yes
Support Platform Security = No
Support Package Stamp Mismatch Reporting = Yes
Support PSOC Update = Yes
Support PSOC Part Information = Yes
Support PSOC Version Information = Yes


Supported PD Operations :
=======================
Support Physical Link Speed = Yes


HwCfg :
=====
ChipRevision =  A0
BatteryFRU = N/A
Front End Port Count = 1
Backend Port Count = 21
Serial Debugger = Absent
NVRAM Size = 0KB
Flash Size = 16MB
Temperature Sensor for ROC = Present
Temperature Sensor for Controller = Absent
ROC temperature(Degree Celsius) = 50


Boot :
====
Max Drives to Spinup at One Time = 2
Maximum number of direct attached drives to spin up in 1 min = 60
Delay Among Spinup Groups (sec) = 2


Capabilities :
============
Supported Drives = SAS, SATA
Enable JBOD = Yes
Max Parallel Commands = 6656
Max SGE Count = 128
Max Data Transfer Size = 32 sectors


Secure Boot :
===========
Secure Boot Enabled = Yes
Controller in Soft Secure Mode = No
Controller in Hard Secure Mode = Yes
Key Update Pending = No
Remaining Secure Boot Key Slots = 7


Security Protocol properties :
============================
Security Protocol = None


Enclosure Information :
=====================

------------------------------------------------------------------
EID State Slots PD PS Fans TSs Alms SIM ProdID     VendorSpecific
------------------------------------------------------------------
  0 OK       16  1  0    0   0    0   0 VirtualSES
------------------------------------------------------------------


Physical Device Information :
===========================

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
{{% /details %}}





{{% details title="actual output: does not show any driver or expanders anymore" open=false %}}
```
>storcli64.exe /c0 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Basics :
======
Controller = 0
Adapter Type =   SAS3816(A0)
Model = HBA 9500-16e
Serial Number = SPE4909773
Current System Date/time = 10/08/2025 22:02:34
Concurrent commands supported = 6656
SAS Address =  500062b2205fea80
PCI Address = 00:01:00:00


Version :
=======
Firmware Package Build = 36.00.00.00
Firmware Version = 36.00.00.00
Bios Version = 09.71.00.00_36.00.00.00
NVDATA Version = 36.00.00.14
PSOC FW Version = 0x006E
PSOC Part Number = 14790
Driver Name = ItSas35
Driver Version = 2.61.82.00


PCI Version :
===========
Vendor Id = 0x1000
Device Id = 0xE6
SubVendor Id = 0x1000
SubDevice Id = 0x4070
Host Interface = PCIE
Device Interface = SAS-12G
Bus Number = 1
Device Number = 0
Function Number = 0
Domain ID = 0


Pending Images in Flash :
=======================
Image name = No pending images


Status :
======
Controller has booted into certificate provision mode = No
Package Stamp Mismatch = No


Supported Adapter Operations :
============================
Support more than 8 Phys = Yes
Support Enclosure Enumeration = Yes
Support Allowed Operations = Yes
Support Multipath = Yes
Support Security = Yes
support EKM = No
Support Secure Boot = Yes
Support Platform Security = No
Support Package Stamp Mismatch Reporting = Yes
Support PSOC Update = Yes
Support PSOC Part Information = Yes
Support PSOC Version Information = Yes


Supported PD Operations :
=======================
Support Physical Link Speed = Yes


HwCfg :
=====
ChipRevision =  A0
BatteryFRU = N/A
Front End Port Count = 1
Backend Port Count = 21
Serial Debugger = Absent
NVRAM Size = 0KB
Flash Size = 16MB
Temperature Sensor for ROC = Present
Temperature Sensor for Controller = Absent
ROC temperature(Degree Celsius) = 52


Boot :
====
Max Drives to Spinup at One Time = 2
Maximum number of direct attached drives to spin up in 1 min = 60
Delay Among Spinup Groups (sec) = 2


Capabilities :
============
Supported Drives = SAS, SATA
Enable JBOD = Yes
Max Parallel Commands = 6656
Max SGE Count = 128
Max Data Transfer Size = 32 sectors


Secure Boot :
===========
Secure Boot Enabled = Yes
Controller in Soft Secure Mode = No
Controller in Hard Secure Mode = Yes
Key Update Pending = No
Remaining Secure Boot Key Slots = 7


Security Protocol properties :
============================
Security Protocol = None
```
{{% /details %}}

example 2: show information from the always present virtual expander with other expander acting up

{{% details title="expected output: expander details show" open=false %}}

```
>storcli64.exe /c0/e0 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Enclosure /c0/e0  :
=================

Information :
===========
Device ID = 0
Position = 0
Enclosure Type = SES
Status = OK
FRU Part Number = N/A
Enclosure Serial Number = 300062B22011EA80
ESM Serial Number = N/A
Enclosure Zoning Mode = N/A
Partner Device ID = Unavailable
Device Type = Backplane
EnclLogicalID = 0x300062B22011EA80


Inquiry Data :
============
Vendor Identification = BROADCOM
Product Identification = VirtualSES
Product Revision Level = 03


EnclSasAddress :
==============

-------------------------
Index SAS address
-------------------------
    0 0x300162B2205FEA80
-------------------------


Properties :
==========

------------------------------------------------------------------
EID State Slots PD PS Fans TSs Alms SIM ProdID     VendorSpecific
------------------------------------------------------------------
  0 OK       16  1  0    0   0    0   0 VirtualSES
------------------------------------------------------------------


EID-Enclosure Device ID |PD-Physical drive count |PS-Power Supply count
TSs-Temperature sensor count |Alms-Alarm count |SIM-SIM Count| ProdID=Product ID
```
{{% /details %}}

{{% details title="actual output: even targetted query fails" open=false %}}
```
>storcli64.exe /c0/e0 show all
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Failure
Description = Failed to get enclosure information
```
{{% /details %}}


### todo: basic commandline switches

## {{< elink "ezcp" "examples safe to copy paste" >}}
## {{< elink "blitz" "upgrading adapter firmware" >}}
