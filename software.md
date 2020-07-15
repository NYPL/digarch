---
title: Software
layout: default
nav_order: 3
has_children: true
---


# Software
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Types of Software
The following is a list of software used in born-digital workflows at NYPL.
### 7-zip  
7-zip is used in the lab to compress evidence and cases generated in Forensic Toolkit. It is also occasionally used to unpack collection material that is not supported by FTK. 
#### Install 7-zip binary  
[Download 7-zip](https://www.7-zip.org/){:target="_blank"}  

### AWS  
Amazon Web Services features S3 and Glacier are used to store copies of born-digital material both before and after the collection has been processed by archivists.  

Using the AWS dashboard requires a login. 

### Bagit.py  
Bagit.py is used to transfer born-digital material to storage. Bagit creates file manifests that help to ensure transfers are complete and free of errors.  

#### Installation  
Check python version  
``` python --version ```  
or  
``` python3 --version ```  
then install  
``` pip install bagit ```  
or  
``` pip3 install bagit ```  

### BitCurator
BitCurator is a Linux distribution with a suite of open source digital forensics and data analysis tools used in the lab as both a virtual machine and as bootable OS alongside Windows. BitCurator is used for transfer and metadata extraction, especially for formats unrecognized in Windows and Mac environments.  
 
#### Installation  
Download software
[BitCurator VM or Live CD](https://github.com/BitCurator/bitcurator-distro/wiki/Releases){:target="_blank"}  

[Current release of VirtualBox](https://www.virtualbox.org/wiki/Downloads){:target="_blank"}  

The VirtualBox Extension Pack must be installed on the host for shared folder support, USB 2.0/3.0 support, and support for some NVMe SSDs. Once you’ve installed VirtualBox, use the link below the main download on VirtualBox download site to install the Extension Pack on your host.  

Unpack the BitCurator Virtual Machine.  

Once you’ve installed VirtualBox and the VirtualBox extension pack, start up VirtualBox.  

Add Virtual Machine  
From the menu bar, select the menu item “Machine -> Add…”, and navigate to the folder containing .vbox file that you extracted. Choose that file, and the Virtual Machine should appear in the list within the manager.

### dBpoweramp
dBpoweramp is used in conjunction with Iromlab and the Nimbie to transfer born-digital material from optical media to storage.

### dd  
The command line utility dd is used in the lab to create disk images of optical media. In most cases transfers are made of optical media instead of disk images.  
#### Use  
In the terminal type  
``` dd if=/dev/sr0 of=/cygdrive/z/ingest/diskImages/CollID/MediaID/objects/MediaID.iso ```  
Hit return  
Once complete the terminal will display bytes copied and return to a blank prompt.  

### Disk Utility  
On MacOS Disk Utility is used in the lab to confirm that removable media is properly mounted.  

### DiskPart  
On Windows DiskPart command line utility is used in the lab to confirm that removable media is properly mounted.  
#### Use
Type  
``` list disk ```  
or  
``` list volume ```  
to confirm media is mounted.  

### disktype
Disktype is used on MacOS in the lab to extract filesystem metadata such as sector format for floppy disks.  

#### Installation  
``` brew install disktype ```  
#### Use  
 ``` cd <diskDirectory> ```  
 ``` diskype <disk.001> ```  

### Filemaker Pro 17  
Filemaker is used by Preservation and Collection Services as a collection management system. Born-digital media is inventoried in Filemaker and PCP tracks projects through Filemaker.
#### Installation 
Installing Filemaker requires license keys. Make sure you have the proper keys and permissions before installing.
#### Use
<!-- Should be its own page. -->
### Forensic Toolkit
Forensic Toolkit is used in the lab to appraise, and arrange born-digital material. 
#### Installation
Forensic Toolkit is licensed software and requires a dongle to open. The software can be downloaded from [AccessData](https://accessdata.com/product-download){:target="_blank"}  
#### Use
<!-- own page -->
### gtar
Gtar is used on a Mac in the lab to compress KryoFlux stream files. It is called through the command line with the bash alias 'compress'.
#### Installation
``` brew install gnu-tar ```
### Iromlab
Iromlab is used in conjunction with dBpoweramp and the Nimbie to transfer born-digital material from optical media to storage.
### Java  
Java is required for tools like DROID and Bagger.  
#### Use
Try commands  
``` which java ```  
and  
``` java -version ```  
if you are encountering java errors. You may need to put the path of the correct version of java in your bash profile.  
In Windows you can use the search from the start menu to check the java version. Type 'about java' into search. Then click the About Java icon result.  
### openssl
openssl is used in the lab to SSH between computers. SSH is used to run workflow scripts located on ARCHV Mac.
### Oracle VM VirtualBox
VirtualBox is used in the lab to run the BitCurator environment as a virtual machine.  
#### Installation  
Current release of [VirtualBox](https://www.virtualbox.org/wiki/Downloads){:target="_blank"}  

The VirtualBox Extension Pack must be installed on the host for shared folder support, USB 2.0/3.0 support, and support for some NVMe SSDs. Once you’ve installed VirtualBox, use the link below the main download on VirtualBox download site to install the Extension Pack on your host.  
### pip 
Pip is used in the lab to install and upgrade Python modules like bagit.py.
#### Use
Pip should be installed with python3. Call pip with  
``` pip``` or ``` pip3 ```  
depending on your installation.  
Check python version  
``` python --version ```  
or  
``` python3 --version ```  
### Python3
Python3 is used in the lab to run a a variety of scripts, including bagit.py.
#### Installation
Windows:  
Check python version  
``` python --version ```  
Installers are available at [python.org](https://docs.python.org/3.8/using/windows.html#windows-full){:target="_blank"}  

Mac:  
Check python version  
``` python3 --version ```  
Replace the number below with the version you wish to install.  
``` brew install python@3.8 ```  
BitCurator:  
Check python version  
``` python3 --version ```  
Replace the number below with the version you wish to install.  
``` sudo apt-get install python3.8 ```
### QuickTime Player
QuickTime is used in the lab to appraise Macintosh formatted born-digital video.  
### rsync
Rsync is used in the lab to transfer born-digital material when bagit.py is unable to complete a transfer. Rsync is used when transferring from a computer backup or a drive with a large number of system files.  
#### Installation
Mac:  
``` brew install rsync```  
### Siegfried  
Siegfried is used in the lab to identify and validate file formats. Siegfried output also includes checksums, useful when rsync is used for transfer instead of bagit.py.
#### Installation  
Windows:  
[Download binary](https://github.com/richardlehane/siegfried/releases/download/v1.8.0/siegfried_1-8-0_win64.zip){:target="_blank"}  
Mac:  
```brew install richardlehane/digipres/siegfried```  

#### Use  
Current installations of siegfried use the config file to store preferred command options.  
``` sf -setconf -csv -hash sha1 -z ```  
sets the preferred command options.  
Find a complete list of sf commands with  
``` sf -help ```  
### Sha1deep  
Sha1deep is used in the lab to identify duplicate material across digital media in a collection. It is usually used in bash scripts. 
#### Installation  
Mac:  
``` brew install m5deep ```  
#### Use  
Here is an example of how to use sha1deep to transfer only unique files from media.  
Write checksums of transfer volume to file  
``` sha1deep -r [directory or volume] >> collnumber.sha1 ```  
Write path of unique files per directory or volume to file with mediaid  
``` sha1deep -rx [path to checksums file] [directory or volume] >> [path to checksums for media] ```  
Remove ds_store from unique file list  
```sed '/.DS_Store/d' [path to file list] > [file list]```  
change terminal path out of home directory  
```cd ../../```  
Navigate to the media being transferred to avoid /Volumes/HD/folders being copied within media-id directory.  
Make sure spaces are not escaped in paths. “ “ not “\ “  
Transfer unique files  
```rsync -aPF --files-from=[path to file list] .   [path to media]```  
### tree  
Tree is used in bash scripts in the lab to identify contents of media including number of folders and files.  
#### Installation  
Mac:  
```brew install tree```
### VLC  
VLC multimedia player is used in the lab to view and appraise born digital audio and video.  
#### Installation  
https://www.videolan.org/vlc/index.html  
## Scripts  
The following is list of scripts used in born-digital workflows at NYPL. The scripts are located in the [digarch_scripts](https://github.com/NYPL/digarch_scripts/blob/main/){:target="_blank"} Github repository. A link to each script is provided after the description.  
### ft.sh 
This script is used in the lab to create bagit transfers and Siegfried csvs for born-digital media.  
[ft.sh ](https://github.com/NYPL/digarch_scripts/blob/main/Mac/ft.sh){:target="_blank"}   
### kryofluxmove.sh  
This script is used in the lab to move KryoFlux disk images to folders with the MediaIDs of the disks.  
[kryofluxmove.sh](https://github.com/NYPL/digarch_scripts/blob/main/Mac/kryofluxmove.sh){:target="_blank"}
### metadata.sh  
This script is used in the lab to move metadata from disk images to folders with the MediaIDs of the disks.  
[metadata.sh](https://github.com/NYPL/digarch_scripts/blob/main/Mac/metadata.sh){:target="_blank"}  
### Brunnhilde with disktype  
This script is used in BitCurator to identify disk image type and pass the type to Brunnhilde to generate the correct output.  
[Brunnhilde with disktype](https://github.com/NYPL/digarch_scripts/blob/main/BitCurator/brudt.sh){:target="_blank"}  
### makesips script
This script is used to create a consecutive number of submission information packages for material from digital media.   
[makesips script](https://github.com/NYPL/digarch_scripts/blob/main/Mac/SIPdir.sh){:target="_blank"}  
Alternatively, ``mkdir`` command can be used to create SIPs. This works when SIPs aren't consecutively numbered. 0001 to 0009 require a different line from 0010 on.  
```mkdir -p CollID/Media-000{1..9}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-00{10..99}/{metadata/submissionDocumentation,objects}```  
```mkdir -p CollID/Media-000{1,5,7,9}/{metadata/submissionDocumentation,objects}```  
### moveimages script  
This script is used in the lab to move a disk image into the objects folder of a SIP.  
[moveimages script](https://github.com/NYPL/digarch_scripts/blob/main/Mac/kryofluxmove.sh){:target="_blank"}  
### movemetadata script  
This script is used in the lab to move metadata into the metadata folder of SIP.  
[movemetadata script](https://github.com/NYPL/digarch_scripts/blob/main/Mac/metadata.sh){:target="_blank"}  
### movephotograph script  
This script is used in the lab to copy JPEGS of media from the photographs directory on the staging drive to the submissionDocumentation directory in the MediaID directory of SIPs.  
[movephotograph script](https://github.com/NYPL/digarch_scripts/blob/main/Mac/movephotograph.sh){:target="_blank"}  
### FACTools  
This script is used in the lab to repackage Finding Aid Component packages.  
[FACTools](https://github.com/NYPL/digarch_scripts/blob/main/Mac/qctools.sh){:target="_blank"}  
### iterative scripts  
Scripts are created per collection using a directory listing as input in a while loop. This allows previous move scripts to run per collection rather than one MediaID.  
### CMS metadata import  
This script is used in the lab to import metadata from transfers to the FileMaker Collection Management System. Currently, output from the Nimbie (Iromlab) is used.  
## Previous and Occasional Software  
The following is a list of software used in previous workflows. These tools can be used when transfer fails with current tools.  
### Emailchemy  
Emailchemy has been used in the lab to migrate email formats.  
### ePADD  
ePADD has been used in the lab to appraise and arrange email.  
### DROID  
DROID has been used in the lab to identify and validate file formats.  
### MediaInfo  
MediaInfo has been used in the lab to extract metadata from born-digital video.  
### FTK Imager  
FTK Imager has been used in the lab to image media and extract files from media.  
### IsoBuster  
IsoBuster has been used in the lab to image optical media and extract files from media.  
### Bagger  
Bagger has been used in the lab to transfer born-digital material.  
## Legacy Format Appraisal  
The following is a list of software used in the lab to view legacy formats not supported by FTK.  
### WinUAE  
WnUAE has been used in the lab to view Amiga files.  
### apple3rtr  
Apple3rtr has been used in the lab to view Apple II files.  
### miniVmac  
MiniVmac has been used in the lab to view legacy Mac files.  
### DosBox  
DosBox has been used in the to view DOS executables and word processing files.  
### QuickView Plus  
QuickView Plus has been used in the lab to view a range of legacy formats like word processing and photo formats.  
### CiderPress  
CiderPress has been used in the lab to view Apple file formats.  
### HFS Explorer 
HFS Explorer has been used in the lab to view files on HFS filesystems.  
### Sheepshaver
Sheepshaver has been used in the lab to view legacy Mac files.  