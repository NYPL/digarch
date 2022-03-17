---
title: On-Site Transfers
layout: default
nav_order: 0
parent: Transfers
---

## On-Site File Transfers

{: .no_toc }

When the Library acquires a copy of digital files, rather than the digital carriers themselves, Digital Archives prefers to make the copy on-site instead of bringing the carrier to the lab, copying, and returning.

## Preparing the Transfer

* Use acquisition dossiers to understand the scale of the transfer.
* Contact the donor or organization for further details about:
  * the types of carriers (external drives, network storage, etc)
  * the available connections to the carriers (USB3, Thunderbolt, Ethernet, etc)
  * space available for a 2-3 week period
  * best times to complete the transfer
* Coordinate with LSC Collection Management about transport to and from the site.

## Equipment

* Check that you have the appropriate equipment for the transfer.
* Test that all equipment works before the site visit.

### Storage

* [ ] 8-16 TB USB External Hard Drive

Or

* [ ] 126TB RAID
* [ ] RAID power cord
* [ ] Thunderbolt 3 cord
* [ ] Thunderbolt 3 to Thunderbolt 2 adapter
* [ ] RAID Pelican case

### Laptop

* [ ] Laptop with Thunderbolt 2/3 ports and/or USB3-A/C ports
* [ ] Laptop power supply

### Potential Additional Supplies

* [ ] Pelican rollaway case
* [ ] USB A 10-receptacle hub
* [ ] USB hub power supply
* [ ] USB 3.1 A receptacle to USB-C plug adapter
* [ ] USB 3.1 B - USB 3.1 A cables
* [ ] USB 3.1 Micro B - USB 3.1 A cable
* [ ] Power strips
* [ ] USB3 write-blocker

## Transfer

* When you arrive, discuss the following with the site contact:
  * contact information and hours of site access
  * any documentation that might be useful for provenance
  * expectations for repeated access (e.g. adding sets of hard drives)
* Establish an expected completion date with LSC Collection Management and update as needed.

### Equipment Setup

Make sure all cables are run safely, such as around the back of a table.

* Find uninterrupted power source for extension cord.
* Connect the laptop, transfer storage, and and additional equipment to extension cord.
* Connect the transfer storage to the laptop.
* Connect any additional equipment to the laptop.
* Boot the laptop and check that all equipment works.
* Do not connect to network unless required for the transfer.

### Connecting Source Hard (if necessary)

Repeat this process until no additional ports are available.

* On the laptop, open the system disk manager or utility to check the status of drives.
* Connect the source drive to laptop or hub and turn on the power.
* Remount the source drive as read-only. Device numbers are available in the disk manager.

  ``` bash
  diskutil umount /dev/sda[]
  diskutil mount readOnly /dev/sda[]
  ```

* Generate a file name and file size manifest of drive and save to the transfer drive

  ``` bash
  find /path/to/drive -type f -print0 | xargs -0r stat -f '%N, %z' | sort  > /path/to/transfer/storage/sourcedrive.csv
  ```

* In a text editor, create the command to transfer the source drive to its own folder on the transfer drive

  ``` bash
  rsync -rtP /path/to/source/drive /path/to/transfer/storage/sourcedrive/
  ```

### Connecting Source Network Drives

To be written{: .label .label-yellow }

### Starting Transfers

* Chain together the transfer commands with semi-colons to run them sequentially.
It is typically faster to copy from source drives sequentially, instead of simultaneously.

  ``` bash
  rsync -rtP ... ; rsync -rtP ... ; rsync -rtP ... ; ...
  ```

* Check transfer speed and calculate when an additional visit will be necessary to add new drives or to complete the transfer.
For the number of expected days: `[total amount on drives in MB] / [transfer speed in MB] / 3600 / 24`

### Disconnecting Hard Drive Transfers

* Compare the size of the source drive to the folder on the transfer drive.

  ``` bash
  du -sh /path/to/source/drive
  du -sh /path/to/transfer/storage/sourcedrive/
  ```

* Generate a file name and file size manifest of folder on the transfer drive and save it to the transfer drive.

  ``` bash
  find /path/to/drive -type f -print0 | xargs -0r stat -f '%N, %z' | sort > /path/to/transfer/storage/sourcedrive_transferred.csv
  ```

* Investigate any discrepancies between the manifests and retransfer if necessary.

  ``` bash
  comm -2 -3 /path/to/transfer/storage/sourcedrive.csv /path/to/transfer/storage/sourcedrive_transferred.csv
  ```

* Unmount the source drive.
* Disconnect completed drive from hub

### Equipment Tear Down

* Unmount the transfer drive and any additional equipment.
* Power down the transfer drive.
* Power down the laptop.
* Disconnect all power.
* Place equipment back into Pelican cases.
* Return to LSC with equipment using Library provided transportation.
