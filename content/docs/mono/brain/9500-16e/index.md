---
title: hba broadcom 9500-16e
description: hba broadcom 9500-16e
params:
  eid: b9500-16e
---
# broadcom 9500-16e
broadcom branded sas hba with 4 sff-8644 connectors

## general specs
- chipset: broadcom sas3816
- host interface: pcie4 x8 (also supports x4, x2 & x1)
- connectors: 4 sff-8644
- sas 12, 6 & 3gb/s
- sata 6 & 3gb/s
- pcie via x4 switches

## power and cooling
- 8.5w power usage
- airflow 150lfm
- 55°c preferred temperature, storcli says it can do up to 115°c

## opinion

- pro
  - hba
  - 4 connectors
  - active support
  - windows11 24h2 support
  - pcie4
  - power efficient (compared to alternatives)
  - vented half & full size bracket included
  - supports sas & pcie on external ports
- con
  - not cheap
  - no built in internal connectors
  - no direct attach nvme support
  - to many steps to update onboard code (psoc, bios, uefi, those things)
  - external connectors leave little room for airflow through the bracket

## images
![front](9500-16e-f.png)
![bracket](9500-16e-bracket.png)
