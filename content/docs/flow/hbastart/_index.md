---
date: '2025-09-04T16:54:32+02:00'
title: 'first steps in the sas world'
weight: 20
---

# goal

reuse enterprise drives in home pc.

## initial setup
* windows 11 24h2
* asrock {{< elink "x670e" "x670e pg lightning" >}} , uefi 3.30
* ryzen 8700g
* wd black sn850x 8tb - no heatsink version
  * slot m2_1
  * slot m2_4
  * using heatsinks included with motherboard
* decent 800w psu

## hardware to add
* netapp x371 disk

{{<image src="humblebrag.jpg" alt="A placeholder" title="A placeholder" loading="lazy">}}

## steps

{{% steps %}}
1. ### find a device you want to connect.
    in general this should be a sata or sas device. sata express and pcie devices can already be excluded.

1. ### figure out what connection is needed
    have a look at the type of connector your device has to figure out the exact type. {{< elink "iface" "details here" >}}

1. ### select hba
    > [!IMPORTANT]
    > this will be the most important choice you'll make
    #### vendor
    there are only 3 valid players left on the market: broadcom, microchip & atto.
    ##### broadcom
    * by far the dominant player
    * their older products can are sold under the "lsi" or "avago" brand name
    * almost all hba's and raid controller from vendors like hp, dell, ibm, lenovo, etc... are actually broadcom devices. 
    ##### microchip
    * also known as microsemi, adaptec & pmc-sierra
    * no current oem cards that i know of
    * market share tiny compared to broadcom but they're trying to make a comeback
    ##### atto
    * no experience with their hba's
    #### controller mode
    * you want a "hba" controller, also known as "it mode" for older controllers.
    * you do not want a raid controller, even if it's running in jbod mode.
    * you do not want a "sas expander"
    #### the fine print
    there might be some non obvious limitations for certain devices. they are mentioned in the manuals, which i recommend reading. at this stage in your journey they might not stand out, so here is the {{< elink "oops" "list of caveats" >}} i've found.
    #### some controllers i have used
    * {{< elink "lsi-9300-4i" "lsi 9300-4i (hba)" >}}
    * {{< elink "b9500-16e" "broadcom 9500-16e (hba)" >}}
    * {{< elink "mraid12g" "cisco mraid 12g (raid)" >}}
    * {{< elink "perc730" "dell perc h730 (raid)" >}}
    > [!IMPORTANT]
    > current advise: broadcom 9500 series
    * non-oem (so actual broadcom) highly suggested over oem versions
    * 2 connectors recommended (so 9500-16i, or 9500-8e/16e)
    * cheaper alternative: lsi 9300-8i or 9300-4i4e
    #### selection criteria
    * current needs and possible future needs
    * price
    * eol/eos timeframe
    * amount and type of connectors
    * power/heat

1. ### get cables

1. ### install hba, drivers-firmware-airflow

1. ### read small print (like 9300 doesn't do sata1, 9600 doesn't do sas, etc...)

1. ### storcli & sg3 utils

1. ### connect device

1. ### initialize, update fw, reformat

1. ### profit


{{% /steps %}}
