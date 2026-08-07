# 01 — Hardware

## Why this box?

€150 on eBay. For that price you get DDR4 memory, 12 threads and four SFP+ ports — nothing else in that range comes close. The only catch is the vendor firmware, and that's what OPNsense is for.

**Good to know:** there's no exotic hardware inside — Intel NICs, an Intel CPU and an AMI (American Megatrends) BIOS. It's a standard x86 server in a firewall chassis. The BIOS is vendor-customised, though, which is where most of the surprises come from (see [BIOS](03-bios.md)).

## Specifications of the documented unit

| Item | Value |
|---|---|
| Model / revision | Barracuda F800, revision `F CCE` <!-- CONFIRM on your unit + say where the label is --> |
| CPU | Intel Xeon E5-2620 v3 (6 cores / 12 threads, 2.4 GHz) |
| RAM | 24 GB DDR4 <!-- TO FILL: how many sticks, ECC or not, free slots --> |
| Storage as shipped | 430gb SSD SATA |
| Storage installed | SATA drive 2.5 |
| Copper interfaces | 16 ports (Intel i350)  |
| SFP+ interfaces | 4 × (Intel X710) |
| Power supply | 2 x PSU (redundant) |
| Console | Serial port RJ45 in 19200 baud ( for the BIOS, OPNSENSE listen in 115200 )|
| Price paid | €150 (eBay, used) |

## Opening the chassis


![Inside the F800](assets/f800-inside.jpg)

## Networking

The four SFP+ ports are the main reason this box is worth the money at this price.


Port-to-interface mapping is covered in [Networking](05-networking.md).

## Living with it

**Noise.** Rack-appliance cooling, designed for a datacenter rather than a living room. Around 75 decibels in normal use


## No video output

There is no usable video output during boot. Everything — BIOS, installer, first boot — goes through the serial console. This is the single biggest stumbling block for anyone new to these appliances, and it is covered in [Serial console access](02-serial-console.md).

## What you need before starting

- [ ] Console cable RJ45
- [ ] USB-to-serial adapter
- [ ] USB stick for the installer (8 GB or more)
- [ ] A SATA drive
- [ ] Screwdriver 
- [ ] SFP+ modules or DAC cables, if you plan to use those ports
