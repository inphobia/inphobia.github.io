---
date: '2025-09-03T21:45:43+02:00'
title: a collection of technical notes.
description: a collection of technical notes.
bookToC: false
---

# a collection of technical notes.

> [!WARNING]
> very much work in progress

## disclaimer
to the best of my knowledge all information compiled here is correct
at the time of writing. even better, it was tested. if something does not work as
expected or you do not agree, you are free to [open an issue](https://github.com/inphobia/inphobia.github.io/issues).

my crystal ball is out for repair, so do provide the needed context.

## for now

* create placeholders for all mono's
* best make archetype for that type first
* adding content as i go along

~~atm trying to find & test options to add content with the least amount of effort to add & maintain:~~
* ~~a basic formatter to offload html and image generation~~
* ~~a way to handle simple metadata like links & layout.~~

~~hugo & hugo-book in testing, most likely a keeper~~

expect typos and engrish.

~~next up:~~
* ~~mock up structure~~
  * ~~how about~~
    * ~~things i wanted to get done & how i did em~~
    * ~~reference lists (sas hw , usage , other hw, etc)~~
    * reworking lists seems pretty doable if need be
* ~~run some test with how images are handled~~

> [!IMPORTANT]
repeating ad infinitum: this is a log, not yet a guide. any breakage at this time/stage just gets you higher on the darwin awards list for computering.

{{% steps %}}
1. ## i just copied your example and now nothing works!
   > [!CAUTION]
   drop me a note and i'll send some more things you can blindly paste.

2. ## likely what you're here for
   this is an extract of cli log and show the least possible steps to reformat a sas drive.

   as in: this is a cli log, not a guide! it's up to you to be intimidated by the beauty of the commands and/or judge if you're feeling lucky.

   the guides are being worked on, but if you're impatient...

3. ## find drive
   use sg3_utils windows version:
   https://github.com/doug-gilbert/sg3_utils/releases


   ```
   >sg_scan.exe -b
   PD0     [S]     <Sas  >  NETAPP    X670_S164315TATE  NA55  S40TNY0M105275
   PD1     [E]     <NVMe >  WD_BLACK SN850X 8000GB  638201WD  E823_8FA6_BF53_0001_001B_448B_4071_28F4.
   PD2     [C]     <NVMe >  WD_BLACK SN850X 8000GB  638201WD  E823_8FA6_BF53_0001_001B_448B_4071_2C80.
   PD3             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R603645
   PD4             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R502225
   PD5             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R502235
   PD6             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R502224
   PD7             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R502223
   PD8             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R502221
   PD9             <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R502238
   PD10            <Sas  >  NETAPP    X371_S164A960ATE  NA54  S5JENE0R607104
   ```


4. ## option1: format 512
   ```
   >sg_format.exe  --format --size=512 PD6
   NETAPP    X371_S164A960ATE  NA54   peripheral_type: disk [0x0]
   Unit serial number: S5JENE0R502224
   LU name: 5002538b01564070
   Mode Sense (block descriptor) data, prior to changes:
   Number of blocks=1875385008 [0x6fc81ab0]
   Block size=520 [0x208]

   A FORMAT UNIT command will commence in 15 seconds
   ALL data on PD6 will be DESTROYED
   Press control-C to abort

   A FORMAT UNIT command will commence in 10 seconds
   ALL data on PD6 will be DESTROYED
   Press control-C to abort

   A FORMAT UNIT command will commence in 5 seconds
   ALL data on PD6 will be DESTROYED
   Press control-C to abort

   Format unit has started
   Format unit in progress, 6.93% done
   Format unit in progress, 14.00% done
   Format unit in progress, 21.07% done
   Format unit in progress, 28.13% done
   Format unit in progress, 35.19% done
   Format unit in progress, 42.26% done
   Format unit in progress, 49.32% done
   Format unit in progress, 56.38% done
   Format unit in progress, 63.45% done
   Format unit in progress, 70.50% done
   Format unit in progress, 77.56% done
   Format unit in progress, 84.62% done
   Format unit in progress, 91.69% done
   Format unit in progress, 98.75% done
   FORMAT UNIT Complete
   ```

5. ## option2: format 4k
   ```
   >sg_format.exe  --format --size=4096 PD7
   NETAPP    X371_S164A960ATE  NA54   peripheral_type: disk [0x0]
   Unit serial number: S5JENE0R502223
   LU name: 5002538b01564060
   Mode Sense (block descriptor) data, prior to changes:
   Number of blocks=1875385008 [0x6fc81ab0]
   Block size=520 [0x208]

   A FORMAT UNIT command will commence in 15 seconds
   ALL data on PD7 will be DESTROYED
   Press control-C to abort

   A FORMAT UNIT command will commence in 10 seconds
   ALL data on PD7 will be DESTROYED
   Press control-C to abort

   A FORMAT UNIT command will commence in 5 seconds
   ALL data on PD7 will be DESTROYED
   Press control-C to abort

   Format unit has started
   Format unit in progress, 6.82% done
   Format unit in progress, 13.78% done
   Format unit in progress, 20.73% done
   Format unit in progress, 27.68% done
   Format unit in progress, 34.63% done
   Format unit in progress, 41.58% done
   Format unit in progress, 48.53% done
   Format unit in progress, 55.47% done
   Format unit in progress, 62.42% done
   Format unit in progress, 69.37% done
   Format unit in progress, 76.31% done
   Format unit in progress, 83.25% done
   Format unit in progress, 90.20% done
   Format unit in progress, 97.15% done
   FORMAT UNIT Complete
   ```

{{% /steps %}}

> [!NOTE]
this is where guides & stuff start

## how to navigate
* flowcharts are step by step guides on how i tackled what some would call projects
  * they'll make heavy use of links to topic specific pages
    * would be nice if hugo could render those inline to make a long & complete chart, [perhaps it can](https://gohugo.io/render-hooks/links/#pageinner-details)
* pages per topic are intended to cover very specific items only
  * actual pages are collapsed in menu to reduce clutter
  * to be used as reference when you know what you need
  * building block for flowcharts
  * catagory names chosen for fun, not clarity
* nomenclatur
  * prolly need to add a sas jargon dictionary...

## this all started with me wanting to rip a few cds

and somehow i ended up with 50 sas ssd's, over 20 optical drives, notes and
half finished documentation all over the place, plus some interesting failures.

the focus will lie on using sas hardware when running only windows 11. the concepts
and tools are os agnostic and will work on other operating systems with some common
sense. there's a small chance that a page or 2 on [openbsd](https://openbsd.org) appears,
don't count on it.

##  reminders


stuff that should show up here / my todo list

* easy to find, mostly corrent
  * basic sas hba: airflow, bandwidth, external connections
  * using dbpoweramp: testing actually bitrotted discs, secure ripping pitfalls
  * full tower cases as drive storage
* easy to find, mostly outdated (so these are updates or rewrites)
  * which sas hba you need
  * sas cabling needs, quality of cabling, sata devices choking on some sas cables
  * which tool does what & how: sg3_utils, smartmond, storcli
  * why sas instead of sata
* hard to find, mostly correct
  * crapness of sff-8482 molex power plugs
  * drive power draw, 12v rails, sata 3.3v pin reassign
  * going from 8644 to hba to 8644-8643 adapter (xi / xixe / xe)
  * totally safe way to to combine a paperclip and psu
  * t10 dif stuff (mostly for seagate drives)
* hard to find, incorrect, ancient. the things that took effort and time.
  * optical drives borked power connectors
  * sector size for sas disks (512/520/4096) - and how to change them
    * most likely what you're here for
  * monitoring sas ssd's
  * flashing sas drives with more recent firmware
  * how not to flash optical drives
  * sas expander stuff:
    * daisy chaining
    * firmware flashing
    * mixed drive use
    * sas expander and towercase as disk enclosure
    * 520byte drives and how they make windows storage commands hang
  * hotplugging sata drives on sas controllers and the tiny risk on overvoltage
* and some words about
  * ses communication
  * out of band connector cable
  * stp (sata tunneling protocol)
