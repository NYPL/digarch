---
title: Transfers
layout: default
nav_order: 3
has_children: true
---

## Transfers
{: .no_toc }

### &nbsp;
{: .no_toc .text-delta }

1. TOC
{:toc}

Born digital collection material can be acquired through file transfer or forensic imaging.
The workflows vary based on media types and file types encountered but the general steps are as follows:  

1. Image or transfer files from the media object.  
2. Acquiring basic metadata about the media and files.  
3. Preparing the files for later archival processing.

**Before a media object can be imaged it first must be recorded in the collection’s media log in CMS.**

### File Transfers

During the file transfer process, some or all of the files are transferred from the original media using standard file copying tools.
Processing archivists may assist in determining which files to transfer.
The most common method of transfer uses a Bagit script via command line.

* Hard drives, USB drives, and other mass storage devices are transferred using a [BagIt script](file-transfers.html).
* CDs, DVDs and other optical media are transferred using a [Nimbie Robot](nimbie-transfers.html)  

### Forensic Imaging

Forensic imaging is reserved for cases where imaging facilitates viewing or accessing material.
For instance, some legacy file formats cannot be viewed on recent operating systems.
Imaging this material allows it to be viewed in an emulator.
Floppy disks and Iomega disks are usually imaged.
Forensic imaging may also be used as a fallback method when file transfers are unsuccessful.

* [Floppy disk images](floppy-disk-imaging.html) are created using the Kryoflux Disk System.
* [Optical media](optical-media-imaging.html) (CD-R/DVD-R) are imaged using the dd command.
* Hard drives, and removable media such as USB thumbdrives, and [Iomega disks](iomega-disk-imaging.html) are imaged with FTK Imager.

### Vendor Transfers

When the lab does not have the proper drive to access a type of media the media may be sent to a vendor for transfer.  

### Network Transfers

In some cases born-digital material may be transferred over a network. Accessioning procedures for these types of transfers are still in progress.
