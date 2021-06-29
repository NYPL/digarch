---
title: Floppy Disk Imaging
layout: default
nav_order: 5
parent: Transfers
---

## Floppy Disks  


**Before a media object can be imaged it first must be recorded in the collection’s media log in CMS.**

### Image disks

#### Getting set up

* Connect the KryoFlux.
  * Ensure the floppy drive is correctly connected to the Kryoflux. 
  * Attach the KryoFlux USB cable from the forensic workstation to the Kryoflux board. See a green power light glow on the Kryoflux board.  
  * Attach the AC power cable to the power supply. See the green LED on the power supply light up. Listen for a faint click from the disk drive.   
  
**See the [KyroFlux page in the Tools section for more](https://nypl.github.io/digarch/tools/kryoflux).**

* Open CMS and locate the collection that you will be working with.
  * Navigate to the electronic records view through the collection management screen.
  * Click on the media number that you are going to image from the “other objects” list. (Check in with Digital Preservation staff if the media object is not listed in the CMS.)

* Calibrate the KryoFlux.
  * Open the KryoFlux software from the desktop "kryoflux-ui.jar".
  * Click on the drive menu and ensure that ‘Drive 0’ is selected.
  * Select ‘calibrate’ from the drive menu, then ‘yes’ from the pop-up window. When the calibration is complete you should see the message ‘calibration is successful, the maximum number of tracks available is: 83’.
  * Calibrate only once when you begin a session, unless calibration fails.  

* Follow these steps if the KryoFlux is unable to communicate with the drive.  
  * Close the application.  
  * Disconnect the power source from the drive.  
  * Disconnect the USB cable from the KryoFlux board.  
  * Reconnect the USB cable to the KryoFlux board.  
  * Reconnect the power source to the drive.  
  * Try connecting a different drive if there is still no communication after the the previous steps.  

#### Imaging

* Insert the floppy disk into the drive.
* Enter the media object ID (for example, M11111-4444) in the "Enter name ..." text field in the Kryoflux imaging software.  
* Determine the filesystem format of the disk.
  * “MFM sector image” is usually the correct format for PC disks, “Apple DOS 400/800k” is usually the correct format for Apple Macintosh disks.
  *  Test the disk if you're unsure about the format. Select a format in the dropdown underneath the name field and click "start" to begin imaging the disk. The sector grid displays color as the disk is imaged.  
  * Grey indicates the format is likely incorrect. Try another format.  
  * Green, orange, or yellow indicates the correct sector format has been determined.  
  * Red sectors indicate either the disk or the drive is damaged.

**See the section on [Problem disks](https://nypl.github.io/digarch/transfers/digital-forensic-imaging.html#problem-disks) for more on damaged media.**

* Select “Multiple” from the drop-down below the "Enter name ..." text field when you have determined the correct sector format. Select “KryoFlux stream image” and, while holding down the control key, select the correct sector format from the dropdown. Click ‘ok’ to close the popup.  
* Click the start button to begin the imaging process. The KryoFlux will now create a folder with the name of the id of the media that contains the stream image files and a sector image (again with the name of the media plus an “.001” file extension). Both the stream directory and the sector image file will be written to the kryofluxOutput directory on Staging.  

#### Completing the imaging process

* Put the media back in the collection’s box and move or remove the pink “To image” flag as necessary if you are working on a large collection. Move the media to the “Small collections complete” box if you are working on a small collection without a box.  
* Enter the following information about the image in CMS:  

Under ‘Image Information’  
interface:	Kryoflux  
imaging software:	Kryoflux Imager  
image successful:	Yes | No  
interpret successful:	Yes | Yes w/Errors | No  
* Use ‘yes w/errors’ if a few red sectors were observed with the KryoFlux software.  

sector format:	select the sector format from the dropdown  
image format:	raw  
imaged by:	your name  

* Select the current date under ‘Progress’  for the ‘Imaging done” field.  

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

### Create destination directories

**These instructions show you how to create destination directories for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers.**  
* Open Cygwin and enter the following commands:   

* Connect to ARCHV Mac.  
```$ ssh archv```  

* Change to diskImage directory.  
```$ diskimages```  

* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  

* Change into your collection directory.  
```$ cd M1111```  

* Run the program to build structured directories. The program will ask you for your collection name and the first and last number of items of the directories you’d like to build.  
```$ makesips```  

### Package images

* Open Cygwin and enter the following commands:
* Connect to ARCHV Mac.  
```$ ssh archv```
* Change to the kryrofluxOutput directory.  
```$ kryofluxoutput```  
* Run the command to tar the stream files.  
```$ compress```  
* Run the program to move files from kryofluxOutput to the appropriate subdirectory in diskImages.  
```$ moveimages```  

### Problem disks
<!-- Change to delete problem images? -->
* Move disk images that are all errors or have unidentifiable file systems to the /problems directory in the Staging drive.
* Move logs for problem disk images to the /problems directory in the Staging drive.
* Move KryoFlux stream files folders to the /problems directory in the Staging drive.
* Select “Problem” from the “Issues” drop-down menu in the medialog and note the issue in the “Notes” field.
