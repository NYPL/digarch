---
title: Cloud File Transfers
layout: default
nav_order: 8
parent: Transfers
---

# Cloud File Transfers
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction
Born-digital collection material can be acquired through file transfer from cloud based storage locations. This page describes Digital Archives workflow for preparing for a cloud based file transfer, creating a destination package using ft_packager.py and transferring material using rclone. The instructions detailed on this page are specific to transfers from google drive, but are adaptable to other cloud storage contexts.  

# Before File Transfer:
Before beginning a file transfer confirmation with Donors and Collections Management about what material is being acquired is essential. Transfer from cloud storage will often require the sharing of permissions or access to the storage location for the duration of the transfer, this should be communicated with the Donor. Digital Archives does not acquire or retain system files, hidden files, deleted files or files containing personally identifiable information. See our [Acquiring Born Digital Material](/sitevisits/acquiring-born-digital.html) page for more information.

* Acquire link to cloud storage location from donor. Have google drive location shared with Digital Archives staff by donor.

# Workstation Preparation: 
Born-digital material held in cloud storage is first transferred with rclone to a temporary working folder on a Digital Archives Lab workstation or a RAID connected to a Digital Archives Lab workstation.

* Connect RAID to Lab Workstation or Login to Lab Workstation
* Open Terminal 
* Create temporary working folder on RAID or on Lab Workstation by entering ```mkdir path/to/working/folder```
    * Note: Folder should be named following file transfer naming convention, ```ACQ_four-digit-acquisition-id_six-digit-spec-id```. Acquisiton, Collection and SPEC ID information can be found in teh associated [SPEC](link to SPEC listing in ) records. 
* Navigate into temporary work folder by entering ```cd path/to/working/folder```
* Create an empty folder named "payload" in temporary working folder by entering ```mkdir ACQ_four-digit-acquisition-id_six-digit-spec-id/payload```.


# File transfer with Rclone: 
Rclone is a command line program for managing files on cloud storage. Using rclone for filetransfers requires configuring storage locations as saved remote locations. For detailed rclone installation and configuration instructions visit our dedicated [rclone](https://nypl.github.io/digarch/tools/rclone.html) page.

* Confirm working folder created in the [Workstation Preparation]()section is the current working directory in terminal. 

* Transfer md5 checksum manifest for materials by entering ```rclone md5sum remote:path/to/source path/to/working/folder/md5-manifest.txt --exclude ".*" -P```
    * Note: "md5-manifest.txt" is included to save checksums to a text file. 
    * Note: remote is the code for a pre-configured remote location
    * Note: --exclude ".*" will exclude any files with name beginning with ".", this is to exclude hidden system files.
    * Note: -P  flag is included to visually track progress.

* Transfer the materials payload by entering ```rclone copyto remote:path/to/source path/to/working/folder --exclude ".*" --log-level INFO --log-file=path/to/working/folder/rclone.log -P```
    * Note: --exclude ".*" will exclude any files with name beginning with ".", this is to exclude hidden system files.
    * Note: --log-level is included to save a log file of process, --log-file= should be followed by a path to a .log file in the working folder
    * Note: -P  flag is included to visually track progress.

# Create Cloud File Transfer Package with package_cloud.py:
After born-digital material, transfer log, and checksum manifest have been transferred to a temporary working folder Digital Archives Staff repackage the files to meet file transfer specifications using [package_cloud.py](link to listing in software tools page). Digital Archives specifications for file transfers described below:

/ACQ_four-digit-acquisition-id
└── /ACQ_four-digit-acquisition-id_six-digit-spec-id
    ├── metadata
    └── objects

/ACQ_1234
└── /ACQ_1234_123456
    ├── metadata
    └── objects

The packager_cloud.py script requires five inputs for repackaging: 
* Payload files: 
* Md5 hashes
* Rclone log
* Output directory
* Package name
