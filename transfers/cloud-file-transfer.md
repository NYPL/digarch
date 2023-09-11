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

# Cloud Transfer Preparation:
Before beginning a file transfer confirmation with Donors and Collections Management about what material is being acquired is essential. Transfer from cloud storage will often require the sharing of permissions or access to the storage location for the duration of the transfer, this should be communicated with the Donor. Digital Archives does not acquire or retain system files, hidden files, deleted files or files containing personally identifiable information. See our [Acquiring Born Digital Material](/sitevisits/acquiring-born-digital.html) page for more information.

* Acquire link to cloud storage location from donor. Have google drive location shared with Digital Archives staff by donor. 

# File transfer with Rclone: 
Rclone is a command line program for managing files on cloud storage. Using rclone for filetransfers requires cnfiguring storage locations as saved remote locations. For detailed installation and configuration instructions visit our dedicated [rclone](https://nypl.github.io/digarch/tools/rclone.html) page.

* Open Terminal. 

* Enter rclone md5sum remote:path/to/source path/to/destination.txt --exclude ".*" -P
    * Note: ".txt" is included to save checksums to a text file. 
    * Note: remote is the code for a pre-configured remote location
    * Note: --exclude ".*" will exclude any files with name beginning with ".", this is to exclude hidden system files.
    * Note: "-P" allows you to track progress.

* Enter rclone copyto remote:path/to/source path/to/destination --exclude ".*" -P

# Create Destination Package:
Before initiating a cloud file transfer a destination package should be creating following Digital Archives specifications for file transfers described below:

/ACQ_four-digit-acquisition-id
└── /ACQ_four-digit-acquisition-id_six-digit-spec-id
    ├── metadata
    └── objects

Visit SPEC for the acquisition id assocated with colelction material to be transfered. Born-Digital material acquired as a file transfer package is considered a single object in SPEC. Visit the object record in SPEC for the associated six digit SPEC id. An example file transfer package is described below:

/ACQ_1234
└── /ACQ_1234_123456
    ├── metadata
    └── objects

Files accuired via cloud transfer can be moved into a file transfer package using the ft_packager.py script: 

* Open terminal 
* Run ft_packager.py by entering ```python3 ft_packager.py -s path/to/source/directory -d path/to/destination/directory```
    * Note: destination directory should be the objects folder in a file transfer package stucture.