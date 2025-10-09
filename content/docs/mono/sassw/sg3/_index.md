---
title: sg3 utils
description: sg3 utils
bookCollapseSection: true
params:
  eid: sg3utils
---
# sg3 utils
> [!TIP]
> sg3 utils supports sas, nvme and sata devices systemwide

## where
- https://sg.danny.cz/sg/sg3_utils.html
  - windows download links at the bottom
- {{< elink "arise" "alternative" >}}

## how
the zipfile can be extracted wherever you want, the executables are
a few directories deep

## all examples are for windows
all examples are given for the windows version of sg3_utils. they can likely be used on other operating systems
if you compensate for the fact that the drive and controller references differ.

all invocations of sg3 binaries have the .exe extension in these documents to clearly show the windows version
is being used.


# todo words

- PD- notation to indicate physical drives
- drive letters are show if the disk has one assigned
- it tends to lump all optical drive letters on the first drive found
```
CDROM0  [DFG]   <Sas  >  PLEXTOR   DVDR   PX-760A    1.07
CDROM1          <Sas  >  HL-DT-ST  DVDRAM GH24NSD1   LW00
CDROM2          <Sas  >  ASUS      DRW-24D5MT        1.00
```
- expanders can only be addressed via their scsi bus id


## why
contains most of the commands you'll need
