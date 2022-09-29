---
title: File Transfers
layout: default
nav_order: 2
parent: Transfers
---

# File Transfers
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction

Born digital collection material can be acquired through file transfer or forensic imaging. Most material will be transferred using a Bagit script through command line.

The file transfer workflows are detailed in this document. The workflows may vary based on media types and file types.  

**Before a media object can be transferred it first must be recorded in the collection’s media log in CMS. See [Verifying inventory in Media Log](/digarch/transfers/verify-inventory.html){:target="_blank"} for instructions.**

## Prepare destination folders for files

**These instructions show you how to prepare destination folders for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers or you are only transferring one media object.**  

* Run [makesips script](../software#makesips-script){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

<!--Windows instructions should go here-->

On Mac:

* Open Terminal.
* Connect to ARCHV Mac.  
```$ ssh archv```  
* Change to fileTransfers directory.  
```$ filetransfers```
* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  
* Change into your collection directory.  
```$ cd M1111```  
* Run the program to build structured directories. The program will ask you for your collection name and the first and last number of items of the directories you’d like to build.  
```$ makesips```  

![](media/image8.png)

Or

* ``mkdir`` command can be used to create directories. This works when media aren't consecutively numbered. 0001 to 0009 require a different line from 0010 on.
* Change to fileTransfers directory.  
```$ filetransfers```
* Enter ```mkdir``` command.  
```mkdir -p CollID/Media-000{1..9}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-00{10..99}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-000{1,5,7,9}/{metadata/submissionDocumentation,objects}```  

### Directory structure

* /M2319-0021
  * /metadata
    * /submissionDocumentation
  * /objects

## Transfer files from media object
  Files that have been updated by the donor within the past 30
 days should be quarantined for 30 days to ensure that
 all virus definitions are up to date.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.

* Use [rsync](../software#rsync){:target="_blank"} to create a transfer package.

### Rsync
  Rsync is a command utility used for copying and syncing file locations, both locally and remotely. More information about rsync can be found on the [rsync documentation page](https://linux.die.net/man/1/rsync) and [installation instructions](../software#rsync) can be found in our software section.

On Windows:

* Start Cygwin Terminal from the desktop or by searching for Cygwin via the desktop search bar. 
  
<!--screenshot of cygwin icon --> 

* On opening the Cygwin terminal navigate to the cygdrive folder by entering ```cd /cygdrive```. 

* In order to transfer via rsync you will need a source path and the destination path. Common locations on FRED are: 
  * d - Sata Drive Bay
  * f - Storage for FTK
  * h - Open FTK cases
  * i - Codemeter access key
  * y - DigArchDiskStation

* To access local disks in via cygwin you will need to start paths with ```/cygdrive```.

* To locate the source path open File Explorer on the desktop and navigate to *This PC*. 
  
* Identify the appropriate disk for attached media.

<!--Screenshot of This PC goes here-->  

* Your destination path will be the collection folders you made earlier in filetransfers: ```/cygdrive/y/Staging/ingest/fileTransfers/collection-folder/media-folder/objects```

* An example rsync command to may look like: 

```rsync -arP /cygdrive/g /cygdrive/y/Staging/ingest/fileTransfers/collection-folder/media-folder/objects```

On Mac:

* Open Terminal.

* Enter ```rsync -arP sourcepath destinationpath```

* A trailing slash on the source path copies contents of a folder not the folder itself.

* The selected options represented in the command are ```--archive --recursive --progress --partial```

* Exclude files using ```--exclude=.DS_Store``` or ```--exclude-from 'exclude-list.txt'``

### FT.sh 
Deprecated
{: .label .label-red }
On Mac:

* Open Terminal.
* Enter the alias ```FT``` and hit return.

Or

* Enter ```/usr/local/bin/ft.sh``` and hit return if the alias is not set.
* Drag the destination directory from the media object to the window and hit return as prompted.
* Enter the MediaID for the file transfer and hit return.

* Copy the number of files in payload and the size of payload in kb when displayed in the window.
* Paste the number of files and the size in the File Transfers section of the media log in CMS.
  
<script id="asciicast-mKpfPqUl74R3t30B0tvpfPBQV" src="https://asciinema.org/a/mKpfPqUl74R3t30B0tvpfPBQV.js" async></script>