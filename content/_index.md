---
date: '2025-09-03T21:45:43+02:00'
title: a collection of technical notes
description: a collection of technical notes
bookToC: false
params:
  eid: technotes
---
# a collection of technical notes.

> [!INFO]
> the content that's online needs some organization, you can
> use the next button on every page except this one and
> cycle through all content. there are no trackers except the
> one github might use, almost no js & full source is in my repo.  
>  
> {{< elink "here" "here" >}} is where to start   
>  
> things with todo are personal reminders. you'll see all content
> finished or not this way.  
> or whatever
>  
> take care & control

> [!WARNING]
> work in progress  
> typos and engrish ahead

## disclaimer
> [!IMPORTANT]
> to the best of my knowledge all information compiled here is correct at the time of writing.  
> even better, it was tested.

if something does not work as expected or you do not agree, you are free to [open an issue](https://github.com/inphobia/inphobia.github.io/issues).

my crystal ball is out for repair, so do provide the needed context.

## reformat sas drives to 512/4096 block size
the 2 needed steps:
* find disk {{< elink "cyclops" "example" >}}
* format {{< elink "redist" "example" >}}  
still need to fully write out these steps

> [!NOTE]
this is where guides & stuff start

## no idea where to start?
{{< elink "here" "here" >}} or {{< elink "orhere" "here" >}} are good options.
here explains how to go from no sas to some sas, while here is a collection of technical notes without a grand goal but i feel are important.

## how to navigate
> [!INFO]
many pages are still being fleshed out and are empty or incomplete, as indicated by "todo".
* flowcharts are step by step guides on how i tackled what some would call projects
  * they'll make heavy use of links to topic specific pages
    * would be nice if hugo could render those inline to make a long & complete chart, [perhaps it can](https://gohugo.io/render-hooks/links/#pageinner-details)
* pages per topic are intended to cover very specific items only
  * actual pages are collapsed in menu to reduce clutter
  * can be used as reference when you know what you need
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

## global todo list


stuff that should show up here / my todo list

* easy to find, mostly corrent
  * basic sas hba: airflow, bandwidth, external connections
  * using dbpoweramp: testing actually bitrotted discs, secure ripping pitfalls
  * full tower cases as drive storage
* easy to find, mostly outdated (so these are updates or rewrites)
  * ~~which sas hba you need~~
  * sas cabling needs, quality of cabling, sata devices choking on some sas cables
  * which tool does what & how: sg3_utils, smartmond, storcli
  * why sas instead of sata
* hard to find, mostly correct
  * crapness of sff-8482 molex power plugs
  * drive power draw, 12v rails, sata 3.3v pin reassign
  * ~~going from 8644 to hba to 8644-8643 adapter (xi / xixe / xe)~~
  * totally safe way to to combine a paperclip and psu
  * t10 dif stuff (mostly for seagate drives)
* hard to find, incorrect, ancient. the things that took effort and time.
  * optical drives borked power connectors
  * sector size for sas disks (512/520/4096) - and how to change them
  * monitoring sas drives
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
  * sata support in netapp shelves (or any shelf for that matter)
  * ses communication
  * out of band connector cable
  * stp (sata tunneling protocol)
