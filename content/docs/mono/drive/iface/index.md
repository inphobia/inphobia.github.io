---
date: 2025-09-13T00:43:46+02:00
title: drive connectors
description: drive connectors
params:
  eid: iface
---
# common drive interface types
and how to identify them. adapters, expanders, backplanes and all those goodies have a wider array of connector types.

> [!important]
> beware the difference between `connector assembly` and `connector mechanical`.
> the connector mechanical refers to the physical layout, the assembly to the exposed connections.
> this document goes into the `connector mechanical` aspect.

# todo explain better

## connector keying
keying refers to the physical layout of the connectors so it's not physically possible to plug in the wrong type of cable.

### sata
![](k-sata.svg)

### sata express
![](key-sata-express.svg)

### sas
![](key-sas.svg)

### enterprise pcie
![](key-spcie.svg)

## close ups

### sata
power and data plug are separate connectors with a split between the two.

![badsata](badsata.jpg)

### sas

#### eia-966 (sff-8482 and friends) - (aka: sas connector)
- sff-8482: serial attachment 2x unshielded connector
- sff-8680: serial attachment 12gb/s 2x unshielded connector 
  - electrically complaint to support 12gb/s
  - sometimes known as high speed sff-8482

your basic sas disk connector. both power and data are in a single connector with a notch where the split is between sata connectors. this will prevent you from using sata power and/or data on sas disks. the opposite side of the notch also has pins, these are for sas dual port use. the notch itself doesn't have pins.

top:\
![sastop](sastop.jpg)

bottom:
![sasbottom](sasbottom.jpg)

#### sff-8630 / sff-8640
- sff-8630: serial attachment 12gb/s 4x unshielded connector
  - also know as sas multilink and sas x4
  - todo: backplane only?
- sff-8640: serial attachment 24gb/s 4x unshielded connector

resembles eia-966/sff8482 but with a more pins on the opposite side of the notch. the notch itself doesn't have pins.

### enterprise pcie

#### sff-8639 (u.2/u.3)
- sff-8639: multifunctional 12gb/s 6x unshielded connector
- sff-ta-1001: universal multilink x4 version of sff-8639

a full loadout of pins: on the bottom, top and notch.

![sn100](sn100.jpg)

top:
![sn100top](sn100top.jpg)

bottom:
![sn100bottom](sn100bottom.jpg)

### todo u.2/u.3 pin usage difference
