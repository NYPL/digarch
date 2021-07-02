---
title: Optical Media Imaging
layout: default
nav_order: 7
parent: Transfers
---

## Optical Media - CD-R/DVD-R

**Before a media object can be imaged it first must be recorded in the collection’s media log in CMS. See [Verifying inventory in Media Log](/digarch/transfers/verify-inventory.html){:target="_blank"} for instructions.**

### Build destination directories

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

### Image discs

* Place the optical media in the optical drive.
* Open CMS and locate the collection that you will be working with. Navigate to the electronic records view through the collection management screen. Click on the media number that you are going to image from the “other objects” list. Check in with Digital Preservation staff if the media object is not listed in CMS.
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

### Metadata
Deprecated
{: .label .label-red }
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
