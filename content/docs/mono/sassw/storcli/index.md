---
title: storcli
params:
  eid: storcli
---

# what

storcli: the tool to interact with your broadcom cards.

## why
needed for most interaction like:
* updating fw
* checking controller
* checking disks


## where
can be downloaded from https://www.broadcom.com/
make sure your version somewhat matches your firmware. i'm using "storcli sas3.5 p36" with a 9500-16e running uefi p36.

## naming
while broadcom all refers to this program as "storcli", it can also be known as storcli64 as you can see in these examples.

## examples
### show your controller

```
>storcli64.exe show
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Status Code = 0
Status = Success
Description = None

Number of Controllers = 1
Host Name = BOX
Operating System  = Windows 11
StoreLib IT Version = 07.3503.0200.0000
StoreLib IR3 Version = 16.16-0

IT System Overview :
==================

---------------------------------------------------------------------------
Ctl Model        AdapterType   VendId DevId SubVendId SubDevId PCI Address
---------------------------------------------------------------------------
  0 HBA 9500-16e   SAS3816(A0) 0x1000  0xE6    0x1000   0x4070 00:01:00:00
---------------------------------------------------------------------------
```

### show it's temperature
```
>storcli64.exe /c0 show temperature
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Controller Properties :
=====================

--------------------------------------
Ctrl_Prop                       Value
--------------------------------------
ROC temperature(Degree Celsius) 50
--------------------------------------
```
### show only help commands related to hba mode
```
>storcli64.exe -help it

      StorCli SAS Customization Utility Ver 007.3503.0000.0000 Aug 05, 2025

    (c)Copyright 2025, Broadcom Inc. All Rights Reserved.


storcli -v
storcli [verbose] -h| -help| ?
storcli show
storcli show all
storcli show ctrlcount
storcli show file=<filepath>
storcli get otc [folder=<name>]
storcli /cx/ex show
storcli /cx/ex show all
storcli /cx/ex set time=systemtime
storcli /cx delete events
storcli /cx show events [logfile[=filename]] ]
storcli /cx show eventcounters [type=sas|pcie]
storcli /cx delete eventcounters [type=sas|pcie]
storcli /cx[/ex]/sx show
storcli /cx[/ex]/sx show all
storcli /cx[/ex]/sx start locate
storcli /cx[/ex]/sx stop locate
storcli /cx show
storcli /cx show all [noASO] [noforeign] [logfile[=filename]]
storcli /cx[/ex]/sx download src=<filepath> [satabridge] [mode= 5|7] [parallel [force]] [chunksize=<val>]
storcli /cx/ex download src=<filepath> [ mode=5 | [forceActivate] mode=7] [bufferid=<val>] [chunksize=<val>]
storcli /cx/ex download src=<filepath> mode=e [offline] [forceActivate [delay=<val>]] [bufferid=<val>] [chunksize=<val>]
storcli /cx/ex download mode=f [offline] [delay=<val>] [bufferid=<val>]
storcli /cx[/ex]/sx download src=<filepath> mode= E [offline] [activatenow [delay=<val>] ] [chunksize=<val>]
storcli /cx[/ex]/sx download  mode= F [offline] [delay=<val>]
storcli /cx[/ex]/sx set bootdrive=<on|off>
storcli /cx download file=<filepath> [noverchk] [noreset] [forcehcb] [force]
storcli /cx set sbr
storcli /cx/px show
storcli /cx/px show phyerrorcounters
storcli /cx/px show phyevents
storcli /cx/lnx show
storcli /cx/px set state=on|off
storcli /cx/px reset [hard | errorlog]
storcli /cx restart
storcli /cx set assemblynumber= xxxx
storcli /cx show assemblynumber
storcli /cx set tracernumber= xxxx
storcli /cx show tracernumber
storcli /cx show boardname
storcli /cx set sasadd = xxxx [devicename] [methodport]
storcli /cx set sasaddhi = xxxx  sasaddlow = xxxxx [devicename] [methodport]
storcli /cx show sasadd
storcli /cx/px compare linkspeed=<speed>
storcli /cx set updatevpd file=<filepath>
storcli /cx show vpd
storcli /cx erase nvsram
storcli /cx erase fwbackup
storcli /cx erase bootservices
storcli /cx erase all [excludemfg] [file=filename]
storcli /cx erase perconfpage
storcli /cx erase mpb
storcli /cx download efibios file=<filepath>
storcli /cx download cpld file=<filepath>
storcli /cx download psoc file=<filepath>
storcli /cx download bios file=<filepath>
storcli /cx download fcode file=<filepath>
storcli /cx compare bios ver =<bios version>
storcli /cx compare fwprodid ver =<fw product id version>
storcli /cx compare ssid ver =<ssid version>
storcli /cx compare firmware ver =<firmware version>
storcli /cx get bios file=<filename>
storcli /cx get firmware  file=<filename>
storcli /cx get mpb  file=<filename>
storcli /cx get fwbackup  file=<filename>
storcli /cx get nvdata file=<filename>
storcli /cx get flash  file=<filename>
storcli /cx set oob mode=i2c|pcie maxpayloadsize=<payloadsize> maxpacketsize=<packetsize> [spdm=on|off] [pldm=on|off]
storcli /cx show oob
storcli /cx show htbparams
storcli /cx set htbparams=off
storcli /cx set htbparams [= on] maxsize=<value> minsize=<value> decrementsize=<value>
storcli /cx show security spdm slotgroup=xx slot=yy
storcli /cx export security spdm slotgroup=xx slot=yy subject=subjectfile file=filename
storcli /cx import security spdm slotgroup=xx slot=yy file=filename [seal]
storcli /cx set security spdm slotgroup=xx slot=yy invalidate [force]
storcli /cx get security spdm slotgroup=xx slot=yy file=filename
storcli /cx show temperature
storcli /cx show refClk
storcli /cx set refClk = 0|1|2
storcli /cx show perst
storcli /cx set perst = 0|1|2
storcli /cx db register type=trace|snapshot [size=<val>] [prodmask=<val>] [iopmask=<val>:<val>] [plmask=<val>:<val>] [irmask=<val>:<val>]
storcli /cx db query type=trace|snapshot
storcli /cx db read type=trace|snapshot file=<filepath>
storcli /cx db release type=trace|snapshot
storcli /cx db unregister type=trace|snapshot
storcli /cx db get type= {[master],[event],[ mpi],[ scsi]} | all
storcli /cx db delete type= {[master],[event],[ mpi],[ scsi]} | all
storcli /cx db set {[master=<val>] [event EventLogQualifier=<val> EventValue=<val> ]
           [mpi loginfo=<val> iocstatus=<val>] [ scsi sensekey=<val> asc=<val> ascq=<val>]}

```
### show most info from all enclosures and disks on controller 0
```
>storcli64.exe /c0/eall/sall show all
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
### show phy error information
```
>storcli64.exe /c0/pall show phyerrorcounters
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = Show Phy Error Counters


Phy Info :
========

-----------------------------------------------------------------------
PhyNo InvldDwrdCount RungDispartyErrCnt LosOfDwrdSynCnt PhyResetPrbCnt
-----------------------------------------------------------------------
    0              0                  0               0              0
    1              0                  0               0              0
    2              0                  0               0              0
    3              0                  0               0              0
    4              0                  0               0              0
    5              0                  0               0              0
    6              0                  0               0              0
    7              0                  0               0              0
    8              0                  0               0              0
    9              0                  0               0              0
   10              0                  0               0              0
   11              0                  0               0              0
   12              0                  0               0              0
   13              0                  0               0              0
   14              0                  0               0              0
   15              0                  0               0              0
-----------------------------------------------------------------------

PhyNo-Phy Number |InvalDwdCnt-Invalid Dword count | RungDispartyErrCnt-Running Disparity error count
LosOfDwrdSynCnt-Loss of Dword synchronization count | PhyResetPrbCnt-Phy reset problem count
```
### all phy info
```
>storcli64.exe /c0/pall show
CLI Version = 007.3503.0000.0000 Aug 05, 2025
Operating system = Windows 11
Controller = 0
Status = Success
Description = None


Test Link State :
===============

------------------------------------------------------------------------------------------------------------------------------------------------------
PhyNo SASLinkSpeed HBASASADDR       Enbl APhy AhDH AhDevAddr        Port Vendor SMPT SMPI STPT STPI SSPT SSPI SEPDI ATAPT DIRAD SATAH SATAE DTYPE ABS
------------------------------------------------------------------------------------------------------------------------------------------------------
    0 Unknown      500062B2205FEA80 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    1 Unknown      500062B2205FEA81 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    2 Unknown      500062B2205FEA82 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    3 Unknown      500062B2205FEA83 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    4 Unknown      500062B2205FEA84 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    5 Unknown      500062B2205FEA85 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    6 Unknown      500062B2205FEA86 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    7 Unknown      500062B2205FEA87 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    8 Unknown      500062B2205FEA88 Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
    9 12.0 Gbps    500062B2205FEA89 Y    0    0017 5002538B09134AB1 8    -      0    0    0    0    1    0    0     0     1     0     0     1     N
   10 Unknown      500062B2205FEA8A Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
   11 Unknown      500062B2205FEA8B Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
   12 Unknown      500062B2205FEA8C Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
   13 Unknown      500062B2205FEA8D Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
   14 Unknown      500062B2205FEA8E Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
   15 Unknown      500062B2205FEA8F Y    -    -    -                -    -      -    -    -    -    -    -    -     -     -     -     -     -     -
------------------------------------------------------------------------------------------------------------------------------------------------------

PhyNo-Phy Number|HBASASADDR-HBA SAS ADDRESS|Enbl-Enable|APhy-Attached Phy Identifier
AhDH-Attached Device Handle|AhDevAddr-Attached Enclosure Device Address
SMPT-SMP Target|SMPI-SMP Initiator|STPT-STP Target|STPI-STP Initiator|SSPT-SSP Target
SSPI-SSP Initiator|SEPDI-SEP Device|ATAPT-ATAP Target|DIRAD-Device Info Direct Attached
DTYPE-Device Type|ABS-Access Status Device Blocked|SATAH-SATA Host|SATAE-SATA Device
```
