---
date: '2025-09-03T21:45:43+02:00'
title: a collection of technical notes.
description: a collection of technical notes.
bookToC: false
params:
  eid: technotes
---
# a collection of technical notes.
most of them regarding spielerei with serial attached scsi
> [!WARNING]
> work in progress  
> typos and engrish ahead

## disclaimer
> [!IMPORTANT]
> to the best of my knowledge all information compiled here is correct at the time of writing.  
> even better, it was tested.

if something does not work as expected or you do not agree, you are free to [open an issue](https://github.com/inphobia/inphobia.github.io/issues).

my crystal ball is out for repair, so do provide the needed context.

## how to navigate
> [!NOTE]
> some pages are still being fleshed out and are empty or incomplete, as indicated by "todo".
- {{< elink "flow" "flowcharts" >}} are step by step guides on how i tackled what some would call projects
  - they'll make heavy use of links to topic specific pages
  - would be nice if hugo could render those inline to make a long & complete chart, [perhaps it can](https://gohugo.io/render-hooks/links/#pageinner-details)
- {{< elink "mr9361" "pages per topic" >}} are intended to cover very specific items only
  - actual pages are collapsed in menu to reduce clutter
  - can be used as reference when you know what you need
  - building block for flowcharts
  - category names chosen for fun, not clarity
- {{< elink "nomen" "nomenclature" >}}
  - prolly need to add a sas jargon dictionary...

## no idea where to start?
if you're new to sas:
- quickly check the {{< elink "nomen#basics" "basic sas terms" >}}
- continue on {{< elink "here" "here" >}} where we start building.

if you're already familiar:
- {{< elink "oops" "overlooked limitations" >}}
- these {{< elink "orhere" "random related items" >}} i found no place for
- {{< elink "arise" "compiling sg3 utils on windows" >}}
- the always popular {{< elink "redist" "reformatting sas disks" >}}
- or just {{< elink "flow" "start from the top" >}}.

## todo: this all started with me wanting to rip a few cds
and somehow i ended up with 50 sas ssd's, over 20 optical drives, notes and
half finished documentation all over the place, plus some interesting failures.

the focus will lay on using sas hardware when running only windows 11. the concepts
and tools are os agnostic and will work on other operating systems with some common
sense. i have no plans to cover pcie over sas, i do have 1 pcie u.2, so might get there
eventually. there's a small chance that a page or 2 on [openbsd](https://openbsd.org) appears,
don't count on it.

## global todo list
stuff that should show up here / my todo list

- easy to find, mostly correct
  - basic sas hba: airflow, bandwidth, external connections
  - using dbpoweramp: testing actually bit rotted discs, secure ripping pitfalls
  - full tower cases as drive storage
- easy to find, mostly outdated (so these are updates or rewrites)
  - ~~which sas hba you need~~
  - sas cabling needs, quality of cabling, sata devices choking on some sas cables
    - and what's the deal with the special supermicro cables broadcom sells
  - 8644 with and without pcie contacts
  - ~~which tool does what & how: sg3_utils, smartmond, storcli~~
  - why sas instead of sata
- hard to find, mostly correct
  - crapness of sff-8482 molex power plugs
  - drive power draw, 12v rails, sata 3.3v pin reassign
  - ~~going from 8644 to hba to 8644-8643 adapter (xi / xixe / xe)~~
  - ~~totally safe way to to combine a paperclip and psu~~
    - document alternatives
  - t10 dif stuff (mostly for seagate drives)
  - ~~4160 blocksize mention~~
- hard to find, incorrect, ancient. the things that took effort and time.
  - optical drives borked power connectors
  - ~~sector size for sas disks (512/520/4096) - and how to change them~~
  - monitoring sas drives
  - ~~flashing sas drives with more recent firmware~~
    - now with alternative tools
  - how not to flash optical drives
- sas expander stuff:
  - ~~daisy chaining~~
  - ~~firmware flashing~~
    - now with alternative tools
  - mixed drive use
  - sas expander and tower case as disk enclosure
  - 520byte drives and how they make windows storage commands hang
  - hot plugging sata drives on sas controllers and the tiny risk on over voltage
  - almost all 82885t are lenovo?
  - get i2c working
- and some words about
  - sata support in netapp shelves (or any shelf for that matter)
    - it seems iom12 based devices only accept sas disks
    - iom6 based devices can run sata devices but still need an interposer
    - ~~ds224c: 2 ioms and disk led will not light up, 1 iom disk led will light up~~
    - ~~neither option finds the disk~~
    - ~~perhaps multipath issue, sata has no multipath and seems always active on shelf~~
  - ses communication
  - out of band connector cable
  - stp (sata tunneling protocol)
