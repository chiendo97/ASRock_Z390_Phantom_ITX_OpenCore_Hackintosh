# Hackintosh for ASRock Z390 Phantom Gaming-ITX/ac via OpenCore

<p align="center">
  <img src="https://i.imgur.com/1lqffJF.png" alt="About this mac specs">
</p>

This is mainly here for my benefit more than anyone elses, but you're welcome to use or modify these files in any way if you believe they can be of assistance to you.

However, make sure you set the following:

- SystemSerialNumber
- SystemUUID
- MLB


## Hardware

Type|Item
:----|:----
**CPU** | [Intel Core i5-9400 2.9 GHz 6-Core Processor](https://pcpartpicker.com/product/V4RzK8/intel-core-i5-9400-29-ghz-6-core-processor-bx80684i59400)
**Motherboard** | [ASRock Z390 Phantom Gaming-ITX/ac Mini ITX Motherboard](https://pcpartpicker.com/product/fvQG3C/asrock-z390-phantom-gaming-itxac-mini-itx-lga1151-motherboard-z390-phantom-gaming-itxac)
**Video Card** | [Gigabyte Radeon RX 580 8 GB Gaming 8G Video Card](https://pcpartpicker.com/product/KQQRsY/gigabyte-radeon-rx-580-8gb-gaming-8g-video-card-gv-rx580gaming-8gd)

## What work and what doesn't

### Works:
- IGPU: you can switch to branch `igpu` to use IGPU
- Ethernet
- Onboard Audio (including digital audio)
- Sleep/Wake
- USB 3.1 and Thunderbolt 3
- iMessage
- Facetime
- Handoff
- Bluetooth & Wi-Fi (via Broadcom adapter)
- Airdrop
- Continuity
- ALL DRMs:
  - iTunes Movies (FairPlay 1.x)
  - Netflix (FairPlay 2.x/3.x)
  - Some Amazon Prime content, but not all. (FairPlay 2.x/3.x)
  - Apple TV+ (FairPlay 4.x)
- Power Nap
- NVRAM


### Doesn't work:

* Onboard Wifi: Won't work, I removed it and replaced with DW1560 Broadcom BCM94352Z Card
* Sidecar: I don't have Ipad to test.

### Not Yet Tested

- FileVault

## Step By Step Instructions

I literally just followed the [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/). When you have troubles, take look at my KEXTs, drivers and config.list for guidance.

#### The SSDT's I ended up using are:

- SSDT-AWAC
- SSDT-EC-USBX
- SSDT-PLUG
- SSDT-PMC
- SSDT-UIAC

## USB Port Map & SSDT

You can get a lot of information over here: https://www.tonymacx86.com/threads/success-asrock-z390-phantom-gaming-itx-tb3-igpu-mojave-sff-build.277418/

However I decided to use a bit different configuration from that guide. 

### Used ports: 

- HS01, HS14: Internal header
- HS10, SS07: Front USB3 and USB2
- HS11, SS08: Front USB3 and USB2
- HS03, HS04: Top USB 2
- HS05, HS06: Middle USB 2
- HS08, HS09: Bottom USB 2
- SS01, SS02: Top USB 3

## Changelogs

- 17/5/2020: Initial config
