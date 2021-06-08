---
title: Digital Forensic Imaging Overview
layout: default
nav_order: 4
parent: Transfers
---


# Digital Forensic Imaging
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction

Born digital collection material can be acquired through file transfer or forensic imaging. Most material will be transferred using a Bagit script through command line. Forensic imaging is reserved for cases where imaging facilitates viewing or accessing material. For instance, some legacy file formats cannot be viewed on  recent operating systems. Imaging this material allows it to be viewed in an emulator. Floppy disks and Iomega disks are usually imaged.   

The forensic imaging workflows are detailed in the [Transfers](transfers/transfers.html) section of this site. Currently, there are three ways disk images are created on a forensic workstation. [Floppy disk images](floppy-disk-imaging.html) are created using the Kryoflux Disk System. [Optical media](optical-media-imaging.html) (CD-R/DVD-R) are imaged using the dd command. Hard drives, and removable media such as USB thumbdrives, and [Iomega disks](iomega-disk-imaging.html) are imaged with FTK Imager. These workflows cover imaging the media, acquiring basic metadata, and preparing the files for staging for archival processing. The workflows may vary based on media types and file types encountered but the general steps are as follows:  


1. Image the media object.  
2. Extract metadata from the filesystem of the image.  
3. Package the SIP.    
     
**Before a media object can be imaged it first must be recorded in the collection’s media log in CMS.**   

