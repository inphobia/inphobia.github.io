---
title: hba firmware
description: hba firmware
params:
  eid: hbafw
---
# todo - wip

## firmware choice
you cannot flash firmware downloaded from broadcom to devices that are not broadcom or lsi labeled. while many controllers from vendors like cisco, hpe, dell, lenovo, etc... are broadcom cards, they do have a unique subsys id, as such you must use the vendor's firmware.


## expander firmware
expander is not relevant, it's functioning is transparent and makes no difference if it's a hba or raid controller that's speaking with them.

todo better words; link {{< elink "revive" "expander fw update" >}} & {{< elink "82885t" "adaptec 82885t expander overview" >}}

## no firmware downloads here {anchor=false}
i will not upload controller or disk firmware to this site. if the vendor no longer has firmware for a device on their site i would suggest checking archive.org. if all else fails you can try to contact me - figuring out how is the litmus test.
