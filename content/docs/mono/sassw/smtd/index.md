---
title: smartmontools
description: smartmontools
params:
  eid: smartmon
---
# smartmontools

# todo still mostly collection of logs/notes

## why

## where
- https://github.com/smartmontools/smartmontools/releases
- https://www.smartmontools.org/

## what

### todo noteworthy information

- Logical block size:   4096 bytes
- dual port attached
  - relative target port id = 1
  - relative target port id = 2


## how

### finding attached drives

smartmontools isn't bothered by sector size nor the lack if a driveletter,
and unlike sg_scan.exe or storcli is seldom hangs.

```
smartctl.exe --scan
/dev/sda -d scsi # /dev/sda, SCSI device
/dev/sdb -d nvme # /dev/sdb, NVMe device
/dev/sdc -d nvme # /dev/sdc, NVMe device
/dev/sdd -d scsi # /dev/sdd, SCSI device
/dev/sde -d scsi # /dev/sde, SCSI device
/dev/sdf -d scsi # /dev/sdf, SCSI device
/dev/sdg -d scsi # /dev/sdg, SCSI device
```

### show all statistics smartmon understands

```
smartctl.exe -x /dev/sdd
smartctl 7.5 2025-04-30 r5714 [x86_64-w64-mingw32-w11-b26200] (AppVeyor)
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               NETAPP
Product:              X371_S164A960ATE
Revision:             NA54
Compliance:           SPC-5
User Capacity:        960.197.124.096 bytes [960 GB]
Logical block size:   4096 bytes
LU is resource provisioned, LBPRZ=1
Rotation Rate:        Solid State Device
Form Factor:          2.5 inches
Logical Unit id:      0x5002538b0156bb30
Serial number:        S5JENE0R504188
Device type:          disk
Transport protocol:   SAS (SPL-4)
Local Time is:        Wed Oct 08 23:05:54 2025 RDT
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Enabled
Read Cache is:        Enabled
Writeback Cache is:   Disabled

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Percentage used endurance indicator: 1%
Current temperature = 30
Lifetime maximum temperature = 37
Lifetime minimum temperature = 14
Maximum temperature since power on = 31
Minimum temperature since power on = 30
Manufactured in week 21 of year 2021
Accumulated start-stop cycles:  12
Specified load-unload count over device lifetime:  0
Accumulated load-unload cycles:  0
Elements in grown defect list: 0

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:          0        0         0         0          0     110374,315           0
write:         0        0         0         0          0     110385,698           0
verify:        0        0         0         0          0      75570,557           0

Non-medium error count:     7748

  Pending defect count:0 Pending Defects
No Self-tests have been logged

Background scan results log
  Status: scan is active
    Accumulated power on time, hours:minutes 33651:44 [2019104 minutes]
    Number of background scans performed: 51,  scan progress: 0,01%
    Number of background medium scans performed: 51
Device does not support General statistics and performance logging

Protocol Specific port log page for SAS SSP
relative target port id = 1
  generation code = 4
  number of phys = 1
  phy identifier = 0
    attached device type: expander device
    attached reason: SMP phy control function
    reason: loss of dword synchronization
    negotiated logical link rate: phy enabled; 12 Gbps
    attached initiator port: ssp=0 stp=0 smp=1
    attached target port: ssp=0 stp=0 smp=1
    SAS address = 0x5002538b0156bb31
    attached SAS address = 0x500a098007ea96cd
    attached phy identifier = 20
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 0
    Phy reset problem count = 0
    Phy event descriptors:
     Received ERROR count: 0
     Received address frame error count: 0
     Received abandon-class OPEN_REJECT count: 0
     Received retry-class OPEN_REJECT count: 0
     Received SSP frame error count: 0
relative target port id = 2
  generation code = 4
  number of phys = 1
  phy identifier = 1
    attached device type: expander device
    attached reason: hard reset
    reason: loss of dword synchronization
    negotiated logical link rate: phy enabled; 12 Gbps
    attached initiator port: ssp=0 stp=0 smp=1
    attached target port: ssp=0 stp=0 smp=1
    SAS address = 0x5002538b0156bb32
    attached SAS address = 0x500a098007ea8759
    attached phy identifier = 20
    Invalid DWORD count = 8
    Running disparity error count = 8
    Loss of DWORD synchronization count = 2
    Phy reset problem count = 0
    Phy event descriptors:
     Received ERROR count: 0
     Received address frame error count: 0
     Received abandon-class OPEN_REJECT count: 0
     Received retry-class OPEN_REJECT count: 0
     Received SSP frame error count: 0
```

### todo initiate background scan
