---
title: Using Tableau Write Blockers
layout: default
nav_order: 1.1
parent: Transfers
---

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

These are instructions on how to connect drives using either the Tableau Ultrakit [forensic bridges](/digarch/tools/ultrakit.html) or FRED panel Ultrabay [write blockers](/digarch/tools/ultrabay.html).

## Connect cables

### Power cables

* Connect the power supply to the forensic bridge.
  - Device cables are available in the yellow case or cabinet by the cord board. 
* Connect the device to power.
  - Connect devices with external power as usual.  
  - Connect uncased internal devices to power through the forensic bridge with a 3M drive power cable or a Molex to 3M drive power cable.  

### Host computer cables
* Connect the forensic bridge to the host computer via Firewire or USB.

### IDE device cables

* Connect the blue Host side of an IDE cable to the forensic bridge. Connect the black side to the device.  

## Set internal hard drives to single or master

* Make sure the jumper pins on the hard drive are set to single or master.  
  * Look for a schematic displaying where to place a shunt on the pins or etched labels on the circuit board.  
  * Research the hard drive model number if you can't find the jumper configuration on the drive.  

## Power on

* Switch on power on the forensic bridge. Switch on the device with transfer media.  
* Look for Power, Write Block, Host, Device, and, Activity lights to turn on.  
* Turn the device off and on again if the Activity light does not turn on after a minute. Turn the forensic bridge off and on if not resolved.
  * Zip disk drives almost always need to be turned off and on before they will connect. This may also be necessary between Zip disks.  

## Check device connection

* Look for the device under Disk Utility if you don't see a prompt indicating the device has been connected.
* When imaging legacy media the device might only appear in the FTK Imager drive list.  

## Completing a transfer

* Contact Digital Preservation staff if transfer fails.
* Turn the device and the forensic bridge off once the media has been transferred.  
* Disconnect the cables and place them back in the case or the labeled drawers.  
  * If you are using an Ultrakit bridge, place it back in the case.  
* Place the media on the Transferred shelf.
