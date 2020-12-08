# Disclaimer

I'm no longer maintain this config repo due to migrating into a new build here. https://github.com/chiendo97/Hackintosh-Intel-AsRock-Z490-Phantom-ITX-TB3

But I think this is still usefull for anyone has the similar build.

Long live Hackintosh.

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
**Video Card** | [MSI GeForce RTX 2080 8 GB SEA HAWK X](https://pcpartpicker.com/product/b7qhP6/msi-geforce-rtx-2080-8gb-sea-hawk-x-video-card-geforce-rtx-2080-sea-hawk-x)

## What work and what doesn't

### Works:
- IGPU: `master` branch uses IGPU as headless. you can switch to branch `igpu` to use IGPU for monitor.
- Ethernet
- Onboard Audio (including digital audio)
- Sleep/Wake
- USB 3.1 
- Thunderbolt 3 (I tested with a USB Hub Type C)
- iMessage and Facetime
- Handoff
- Bluetooth & Wi-Fi (via Broadcom adapter)
- Airdrop Continuity
- ALL DRMs:
  - iTunes Movies (FairPlay 1.x)
  - Netflix (FairPlay 2.x/3.x)
  - Some Amazon Prime content, but not all. (FairPlay 2.x/3.x)
  - Apple TV+ (FairPlay 4.x)
- Power Nap
- NVRAM

### Doesn't work:
- MSI GeForce RTX 2080 8 GB SEA HAWK X (disable through OpenCore)

### Not Yet Tested

- FileVault
- Sidecar: I don't have Ipad to test.

## Step By Step Instructions

I literally just followed the [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/). 
When you have troubles, take look at my kexts, drivers and config.list for guidance.

#### The SSDT's I ended up using are:

- SSDT-AWAC : Fix Clock
- SSDT-EC-USBX : Fix EC and USB powers.
- SSDT-PLUG : For CPU
- SSDT-PMC : NVRAM
- SSDT-UIAC : Mapping USB

#### Note: Don't use any SSDT you don't know usage.

## USB Port Map & SSDT

I can get a lot of information over here: [TonyMacX86 Topic](https://www.tonymacx86.com/threads/success-asrock-z390-phantom-gaming-itx-tb3-igpu-mojave-sff-build.277418/)

For mapping, I used `SSDT-UIAC.aml` with vanila `UsbInjectAll` kext. I'm not using custom `UsbInjectPorts` kext.

However I decided to use a bit different configuration from that guide:

### Used ports: 

- HS01: Internal header
- HS14: Internal header for bluetooth
- HS10, SS07: Front USB3 and USB2
- HS11, SS08: Front USB3 and USB2
- HS03, HS04: Back Top USB 2
- HS05, HS06: Back Middle USB 2
- HS08, HS09: Back Bottom USB 2
- SS01, SS02: Back Top USB 3

Only after mapping those necessary 14 ports, my TB3 port works.

## Changelogs

- 18/5/2020: Update README
- 17/5/2020: Initial config
