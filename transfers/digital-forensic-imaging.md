---
title: Digital Forensic Imaging
layout: default
nav_order: 3
parent: Transfers
---


# Digital Forensic Imaging
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction

Born digital collection material can be acquired through file transfer or forensic imaging. Most material will be transferred using a Bagit script through command line. Forensic imaging is reserved for cases where imaging facilitates viewing or accessing material. For instance, some legacy file formats cannot be viewed on  recent operating systems. Imaging this material allows it to be viewed in an emulator.  

The forensic imaging workflows are detailed in this document. Currently, there are three ways disk images are created on a forensic workstation. Floppy disk images are created using the Kryoflux Disk System. Optical media (CD-R/DVD-R) are imaged using the dd command. Hard drives, USB thumbdrives, and Zip disks are imaged with FTK Imager. These workflows cover imaging the media, acquiring basic metadata, and preparing the files for staging for archival processing. The workflows may vary based on media types and file types encountered but the general steps are as follows:  


1. Image the media object.  
2. Extract metadata from the filesystem of the image.  
3. Package the SIP.    
     
**Before a media object can be imaged it first must be recorded in the collection’s media log in CMS.**   

 
## Floppy Disks  

### Image disks   

* Attach the Kryoflux USB cable from the forensic workstation to the Kryoflux board. See a green power light glow on the Kryoflux board.  

* Attach the AC power cable to the power supply. See the green LED on the power supply light up.  Listen for a faint click from the disk drive.   

* Open CMS and locate the collection that you will be working with. Navigate to the electronic records view through the collection management screen. Click on the media number that you are going to image from the “other objects” list. Contact the Digital Archives Assistant if the media object is not listed in CMS.  

* Open the Kryoflux software from the desktop. Click on the drive menu and ensure that ‘Drive 0’ is selected. Select ‘calibrate’ from the drive menu. Select ‘yes’ from the pop-up window. When the calibration is complete you should see the message ‘calibration is successful, the maximum number of tracks available is: 83’. Calibrate only once when you begin a session, unless calibration fails.  

* Follow these steps if the KryoFlux is unable to communicate with the drive:  
     * Close the application.  
     * Disconnect the power source from the drive.  
     * Disconnect the USB cable from the KryoFlux board.  
     * Reconnect the USB cable to the KryoFlux board.  
     * Reconnect the power source to the drive.  
     * Try connecting a different drive if there is still no communication after the the previous steps.  


* Insert the floppy disk into the drive. Navigate to the text field where you see the words “Enter name...” in the Kryoflux imaging software. Enter the media object ID from the id field in CMS (For example, M11111-4444.) in the text field in the Kryoflux imaging software.  




* Determine the filesystem format of the disk. Select the encoding format from the drop down below the name of the image. “MFM sector image” is usually the correct format for PC disks, “Apple DOS 400/800k” is usually the correct format for Apple Macintosh disks.  

* Click start and begin imaging the disk. The sector grid will fill in with either grey or some type of color (green, yellow, orange red). Try another format if the boxes are filling in grey as it is likely the wrong sector format. Green, orange or yellow indicates the correct sector format has been determined. Red sectors indicate either the disk or the drive is damaged.  

**See the section on Problem disks for more on damaged media.**  



* Select “Multiple” from the drop-down below the “Enter name” text field when you have determined the correct sector format. Select “KryoFlux stream image” and while holding down the control key select the correct sector format from the dropdown. Click ‘ok’ to close the popup.  

* Click the start button to begin the imaging process. The KryoFlux will now create a folder with the name of the id of the media that contains the stream image files and a sector image (again with the name of the media plus an “.001” file extension). Both the stream directory and the sector image file will be written to the kryofluxOutput directory on Staging.  

* Put the media back in the collection’s box and move or remove the pink “To image” flag as necessary if you are working on a large collection. Move the media to the “Small collections complete” box if you are working on a small collection without a box.  



* Enter the following information about the image in CMS:  


Under ‘Image Information’  
interface:	Kryoflux  
imaging software:	Kryoflux Imager  
image successful:	Yes | No  
interpret successful:	Yes | Yes w/Errors | No  
[use ‘yes w/errors’ if a few red sectors were observed with the kryoflux software, such as in the example on the previous page]  


sector format:	select the sector format from the dropdown  
image format:	raw  
imaged by:	your name  


Select the current date under ‘Progress’  for the ‘Imaging done” field.  


### Metadata  

* Open Cygwin and enter the following commands:   

* Connect to ARCHV Mac.  
```$ ssh archv```  

* Change to the kryrofluxOutput directory.  
```$ kryofluxoutput```  

* Run disktype on the disk image to get the file system metadata.  
```$ disktype M1111-0004.001```  

* Use the disk image size output by disktype if it is in kb.  
* Get the size of the disk image using the du command if disktype outputs mb.  
```$ du -ck M1111-0004.001```  

* Copy the size and file system information data into the media object’s CMS record.  









### Build SIPs  
**These instructions show you how to create SIPs for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers.**  
* Open Cygwin and enter the following commands:   

* Connect to ARCHV Mac.  
```$ ssh archv```  

* Change to diskImage directory.  
```$ diskimages```  

* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  

* Change into your collection directory.  
```$ cd M1111```  

* Run the program to build structured SIP directories. The program will ask you for your collection name and the first and last number of items of the SIPs you’d like to build.  
```$ makesips```  



### Package SIPs

* Open Cygwin and enter the following commands:   

* Connect to ARCHV Mac.  
```$ ssh archv``` 

* Change to the kryrofluxOutput directory.  
```$ kryofluxoutput```  

* Run the command to tar the stream files.  
```$ compress```  

* Run the program to move files from kryofluxOutput to the appropriate subdirectory in diskImages.  
```$ moveimages```  

* Change to the diskImages directory and change directory to the objects folder for the media object.  
```$ diskimages```  
```$cd M1111/M1111-0004/objects```  

* Run the program to move metadata files to metadata directory.  
```$ movemetadata```  
 
### Problem disks
<!-- Change to delete problem images? -->
* Move disk images that are mostly errors or have unidentifiable file systems to the /problems directory in the Staging drive.
* Move logs for problem disk images to the /problems directory in the Staging drive.
* Move KryoFlux stream files folders to the /problems directory in the Staging drive. 
* Select “Problem” from the “Issues” drop-down menu in the medialog and note the issue in the “Notes” field.	                  

## Optical Media - CD-R/DVD-R

### Build SIPs  
**These instructions show you how to create SIPs for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers.**  
* Open Cygwin and enter the following commands:   

* Connect to ARCHV Mac.  
```$ ssh archv```  

* Change to diskImage directory.  
```$ diskimages```  

* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  

* Change into your collection directory.  
```$ cd M1111```  

* Run the program to build structured SIP directories. The program will ask you for your collection name and the first and last number of items of the SIPs you’d like to build.  
```$ makesips```  




## Image discs

* Place the optical media in the optical drive.

* Open CMS and locate the collection that you will be working with. Navigate to the electronic records view through the collection management screen. Click on the media number that you are going to image from the “other objects” list. Contact the Digital Archives Assistant if the media object is not listed in CMS.
* Open Cygwin. A terminal like screen should appear.

* Use the dd command to copy optical media in the drive to iso. ```if``` is the input file and ```of``` is the output file.  
```$ dd if=/dev/sr0 of=/cygdrive/z/ingest/diskImages/CollID/MediaID/objects/MediaID.iso```  

* Once complete the terminal will display bytes copied and return to a blank prompt.

* Eject the disc from the drive.

* Enter the following information about the image in CMS :

 Under “Image Metadata’ record the following  
interface:	[Choose DVD Drive]  
imaging software:	dd  
image successful:	Yes | No  
image filename:	M11111-3332  
image format:	iso  
imaged by:	select your name from the dropdown  
image segmented:	Yes | No  

* Select the current date for the ‘Imaging done” field under ‘Progress’.

* Put the media back in the collection’s box and move or remove the pink “To image” flag as necessary if you are working on a large collection. Move the media to the “Small collections complete” box if you are working on a small collection without a box.
.
### Metadata

* Open Cygwin and enter the following commands:   

* Connect to ARCHV Mac.  
```$ ssh archv```  

* Change to the diskImages directory and change directory to the objects folder for the media object.  
```$ diskimages```  
```$cd M1111/M1111-0004/objects```  

* Run disktype on the disk image to get the file system metadata.  
```$ disktype M1111-0004.iso```  


* Copy the file system information data from the output into the media objects CMS record.

* Get the size of the disk image using the du command if disktype outputs mb.  
```$ du -ck M1111-0004.iso```  


* Run the program to move metadata files to metadata directory.  
```$ movemetadata```  


## Optical Media (CD-R, DVD-R) Export

Additionally, a single file system can be extracted from optical media for ease of processing in FTK. The multiple file systems usually available on optical media are redundant in this software.

* Select “Add Evidence Item” from File drop down menu. Select “Logical Image” and highlight F:\ or the source path of the CD drive if using a different drive letter. 



* FTK Imager will display the drive (F:), the session (1), the track (01) and 1-4 file systems (ISO, Joliet, UDF, HFS). (You may also see unpartitioned space and a partition for the CD builder/Disc Recorder but stick to the file systems 1-4 for now.)

* Click the + sign to the left of the F:\ if this information tree is not displayed. 

* Choose file system for export. Click on a folder or name to select it. In the example above the UDF file system has been selected.  

* Select Export Files… under the File menu to extract files from the highlighted file system.

Or

* Right-click on the file system and select Export Files.

* Create a folder in the Evidence directory if you have not already done so and save the extracted files to this location. Follow the path name convention  ```Z:\FTK\Evidence\CollectionID\MediaID```   
```(EX: Z:\FTK\Evidence\M23230\M23230-0152) ```  

**Hint: Navigate to the folder using Windows Explorer, create the folder there,  then click on the folder in the navigation bar to copy the path. Paste this path into FTK Imager Save as.**

* Put the media back in the collection’s box and move or remove the pink “To image” flag as necessary if you are working on a large collection. Move the media to the “Small collections complete” box if you are working on a small collection without a box.
