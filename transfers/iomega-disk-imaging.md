---
title: Iomega Disk Imaging
layout: default
nav_order: 6
parent: Transfers
---

## Iomega Disks

**Before a media object can be imaged it first must be recorded SPEC.**

This section covers imaging with FTK Imager. Iomega disks are usually imaged with FTK Imager. Use FTK Imager when creating a disk image of a hard drive or removable media.  

### Using Digital Archives scripts
Make sure the setup instructions for Digital Archives [scripts](https://github.com/NYPL/digarch_scripts){:target="_blank"} have been completed before running the scripts in the next section.  

### Create destination directories

**These instructions show you how to create destination directories for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers.**  

On Mac:

* Open Terminal.

* Navigate to DigArchDiskStation.  

* Change into diskImages directory.  
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/diskImages```

* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  

* Change into your collection directory.  
```$ cd M1111```  

* Run [makesips script](https://nypl.github.io/digarch/tools/software.html#makesips-script){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to diskImages directory.  

```$ cd /Volumes/DigArchDiskStation/Staging/ingest/diskImages```  
  * Enter ```mkdir``` command.  
```mkdir -p CollID/Media-000{1..9}/{metadata,objects}```  
```mkdir -p CollID/Media-00{10..99}/{metadata,objects}```  
```mkdir -p CollID/Media-000{1,5,7,9}/{metadata,objects}```  

On Windows via WSL:

* Open WSL.
* If you do not see the Y:\ drive in /mnt or /mnt/y appears to be empty then it must be re-mounted by:
  * Changing to the top level directory by entering ```cd ../```
  * Entering the command ```sudo mount drvfs Y: /mnt/y```
* Change into diskImages directory.  
```$ cd /mnt/y/Staging/ingest/diskImages```

* Create a directory for your collection if it does not exist.  
```$ mkdir M1111```  

* Change into your collection directory.  
```$ cd M1111```  

* Run [makesips script](https://nypl.github.io/digarch/tools/software.html#makesips-script){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to diskImages directory.  

```$ cd /mnt/y/Staging/ingest/diskImages```  
  * Enter ```mkdir``` command.  
```mkdir -p CollID/Media-000{1..9}/{metadata,objects}```  
```mkdir -p CollID/Media-00{10..99}/{metadata,objects}```  
```mkdir -p CollID/Media-000{1,5,7,9}/{metadata,objects}```  
#### Directory structure

* /M2319-0021
  * /metadata
    * 
  * /objects


<!-- ![](media/media/image29.png){width="6.069444444444445in"
height="2.3472222222222223in"} -->

### Image disks

* Connect the Iomega drive to the FRED's Tableau Ultrabay. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.  

* Start FTK Imager from the FRED's launch bar and select
Create New Image from the application's file menu.

<!-- ![](media/media/image9.png){width="0.7395833333333334in"
height="0.5104166666666666in"} -->

* Select Physical Image and click next.

<!-- ![](media/media/image21.png){width="5.0in"
height="3.6666666666666665in"} -->

* Select the drive to be imaged from the drop down menu and
click finish.

<!-- ![](media/media/image23.png){width="4.946247812773404in"
height="3.5879155730533685in"} -->

* Select E01 form the image type menu and click next.

<!-- ![](media/media/image20.png){width="5.008970909886264in"
height="3.433333333333333in"} -->

* Type the collection ID in the Case number field, the
media ID in the Evidence number field, and your name in the
Examiner field. Click next.

<!-- ![](media/media/image12.png){width="5.130208880139983in"
height="3.5120352143482063in"} -->

* Using the browse button, select the objects folder in the
correct collection directory (e.g.
Staging/ingest/diskImages/M1111/M1111-0004/objects). Enter the media
ID into the Image Filename field. Ensure that the image fragment
size is set to 0 and the compression field is set to 9. Click finish.

<!-- ![](media/media/image14.png){width="5.094400699912511in"
height="3.493303805774278in"} -->

* Ensure all check boxes are checked and click Start to
begin the imaging process.

<!-- ![](media/media/image16.png){width="5.590798337707787in"
height="4.778125546806649in"} -->

**FTK Imager will approximate the time needed to image the media.**

<!-- ![](media/media/image8.png){width="5.989583333333333in"
height="3.84375in"} -->

* Make sure that the checksums match on the complete screen, if not imaging was not successful.

<!-- ![](media/media/image19.png){width="4.950121391076116in"
height="4.55in"} -->

### Completing the imaging process

* Put the media back in the collection’s box and move or remove the pink “To image” flag as necessary if you are working on a large collection.  
* Move the media to the “Small collections complete” box if you are working on a small collection without a box.  

### Metadata
Deprecated
{: .label .label-red }
* Open Cygwin and enter the following commands:
* Connect to ARCHV Mac.  
```$ ssh archv```
* Change to the diskImages directory and change directory to the objects folder for the media object.  
`$ diskimages`  
`$cd M1111/M1111-0004/objects`
* Run disktype on the disk image to get the file system metadata.  
`$ disktype M1111-0004.E01`
* Copy the file system information data into the media objects CMS record.
* Run program to move metadata files to metadata directory.  
`$ movemetadata`
