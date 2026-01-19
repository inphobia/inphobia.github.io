---
draft: true
date: 2026-01-02T03:26:37+01:00
title: detecting errors
description: detecting errors
params:
  eid: bzzzt
---
# TODO

## example 1
for
```
SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       40%        68         5859479392

  1 Raw_Read_Error_Rate     POSR-K   187   187   051    -    4752
```

output
```
smartctl -x /dev/sdd
smartctl 7.5 2025-04-30 r5714 [x86_64-w64-mingw32-w11-b26200] (AppVeyor)
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Green
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T1863442
LU WWN Device Id: 5 0014ee 058d69272
Firmware Version: 80.00A80
User Capacity:    3.000.592.982.016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Dec 31 22:44:05 2025 RST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM feature is:   Unavailable
Rd look-ahead is: Enabled
Write cache is:   Enabled
DSN feature is:   Unavailable
ATA Security is:  Disabled, NOT FROZEN [SEC1]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (40380) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 405) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70b5) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR-K   187   187   051    -    4752
  3 Spin_Up_Time            POS--K   192   176   021    -    5358
  4 Start_Stop_Count        -O--CK   100   100   000    -    25
  5 Reallocated_Sector_Ct   PO--CK   200   200   140    -    0
  7 Seek_Error_Rate         -OSR-K   200   200   000    -    1
  9 Power_On_Hours          -O--CK   100   100   000    -    76
 10 Spin_Retry_Count        -O--CK   100   253   000    -    0
 11 Calibration_Retry_Count -O--CK   100   253   000    -    0
 12 Power_Cycle_Count       -O--CK   100   100   000    -    24
192 Power-Off_Retract_Count -O--CK   200   200   000    -    18
193 Load_Cycle_Count        -O--CK   200   200   000    -    197
194 Temperature_Celsius     -O---K   129   115   000    -    21
196 Reallocated_Event_Count -O--CK   200   200   000    -    0
197 Current_Pending_Sector  -O--CK   200   200   000    -    0
198 Offline_Uncorrectable   ----CK   100   253   000    -    0
199 UDMA_CRC_Error_Count    -O--CK   200   200   000    -    0
200 Multi_Zone_Error_Rate   ---R--   100   253   000    -    0
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O      5  Comprehensive SMART error log
0x03       GPL     R/O      6  Ext. Comprehensive SMART error log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  NCQ Command Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa0-0xa7  GPL,SL  VS      16  Device vendor specific log
0xa8-0xb7  GPL,SL  VS       1  Device vendor specific log
0xbd       GPL,SL  VS       1  Device vendor specific log
0xc0       GPL,SL  VS       1  Device vendor specific log
0xc1       GPL     VS      93  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (6 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       40%        68         5859479392

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

SCT Status Version:                  3
SCT Version (vendor specific):       258 (0x0102)
Device State:                        Active (0)
Current Temperature:                    21 Celsius
Power Cycle Min/Max Temperature:     21/21 Celsius
Lifetime    Min/Max Temperature:     17/35 Celsius
Under/Over Temperature Limit Count:   0/0
Vendor specific:
03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/60 Celsius
Min/Max Temperature Limit:           -41/85 Celsius
Temperature History Size (Index):    478 (320)

Index    Estimated Time   Temperature Celsius
 321    2025-12-31 14:47    29  **********
 ...    ..(144 skipped).    ..  **********
 466    2025-12-31 17:12    29  **********
 467    2025-12-31 17:13    28  *********
 ...    ..( 75 skipped).    ..  *********
  65    2025-12-31 18:29    28  *********
  66    2025-12-31 18:30    29  **********
 ...    ..(  2 skipped).    ..  **********
  69    2025-12-31 18:33    29  **********
  70    2025-12-31 18:34    30  ***********
 ...    ..(  3 skipped).    ..  ***********
  74    2025-12-31 18:38    30  ***********
  75    2025-12-31 18:39    31  ************
 ...    ..( 31 skipped).    ..  ************
 107    2025-12-31 19:11    31  ************
 108    2025-12-31 19:12    32  *************
 ...    ..( 98 skipped).    ..  *************
 207    2025-12-31 20:51    32  *************
 208    2025-12-31 20:52    31  ************
 ...    ..( 38 skipped).    ..  ************
 247    2025-12-31 21:31    31  ************
 248    2025-12-31 21:32    30  ***********
 ...    ..( 13 skipped).    ..  ***********
 262    2025-12-31 21:46    30  ***********
 263    2025-12-31 21:47    31  ************
 ...    ..(  6 skipped).    ..  ************
 270    2025-12-31 21:54    31  ************
 271    2025-12-31 21:55    30  ***********
 ...    ..( 16 skipped).    ..  ***********
 288    2025-12-31 22:12    30  ***********
 289    2025-12-31 22:13    29  **********
 ...    ..(  8 skipped).    ..  **********
 298    2025-12-31 22:22    29  **********
 299    2025-12-31 22:23     ?  -
 300    2025-12-31 22:24    29  **********
 ...    ..(  5 skipped).    ..  **********
 306    2025-12-31 22:30    29  **********
 307    2025-12-31 22:31     ?  -
 308    2025-12-31 22:32    18  -
 ...    ..(  2 skipped).    ..  -
 311    2025-12-31 22:35    18  -
 312    2025-12-31 22:36    19  -
 313    2025-12-31 22:37    19  -
 314    2025-12-31 22:38     ?  -
 315    2025-12-31 22:39    21  **
 316    2025-12-31 22:40     ?  -
 317    2025-12-31 22:41    21  **
 318    2025-12-31 22:42     ?  -
 319    2025-12-31 22:43    21  **
 320    2025-12-31 22:44    21  **

SCT Error Recovery Control command not supported

Device Statistics (GP/SMART Log 0x04) not supported

Pending Defects log (GP Log 0x0c) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0002  2            0  R_ERR response for data FIS
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  2            4  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            5  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000f  2            0  R_ERR response for host-to-device data FIS, CRC
0x0012  2            0  R_ERR response for host-to-device non-data FIS, CRC
0x8000  4          139  Vendor specific
```

## example 2
for
```
   1 13482:45  0000000021e2866c  [1,16,0]   Recovered via rewrite in-place
   2 17394:52  00000000116f3c91  [1,17,1]   Reassigned by app, has valid data
   3 17466:52  00000000116f3c91  [1,18,1]   Successfully reassigned
```

output

```
smartctl -x /dev/sdg
smartctl 7.5 2025-04-30 r5714 [x86_64-w64-mingw32-w11-b26200] (AppVeyor)
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               SEAGATE
Product:              ST1000NM0045
Revision:             DS03
Compliance:           SPC-4
User Capacity:        1.000.204.886.016 bytes [1.00 TB]
Logical block size:   512 bytes
Formatted with type 2 protection
8 bytes of protection information per logical block
LU is fully provisioned
Rotation Rate:        7200 rpm
Form Factor:          3.5 inches
Logical Unit id:      0x5000c50085dee1f7
Serial number:        ZBS02JV9
Device type:          disk
Transport protocol:   SAS (SPL-4)
Local Time is:        Thu Jan 01 08:23:32 2026 RST
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Disabled or Not Supported
Read Cache is:        Enabled
Writeback Cache is:   Enabled

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Grown defects during certification <not available>
Total blocks reassigned during format <not available>
Total new blocks reassigned = 28
Power on minutes since format <not available>
Current Drive Temperature:     40 C
Drive Trip Temperature:        60 C

Manufactured in week 34 of year 2016
Specified cycle count over device lifetime:  10000
Accumulated start-stop cycles:  174
Specified load-unload count over device lifetime:  300000
Accumulated load-unload cycles:  2695
Elements in grown defect list: 28

Vendor (Seagate Cache) information
  Blocks sent to initiator = 429181014
  Blocks received from initiator = 4248418923
  Blocks read from cache and sent to initiator = 242933321
  Number of read and write commands whose size <= segment size = 682992790
  Number of read and write commands whose size > segment size = 591

Vendor (Seagate/Hitachi) factory information
  number of hours powered up = 60752.60
  number of minutes until next internal SMART test = 58

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:   2328747118        7         0  2328747125          7      10055.645           0
write:         0        0         0         0          0     125117.605           0
verify: 4071508430      138         0  4071508568        138     369842.638           0

Non-medium error count:      117

SMART Self-test log
Num  Test              Status                 segment  LifeTime  LBA_first_err [SK ASC ASQ]
     Description                              number   (hours)
# 1  Background short  Completed                  96       2                 - [-   -    -]
# 2  Reserved(7)       Completed                  64       2                 - [-   -    -]

Long (extended) Self-test duration: 10800 seconds [180.0 minutes]

Background scan results log
  Status: scan is active
    Accumulated power on time, hours:minutes 60752:36 [3645156 minutes]
    Number of background scans performed: 855,  scan progress: 52.92%
    Number of background medium scans performed: 855

   #  when        lba(hex)    [sk,asc,ascq]    reassign_status
   1 13482:45  0000000021e2866c  [1,16,0]   Recovered via rewrite in-place
   2 17394:52  00000000116f3c91  [1,17,1]   Reassigned by app, has valid data
   3 17466:52  00000000116f3c91  [1,18,1]   Successfully reassigned
   4 28688:24  00000000116f4a42  [1,17,1]   Successfully reassigned
   5 28688:24  00000000116f57f3  [1,18,1]   Successfully reassigned
   6 28688:24  00000000116f65a4  [1,18,1]   Successfully reassigned
   7 52013:22  00000000116f137f  [1,17,1]   Successfully reassigned
   8 52013:22  0000000011b74d24  [1,18,8]   Successfully reassigned
   9 52013:22  0000000011b7924c  [1,17,1]   Successfully reassigned
  10 52590:54  000000006ae5cb6d  [1,18,1]   Successfully reassigned
  11 52928:08  0000000011b76885  [1,18,1]   Successfully reassigned
  12 53000:04  000000000dd8e7d1  [1,18,1]   Successfully reassigned
  13 53144:08  0000000011b7bb5e  [1,18,4]   Successfully reassigned
  14 53289:25  00000000604e4edd  [1,18,1]   Successfully reassigned
  15 60751:51  000000000dd8cbfd  [1,18,1]   Successfully reassigned
  16 60751:51  000000000dd8d9e7  [1,17,1]   Recovered via rewrite in-place
  17 60751:54  00000000116f7355  [1,18,1]   Successfully reassigned
  18 60751:54  00000000116f8eb6  [1,18,1]   Successfully reassigned
  19 60751:54  00000000116f9c67  [1,18,1]   Successfully reassigned
 49152 52013:22  0001000011b74d24  [1,18,8]   Successfully reassigned
Device does not support General statistics and performance logging

Protocol Specific port log page for SAS SSP
relative target port id = 1
  generation code = 0
  number of phys = 1
  phy identifier = 0
    attached device type: expander device
    attached reason: hard reset
    reason: hard reset
    negotiated logical link rate: phy enabled; 12 Gbps
    attached initiator port: ssp=0 stp=0 smp=1
    attached target port: ssp=0 stp=0 smp=1
    SAS address = 0x5000c50085dee1f5
    attached SAS address = 0x50000d1700b1bcbf
    attached phy identifier = 11
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 1
    Phy reset problem count = 0
relative target port id = 2
  generation code = 0
  number of phys = 1
  phy identifier = 1
    attached device type: no device attached
    attached reason: unknown
    reason: unknown
    negotiated logical link rate: phy enabled; unknown
    attached initiator port: ssp=0 stp=0 smp=0
    attached target port: ssp=0 stp=0 smp=0
    SAS address = 0x5000c50085dee1f6
    attached SAS address = 0x0
    attached phy identifier = 0
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 0
    Phy reset problem count = 0
```


## example 3
for
```
   #  when        lba(hex)    [sk,asc,ascq]    reassign_status
   1 21639:39  000000000137d432  [1,18,1]   Recovered via rewrite in-place
   2 22056:43  000000000137c5e5  [1,18,1]   Recovered via rewrite in-place
   3 22066:53  000000000143d935  [1,18,4]   Recovered via rewrite in-place
Device does not support General statistics and performance logging

```

output

```
smartctl -x /dev/sdi
smartctl 7.5 2025-04-30 r5714 [x86_64-w64-mingw32-w11-b26200] (AppVeyor)
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               SEAGATE
Product:              ST1000NM0045
Revision:             DS03
Compliance:           SPC-4
User Capacity:        1.000.204.886.016 bytes [1.00 TB]
Logical block size:   512 bytes
LU is fully provisioned
Rotation Rate:        7200 rpm
Form Factor:          3.5 inches
Logical Unit id:      0x5000c50085d1ad17
Serial number:        ZBS022ME
Device type:          disk
Transport protocol:   SAS (SPL-4)
Local Time is:        Thu Jan 01 12:22:28 2026 RST
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Disabled or Not Supported
Read Cache is:        Enabled
Writeback Cache is:   Enabled

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Grown defects during certification = 0
Total blocks reassigned during format = 0
Total new blocks reassigned = 0
Power on minutes since format = 229
Current Drive Temperature:     40 C
Drive Trip Temperature:        60 C

Manufactured in week 34 of year 2016
Specified cycle count over device lifetime:  10000
Accumulated start-stop cycles:  176
Specified load-unload count over device lifetime:  300000
Accumulated load-unload cycles:  2696
Elements in grown defect list: 0

Vendor (Seagate Cache) information
  Blocks sent to initiator = 3799915956
  Blocks received from initiator = 3023110301
  Blocks read from cache and sent to initiator = 229967894
  Number of read and write commands whose size <= segment size = 648456224
  Number of read and write commands whose size > segment size = 14595

Vendor (Seagate/Hitachi) factory information
  number of hours powered up = 60758.00
  number of minutes until next internal SMART test = 15

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:   1586540899        1         0  1586540900          1      10740.543           0
write:         0        0         0         0          0     115539.480           0
verify: 2172820407        9         0  2172820416          9     368677.100           0

Non-medium error count:      485

SMART Self-test log
Num  Test              Status                 segment  LifeTime  LBA_first_err [SK ASC ASQ]
     Description                              number   (hours)
# 1  Background short  Completed                  96       2                 - [-   -    -]
# 2  Reserved(7)       Completed                  64       2                 - [-   -    -]

Long (extended) Self-test duration: 10800 seconds [180.0 minutes]

Background scan results log
  Status: scan is active
    Accumulated power on time, hours:minutes 60758:00 [3645480 minutes]
    Number of background scans performed: 855,  scan progress: 50.13%
    Number of background medium scans performed: 855

   #  when        lba(hex)    [sk,asc,ascq]    reassign_status
   1 21639:39  000000000137d432  [1,18,1]   Recovered via rewrite in-place
   2 22056:43  000000000137c5e5  [1,18,1]   Recovered via rewrite in-place
   3 22066:53  000000000143d935  [1,18,4]   Recovered via rewrite in-place
Device does not support General statistics and performance logging

Protocol Specific port log page for SAS SSP
relative target port id = 1
  generation code = 0
  number of phys = 1
  phy identifier = 0
    attached device type: expander device
    attached reason: power on
    reason: power on
    negotiated logical link rate: phy enabled; 12 Gbps
    attached initiator port: ssp=0 stp=0 smp=1
    attached target port: ssp=0 stp=0 smp=1
    SAS address = 0x5000c50085d1ad15
    attached SAS address = 0x50000d1700b1bcbf
    attached phy identifier = 9
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 0
    Phy reset problem count = 0
relative target port id = 2
  generation code = 0
  number of phys = 1
  phy identifier = 1
    attached device type: no device attached
    attached reason: unknown
    reason: unknown
    negotiated logical link rate: phy enabled; unknown
    attached initiator port: ssp=0 stp=0 smp=0
    attached target port: ssp=0 stp=0 smp=0
    SAS address = 0x5000c50085d1ad16
    attached SAS address = 0x0
    attached phy identifier = 0
    Invalid DWORD count = 0
    Running disparity error count = 0
    Loss of DWORD synchronization count = 0
    Phy reset problem count = 0
```
