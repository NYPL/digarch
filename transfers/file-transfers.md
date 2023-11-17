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

**Before a media object can be transferred it first must be recorded SPEC.**

## Prepare destination folders for files

**These instructions show you how to prepare destination folders for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive ID numbers or you are only transferring one media object.**  

<!--Windows instructions should go here-->

<!--May actually need to move the descriptive information on cygwin and wsl up here cause this can be done via terminal-->
On Windows via WSL:

* Start WSL (Windows Subsystem for Linux) by searching for Ubuntu or selecting the Ubuntu icon on the Windows task bar.

Note: If you search for WSL you may come across the WSL app with a penguin icon, this is an older version of WSL and NOT the version currently used by Digital Archives

* On opening the WSL terminal navigate to the mount point directory by entering ```cd /mnt```

* Any mounted drives, such as those you are transferring between, should be accessible from the mount point directory. Drives you'll see in /mnt include:
  * d - Sata Drive Bay
  * f - Storage for FTK
  * h - Open FTK cases
  * i - Codemeter access key
  * y - DigArchDiskStation

* If you do not see the Y:\ drive in /mnt or /mnt/y appears to be empty then it must be re-mounted by:
  * Changing to the top level directory by entering ```cd /```
  * Entering the command ```sudo mount -t drvfs Y: /mnt/y```

* Change to fileTransfers directory by entering ```cd /mnt/y/Staging/ingest/fileTransfers```

* Run [makesips script](https://nypl.github.io/digarch/tools/software.html#makesips-script){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

or

* Use ``mkdir`` command to create directories when media aren't consecutively numbered:

  * Enter ```mkdir``` command.  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID{1..9}/{metadata,objects}```  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID{10..99}/{metadata,objects}```  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID{1,5,7,9}/{metadata,objects}```  

On Mac:

* Open Terminal.

* Navigate to DigArchDiskStation  

* Change into fileTransfers directory.  
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/fileTransfers```

* Create a directory for the acquisition if it does not exist.  
```$ mkdir ACQ_acqID```  

* Change into the acquisition directory.  
```$ cd ACQ_acqID```  

* Run [makesips script](https://nypl.github.io/digarch/tools/software.html#makesips-script){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to fileTransfers directory.
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/fileTransfers```
  * Enter ```mkdir``` command.  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID{1..9}/{metadata,objects}```  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID{10..99}/{metadata,objects}```  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID{1,5,7,9}/{metadata,objects}```  

### Directory structure

* /ACQ_1234_123456
  * /metadata
  * /objects

## Transfer files from media object

Files that have been updated by the donor within the past 30
days should be quarantined for 30 days to ensure that
all virus definitions are up to date.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.

* Use [rsync](../software#rsync){:target="_blank"} to create a transfer package.

### Rsync

Rsync is a command utility used for copying and syncing file locations, both locally and remotely. More information about rsync can be found on the [rsync documentation page](https://linux.die.net/man/1/rsync) and [installation instructions](../software#rsync) can be found in our software section.

On Windows via WSL:

* Open WSL terminal

Note: rsync will require a source path (the path to the disk of associated media carrier) and destination path (path to the fileTransfers directory in DigArchDiskStation ). Both paths should meet requirements for the terminal being used.

* Enter ```rsync -arP sourcepath destinationpath```

* An example rsync command may look like: ```rsync -arP /mnt/g/ /mnt/y/Staging/ingest/fileTransfers/acquisition-folder/carrier-folder/objects```


On Mac:

* Open Terminal.

* Enter ```rsync -arP sourcepath destinationpath```

* An example rsync command may look like: ```rsync -arP /Volumes/path/to/media/carrier /Volumes/DigArchDiskStation/Staging/ingest/fileTransfers/acquisition-folder/media-folder/objects```

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
