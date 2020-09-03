---
title: Tableau Ultrabay
layout: default
nav_order: 4
parent: Transfer Equipment
grand_parent: Hardware
---

# Tableau Ultrabay
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction  
Tableau Ultrabays are installed on each FRED. These Forensic bridges are used in the lab to prevent writing to collection devices. Ports on the Ultrabay are labeled. These include: SATA/SAS, Drive Power, PCIe, IDE, FireWire, and USB. Cables are available for most devices in the plastic drawers on the bakers rack.  A drive tray slides out below the Ultrabay panel to hold devices while connected.

## Connect cables.  
* Device cables are available in labeled plastic drawers on the bakers rack. 
* Connect devices with external power as usual.  
* Connect uncased internal devices to power through the Ultrabay with a 3M drive power cable or a Molex to 3M drive power cable.  

### USB
* Make sure to connect the USB cable to the USB port on the Ultrabay panel. The USB ports above the Ultrabay are not connected to the forensic bridge.  

### IDE
* Connect the blue Host side of an IDE cable to the Ultrabay. Connect the black side to the device.  

## Set internal hard drives to single or master.  
* Make sure the jumper pins on the hard drive are set to single or master.  
    * Look for a schematic displaying where to place a shunt on the pins or etched labels on the circuit board.  
    * Research the hard drive model number if you can't find the jumper configuration on the drive.  

## Power on.  
* Press power on the Ultrabay panel. Switch on the device with transfer media.  
* Look for Power, Write Block, Host, Device, and, Activity lights to turn on.  
* Turn the device off and on again if the Activity light does not turn on after a minute. Turn the Ultrabay off and on if not resolved.  
    * Zip disk drives almost always need to be turned off and on before they will connect. This may also be necessary between Zip disks.  

## Check device connection.
* Look for the device under Computer if you don't see a Windows prompt indicating the device has been connected.  
* When imaging legacy media the device might only appear in the FTK Imager drive list.  

## Completing a transfer.
* Contact the Digital Archives Assistant if transfer fails.   
* Turn the device and Ultrabay off once the media has been transferred.  
* Disconnect the cables and place them back in the labeled drawers.  
* Place the media on the Transferred shelf.  