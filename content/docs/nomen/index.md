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

- connector: physical connector to plug in cables
- controller: generic term for both hba's and raid adapters
- hba: host bus adapter, sas controller to allow direct access to disks
- sas:
- {{< elink "iface#sas-1" "sff-8482:" >}} most common connector to connect to sas disks
- port: collection of phy's
- phy: part of sas assembly that creates the physical link

## the whole shebang
todo - lots to add

- sas speeds
  - sas-1: 3gb/s
  - sas-2: 6gb/s
  - sas-3: 12g/s
  - sas-4: 22.5gb/s
- tri mode card
- sas address

- controller
- hba
- jbod
- raid

- narrow port: port that is connected using only 1 phy
- wide port

- sas expander
  - sas edge expander (connects 128 devices)
  - sas fanout expander (connects 128 edge expanders) - 1 per sas domain
- sas domain max 16384 sas ports / adresses

- connector: physical connector to plug in cables
  - connector assembly
  - connector mechanical

- phy
- lane: only used in pcie context; not sas context

