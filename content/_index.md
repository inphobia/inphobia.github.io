+++
date = '2025-09-03T21:45:43+02:00'
draft = false
title = "home"
type = "docs"
+++
# a collection of technical notes.

## disclaimer
to the best of my knowledge all information compiled here is correct
at the time of writing. even better, it was tested. if something does not work as
expected or you do not agree, you are free to [open an issue](https://github.com/inphobia/inphobia.github.io/issues).

my crystal ball is out for repair, so do provide the needed context.

## for now

atm trying to find & test options to add content with the least amount
of effort to add & maintain:
* a basic formatter to offload html and image generation
* a way to handle simple metadata like links & layout.

if you are seeing this you stumbled upon me testing hugo, after having
found a theme seems to be able to run without the need for js.

expect typos and engrish.

next up:
* mock up structure
  * how about
    * things i wanted to get done & how i did em
    * reference lists (sas hw , usage , other hw, etc)
    * doable with front matter tags i guess
    * reworking lists seems pretty doable if need be
* run some test with how images are handled
* start adding actual content

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
  * why sas instead oof sata
* hard to find, mostly correct
  * drive power draw, 12v rails, sata 3.3v pin reassign
  * going from 8644 to hba to 8644-8643 adapter (xi / xixe / xe)
  * totally safe way to to combine a paperclip and psu
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
