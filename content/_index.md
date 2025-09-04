+++
date = '2025-09-03T21:45:43+02:00'
draft = false
title = "home"
type = "docs"
+++
# a collection of technical notes.

## disclaimer
to the best of my knowledge all information compiled here is correct is correct
at the time of writing. even better, it was tested. if something does not work as
expected or you do not agree, you are free to [open an issue](https://github.com/inphobia/inphobia.github.io/issues).

my crystal ball is out for repair, so do provide the needed context when doing so.

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
* run some test with how images are handled
* start adding actual content

## this all started with me wanting to rip a few cds

and somehow i ended up with 50 sas ssd's, over 20 optical drives, notes and
half finished documentation all over the place, plus some interesting failures.

the focus will lie on using sas hardware when running only windows 11. the concepts
and tools are os agnostic and will work on other operating systems with some common
sense. there's a small chance that a page or 2 on [openbsd](https://openbsd.org) appears,
don't count on it.


stuff that should show up here / my todo list

* easy to find, mostly corrent
  * basic sas hba: airflow, bandwidth, external connections
* how not to flash sata optical drives
  * using dbpoweramp: testing actually bitrotted discs, secure ripping pitfalls

* easy to find, mostly outdated (so these are updates or rewrites)
  * which sas hba you need
  * sas cabling needs
  * which tool does what & how: sg3_utils, smartmond, storcli
  * why sas instead of sata

* hard to find, incorrect, ancient. the things that took effort and time.
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
