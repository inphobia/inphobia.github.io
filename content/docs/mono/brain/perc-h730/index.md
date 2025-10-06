---
date: 2025-09-19T07:07:17+02:00
title: dell perc h730
description: dell perc h730
params:
  eid: perc730
---
# dell perc h730
dell perc h730 (i think) with 1gb cache and battery backup

# todo perhaps h730p

## general specs
* controller: lsi sas3108 (megaraid 9300 series - likely 9361-8i)
* host interface: pcie3
* sas 12, 6 & 3gb/s
* sata 6 & 3gb/s

## opinion

* pro
  * saved from eol server, so free
  * battery pack
  * supports 4k sector size drives
  * 2 sff-8643
* con
  * pcie3
  * gets very hot quickly
  * raid card, not hba. didn't try to reflash to hba mode
    * could not get the "switch to hba mode" working
  * actual battery, no non volatile memory

## images
![front](h730f.jpg)
![back](h730b.jpg)
