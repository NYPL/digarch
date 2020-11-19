---
title: Site Visit File Transfers
layout: default
nav_order: 4
parent: Site Visits
---

# Site Visit File Transfers
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction


 Born digital collection material can be acquired through file transfer or forensic imaging. Most material will be transferred using a Bagit script through command line. 

 The file transfer workflows are detailed in this document. The workflows may vary based on media types and file types encountered. Transferring material during a site visit will differ from transferring material in the lab. At the time of a site visit no collection number will be assigned to the material and no media log inventory will exist for the material. 

**Be sure to pad your estimates of transfer time. Transfer always takes longer than estimated.**
1. Name the Transfer

2.  Build SIPs

3.  Transfer files from media object

## Name the Transfer
At the time of a site visit no collection number will be assigned to the material. 
* Use a collection name such as the name of the institution you are acquiring from or the personal name of the creator.
     * The Foundry Theatre ```foundryTheatre```  
     * Lou Reed papers ```louReed```  
* Add ```additions``` to the transfer name when you are acquiring additions.  
     * Bill T. Jones additions ```billTJonesadditions```



## Build SIPs
These instructions show you how to create SIPs using a one-line command to create directories.  


On Windows: 
* Start Cygwin from the desktop. A terminal like screen should appear.

On Mac:
* Open Terminal.  

On all operating systems: 

* ``mkdir`` command can be used to create SIPs. This works when SIPs aren't consecutively numbered. 0001 to 0009 require a different line from 0010 on. 
* Change to fileTransfers directory.  
```$ cd filetransfers```
* Enter ```mkdir``` command.  
```mkdir -p CollID/Media-000{1..9}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-00{10..99}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-000{1,5,7,9}/{metadata/submissionDocumentation,objects}```  



### SIP structure

* /M0021

     * /metadata

          * /submissionDocumentation

     * /objects

## Transfer files from media object

Files that have been updated by the donor within the past 30
 days should be quarantined for 30 days to ensure that
 all virus definitions are up to date.

* Use a write-blocker to connect the drive to the computer.
     * [Ultrakit](../tools/ultrakit){:target="_blank"}, [Portable Forensic Bridges](../using/using-lab-equipment#portable-forensic-bridges){:target="_blank"}

### Bagit Script

* Run [ft.sh ](../software#ftsh){:target="_blank"} to create a transfer package.   

On Windows: 
* Start Cygwin from the desktop. A terminal like screen should appear.

On Mac:
* Open Terminal.  

On all operating systems: 
 * Enter the alias ```FT``` and hit return.

Or

* Enter ```/usr/local/bin/ft.sh``` and hit return if the alias is not set.

* Drag the SIP folder from the media object to the window and hit return as prompted.

* Enter the MediaID [EX: ```M0021```] for the file transfer and hit return.

* The terminal prompt will display below when the process is complete.

### Rsync
Bagit may fail when attempting to copy hidden or system files. Use rsync when you determine it is the better tool for a transfer. It might be possible to use rsync in the event Bagit fails. Make sure you have enough time to start a new transfer. When you don't have enough time the transfer will need to take place another time.

On Windows: 
* Start Cygwin from the desktop. A terminal like screen should appear.

On Mac:
* Open Terminal.  

On all operating systems: 
* Enter ```rsync -arP targetpath destinationpath```
* A trailing slash on the destination path copies contents of a folder not the folder itself.
* The selected options represented in the command are ```--archive --recursive --progress --partial```.
* Exclude files using ```--exclude=.DS_Store``` or ```--exclude-from 'exclude-list.txt'```
