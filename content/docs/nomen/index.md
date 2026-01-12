---
date: 2025-10-07T00:31:43+02:00
title: nomenclature
description: nomenclature
weight: 549
params:
  eid: nomen
---
# nomen est omen

## basics
{{< elink "glue" "todo: sas topology" >}} todo: sas topology

- connector: physical connection where to plug in cables
- controller: generic term for both hbas and raid adapters
- hba: host bus adapter, sas controller to allow direct access to disks
- sas:
- {{< elink "iface#sas-1" "sff-8482:" >}} most common connector to direct connect sas disks
- port: collection of phy's
- phy: part of sas assembly that creates the physical link

## the whole shebang
todo - lots to add

- sas speeds
  - sas-1: 3gb/s
  - sas-2: 6gb/s
  - sas-3: 12gb/s
  - sas-4: 22.5gb/s
    - marketed as 24gb/s
- tri mode card: card that does sata, sas and nvme
- sas address

- controller
- hba
- jbod
- raid
- nearline sas

- narrow port: port that is connected using only 1 phy
- wide port
- dual port:

- standards (incits)
  - sam: scsi architecture model
  - sbc: scsi block commands
  - spc: scsi primary commands
  - spl: sas protocol layer
  - zbc: zoned block commands


- sas expander
  - sas-2 and later have a simple rule
    - if the expander connects only to the hba & other expanders it may connect as many expanders as it's connectors allow
    - if there are 1 or more end devices attached it may connect **at most** to 2 other expanders, or 1 expander and 1 hba
  - sas-1 defined 2 types of expanders
    - sas edge expander (connects 128 devices)
    - sas fanout expander (connects 128 edge expanders)
- sas domain max 16384 sas ports / addresses

- connector: physical connector to plug in cables
  - connector assembly
  - connector mechanical

- phy
- lane: only used in pcie context; not sas context

- vpd: vital product data
- stp: serial ata tunneled protocol
- smp: sas serial management protocol
- ses: scsi enclosure services
- ssp: serial scsi protocol
