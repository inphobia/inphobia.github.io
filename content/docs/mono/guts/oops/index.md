---
title: 'non obvious limitations'
params:
  eid: oops
---
# unexpected limitations

## no sata 1.5gbps support (optical drives)
starting from the 9300 series broadcom no longer mentions support for 1.5gbps sata, only 3gbps & 6gbps. this should not be an issue for disk drives, but optical drives (cd, dvd, blu-ray) most often use 1.5gbps connections.

## no sata 3gbps support
broadcom's 9600 series only supports 6gbps sata

## lto (tape) support
broadcom states the 9500 series should support lto drives but they do not explicitly test this. the 9600 series however has no current nor plannned support for lto drives (likely due to not supporting "transport layer retries").

