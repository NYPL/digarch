---
title: KryoFlux
layout: default
nav_order: 6
parent: Transfer Equipment
grand_parent: Tools
---

# KryoFlux
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction  
KryoFlux is used in the lab to image 5.25" and 3.5" floppy disks. Kryoflux is a hardware and software system that can read, convert, store, and write contents of various legacy disk formats. The system consists of a control board and a Java application, DiskTool Console (DTC). DTC refers to the command line interface. The DTC folder contains a jar file user interface. Before KryoFlux can be used on a computer for the first time setup must be completed through DTC. Here you will find initial setup instructions and optional settings. To image floppy disks with KryoFlux follow [Digital Forensic Imaging](/transfers/digital-forensic-imaging#floppy-disks){:target="_blank"} instructions.  

## How Kryoflux works  
Magnetic disks store data by changing the orientation of ferro oxide particles bound onto a durable and flexible plastic platter. The data is represented as flux transitions which indicate a change in the polarity of the magnetic field. Kryoflux records data from an attached drive as a flux data stream. Kryoflux can also output disk images in a variety of sector formats. Disk images are used in archival processing.  

## Requirements  
* KryoFlux board  
* USB port  
* Floppy disk drive with standard 34 pin connector  
* Drive cable  
* Drive power supply  

## Assembly and installation
![](/kryoflux/kryoflux-0003.jpg)  
* Note the locations of 
    * the USB connector  
    * the drive select jumpers
    * the write-blocker
    * the floppy disk drive connector  

* Place the KryoFlux board and the disk drive on a flat, non-conductive surface.  
* Connect KryoFlux and drive with floppy data cable. Check for the correct orientation, the
marked wire (usually red or white) signals data line 1. 
* Make sure line 1 is pointing towards drive select jumpers on KryoFlux board.  
* Usually, pin 1 faces left when looking at the drive from above with the drive pointing away from you.
![](/kryoflux/kryoflux-0010.jpg)
![](/kryoflux/kryoflux-0012.jpg)  
* Set the drive select jumpers to the inner position for initial installation. After one drive has been installed you can set the jumpers to the outer (2 drive) position.  
![](/kryoflux/kryoflux-0007.jpg)
![](/kryoflux/kryoflux-0006.jpg)
* Connect the power supply to the drive. Do not connect the power supply to a power outlet yet.  
* Download the [KryoFlux software package](http://kryoflux.com/?page=download){:target="_blank"} and extract it.  

Windows:  
* Copy DTC to the location where you want to execute it.  
* Disconnect from the internet to avoid auto-installation of incorrect drivers.  
* Attach the USB cable to KryoFlux and then attach it to your computer. Do not use a
USB hub.  
* Windows will ask for a driver. Select Browse my computer for drive software. Select “KryoFlux USB driver.inf”. Wait for installation to finish.  
* Open Command Prompt.
* Change to dtc directory.  
```cd KryoFlux\dtc```  
* Enter  
```dtc -c2```  
* Plug power supply into power outlet.   
* Repeat  
```dtc -c2```  
* DTC will check for maximum track access. The seek might fail but this should not interfere with operation.  
* Check to see if Windows 10 installed a Bossa device under COM
ports. In this case, right-click and choose to replace the driver manually. Repeat the instructions after opening Command Prompt.  
* Re-connect Windows computers to the internet.  

Mac: 
* Run KryoFlux.dmg installer.  
* Attach the USB cable to KryoFlux and then attach it to your computer. Do not use a
USB hub.  
* Open Terminal.
* Change to dtc directory.  
```cd KryoFlux\dtc```  
* Enter  
```dtc -c2```  
* Plug power supply into power outlet.   
* Repeat  
```dtc -c2```  
* DTC will check for maximum track access. The seek might fail but this should not interfere with operation.  

BitCurator:
* Install libusb 1.0.9 if it is not already installed.  
* Make sure VirtualBox has the correct USB added.  
* Copy X86 dtc files to usr and lib:  

| Copy | Paste |
| -----------| --------------|
| x86_64/static/dtc | /usr/local/bin/                |
| x86_64/lib* (files starting with lib) | /usr/local/lib/          |
| firmware_kf_usb_rosalie.bin  | /lib/firmware/          |

* Copy kryoflux-ui.jar
* Install gcc-4.9 from Terminal.  
```sudo add-apt-repository ppa:ubuntu-toolchain-r/test```  
```sudo apt-get update```  
```sudo apt-get install gcc-4.9 g++-4.9```  
```sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 60 --slave /usr/bin/g++ g++ /usr/bin/g++-4.9```   
* create/add rule to udev.  
```sudo nano  /etc/udev/rules.d/80-kryoflux.rules```  
* Add lines so the device nodes are owned by the floppy group.  
```ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="03eb", ATTR{idProduct}=="6124", GROUP="floppy", MODE="0660"```  
* Add user to floppy group.  
```adduser -G floppy [username]```  
* Open Terminal.
* Change to dtc directory.  
```cd KryoFlux\dtc```  
* Enter  
```dtc -c2```  
* Plug power supply into power outlet.   
* Repeat  
```dtc -c2``` 
* Restart if needed.  
## Using the GUI
* Double click kryoflux-ui.jar to open the GUI.  Check Java installation if the GUI won't launch.
* The left section of the GUI window displays disk tracks as blocks on side 0 and side 1.  
* Green blocks indicate a track is decoded.  
* Orange blocks indicate a track is decoded and has been modified. The disk has been written to more than once.  
* Grey blocks indicate an unknown sector format or an unformatted disk.  
* Red blocks indicate a track is decoded with errors. Kryoflux will retry the track the number of times indicated in settings.  
* Yellow blocks indicate a track is decoded with warnings. Change sector size until the result is green or orange.  
* Point to a track to get information about the result. The result will output in the status line.  
* The right section of the GUI window displays visualizations of stream files as they are written.  
* The lower section of the GUI window displays track number and information, drive controls, filename, and sector format drop down.  
![KryoFlux GUI window](/kryoflux/kryoflux-0020.jpg)

### Settings  
* The file menu displays Settings.  
* The Image Profiles tab contains most settings for creating disk images.  
* Click Copy to use an existing profile as a template.  
* Click Default check boxes to edit fields.  
* The Advanced tab contains a field to set the number of retries per track.  
![KryoFlux GUI Settings](/kryoflux/kryoflux-0021.jpg)

## DiskTool Console
DTC is the command line interface for KryoFlux. Some options available in DTC are not available through the GUI.
* Enter the following parameters before image type:
    * file name
    * flippy disk mode
    * image type
    * start track
    * end track
    * output image start track
    * output image end track
    * output image track order
    * single sided mode
    * sector size
    * sector count
    * track distance
    * rpm
    * data band threshold
    * extended cell band search

All parameters:  
-f<name> set filename  

-i<type> set image type  

-m<id> set device mode 1=image file, 2=KryoFlux (Model: Rosalie) (default 2)  

-d<id> select drive (default 0)  

-dd<val> set drive density line (default 0) 0=L, 1=H  

-l<mask> set output level, add values to define mask (default 62) 1=device, 2=read, 4=cell, 8=format, 16=write, 32=verify, 64=TI  

-r<rev> set number of revolutions to sample (default by image type)  

-t<try> set number of retries per track, min 1 (default 5)  

-tc<try> set number of retry cycles per track, min 1 (default 2)  

-tm<try> treat missing sectors as bad sectors  
0=off, 1=on (default on)  

-a<trk> set side 0/a track0 physical position (default 0)  

-b<trk> set side 1/b track0 physical position (default 0)  

-s<trk> set start track (default at least 0)  

-e<trk> set end track (default at most 83)  

-g<side> set single sided mode  
0=side 0, 1=side 1, 2=both sides  

-z<size> set sector size  
0=128, 1=256, 2=512, 3=1024 (default 2)  

-n<scnt> set sector count  
0=any, +Z=exactly Z, -Z=at most |Z| (default 0, by image type)  

-k<step> set track distance  
1=80 tracks, 2=40 tracks (default 1)  

-ks use only selected tracks during analysis (default auto)  

-v<rpm> set target system’s drive speed, RPM (default by image type)  

-x<mode> set extended cell band search (default by image type)  
0=image only, 1=all, 2=reference only  

-y set flippy disk mode  

-oo<ord> output image track order, add values to define ord (default by image)  
1=side 0 descending (side 0 ascending if 0)  
2=side 1 descending (side 1 ascending if 0)  
4=side 1 then side 0 (side 0 then side 1 if 0)  
8=side oriented (track oriented if 0)  

-os<trk> output image start track (default by image)  

-oe<trk> output image end track (default by image)  

-ot<pct> data band threshold (default 30)  

-p create path  

-c<mode> read calibration mode  
1=track read, 2=maximum track, 3=RPM  

-pg<type> plot: graph type (default 0)  
0=no graphs, 1=sample, 2=consistency  

-pf<mode> plot: flip mode (default 0)  
0=off, 1=side 1, 2=both sides  

-pw<size> plot: graph width (default 800)  

-ph<size> plot: graph height (default 600)  

-px<fval> plot: graph x origin (default 0.0)  

-py<fval> plot: graph y origin (default 0.0)  

-pd<fval> plot: graph domain (default 0.2)  

-pr<fval> plot: graph range (default 0.000020)  

-w write image to disk  

-wi<type> write: set source image type (default 0)  

-wp<par> write: set platform specific parameter (default 0)  

-wm<mode> write: set mode, add values to define mode (default 0)  

-wy write: write side 1 to side 0, side 1 becomes unformatted  

-y write: -wy for flippy disks imaged in a single pass  

-g<side> write: select sides to write (default auto)  
0=side 0, 1=side 1, 2=both sides  

-k<step> write: set track distance preference in source image  
1=80/all tracks, 2=40/even tracks (default 2)  

-ks<step> write: enforce track distance; disables crosstalk filter  

-wg<side> write: enable unformatted side filter (default 3)  
0=disable, 1=side 0, 2=side 1, 3=both sides  

-wk<side> write: enable track crosstalk filter (default 3)  
0=disable, 1=side 0, 2=side 1, 3=both sides  

-wv<mode> write: verify (default 1)  
0=off, 1=verify  

-ww<ns> write: precompensation window in ns, max 10000 (default auto)  

-wt<ns> write: precompensation time in ns, max 1000 (default auto)  

-wb<bias> write bias (default by image)  
0=neutral, 1=bias out, 2=bias in  

-we<mode> write: erase mode (default by bias)  
0=normal, 1=used only, 2=wipe  

Image types supported for reading from a disk:  

0 KryoFlux stream files, preservation  

0a KryoFlux stream files, format guided  

2 CT Raw image, 84 tracks, DS, DD, 300, MFM  

3 FM sector image, 40/80+ tracks, SS/DS, SD/DD, 300, FM  

3a FM XFD, Atari 8-bit  

4 MFM sector image, 40/80+ tracks, SS/DS, DD/HD, 300, MFM  

4a MFM XFD, Atari 8-bit  

5 AmigaDOS sector image, 80+ tracks, DS, DD/HD, 300, MFM  

6 CBM DOS sector image, 35+ tracks, SS, DD, 300, GCR  

6a CBM DOS sector image with error map  

7 Apple DOS 3.2 sector image, 35+ tracks, SS, DD, 300, GCR  

8 Apple DOS 3.3+ sector image, 35+ tracks, SS, DD, 300, GCR  

8a DSK, DOS 3.3 interleave  

9 Apple DOS 400K/800K sector image, 80+ tracks, SS/DS, DD, CLV, GCR  

10 Emu sector image, 35+ tracks, SS, DD, 300, FM  

11 Emu II sector image, 80+ tracks, DS, DD, 300, FM  

12 Amiga DiskSpare sector image, 80+ tracks, DS, DD/HD, 300, MFM  

13 DEC RX01 sector image, 77+ tracks, SS, SD, 360, FM  

14 DEC RX02 sector image, 77+ tracks, SS, SD/DD, 360, FM/DMMFM  

15 CBM MicroProse sector image, 35+ tracks, SS, DD, 300, GCR  

16 CBM RapidLok sector image, 35+ tracks, SS, DD, 300, GCR  

17 CBM Datasoft sector image, 35+ tracks, SS, DD, 300, GCR  

18 CBM Vorpal sector image, 35+ tracks, SS, DD, 300, GCR  

19 CBM V-MAX! sector image, 35+ tracks, SS, DD, 300, GCR  

20 CBM Teque sector image, 35+ tracks, SS, DD, 300, GCR  

21 CBM TDP sector image, 35+ tracks, SS, DD, 300, GCR  

22 CBM GCR image, SS, DD, 300, GCR  

22a CBM GCR image with mastering info, SS, DD, 300, GCR  

23 CBM Big Five sector image, 35+ tracks, SS, DD, 300, GCR  

24 CBM DOS extended sector image, 35+ tracks, SS, DD, 300, GCR  

25 CBM OziSoft sector image, 35+ tracks, SS, DD, 300, GCR  

Image types supported for writing to a disk:  

0 auto-detect  

1 IPF image  

2 Amiga ADF sector image  

3 CBM G64 image  

4 KryoFlux stream files  
