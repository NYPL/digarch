---
title: Software (Draft)
layout: default
nav_order: 5
parent: Tools
has_children: False
---

# Software
{: .no_toc }

Digital Archives utilizes several software throughout our workflows. This page acts as a departmental glossary for these software and includes installation, detailed use instructions and links to official documentation whenever possible. Shorter contextual instructions for these software can be found on the associated pages, consider this page our definitive guides.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Programs:

Programs are defined as any non-internally developed out-of-the-box software used in Digital Archives workflows.

{% for tool in site.data.program %}

### {{tool.name}}:
{{tool.desc}}

#### Installing {{tool.name}}:
{{tool.inst}}

{% comment %}
#### Configuring {{tool.name}}:
{{tool.conf}}

#### Using {{tool.name}}:
{{tool.use}}
{% endcomment %}

{% endfor %}

{% comment %}
### 7-zip

7-zip is used in the lab to compress evidence and cases generated in Forensic Toolkit. It is also occasionally used to unpack collection material that is not supported by FTK. 

#### Installing 7-zip:

[Download 7-zip](https://www.7-zip.org/){:target="_blank"}

#### Configuring: 
#### Using:

### apple3rtr:

Apple /// Ready-to-Run (apple3rtr) is a software bundle used for MAME Apple emulation. It has been used by Digital Archives staff to view Apple II files.

#### Installing: 
For detailed installation instructions visit the (apple3rtr github repo)[https://github.com/datajerk/apple3rtr].

#### Configuring: 
#### Using:

### AWS:

#### Installing: 
#### Configuring: 
#### Using:

### Bagger: 

#### Installing: 
#### Configuring: 
#### Using:

### Bagit.py:

#### Installing: 
#### Configuring: 
#### Using:

### BitCurator:

#### Installing: 
#### Configuring: 
#### Using:

### Brunnhilde with disktype:

#### Installing: 
#### Configuring: 
#### Using:

### clamscan:

#### Installing: 
#### Configuring: 
#### Using:

### CiderPress:

#### Installing: 
#### Configuring: 
#### Using:

### dBpoweramp:

#### Installing: 
#### Configuring: 
#### Using:

### dd:

#### Installing: 
#### Configuring: 
#### Using:

### Disk Utility:

#### Installing: 
#### Configuring: 
#### Using:

### DiskPart:

#### Installing: 
#### Configuring: 
#### Using:

### disktype:

#### Installing: 
#### Configuring: 
#### Using:

### DosBox:

#### Installing: 
#### Configuring: 
#### Using:

### DROID:

#### Installing: 
#### Configuring: 
#### Using:

### Emailchemy:

#### Installing: 
#### Configuring: 
#### Using:

### ePADD:

#### Installing: 
#### Configuring: 
#### Using:

### FACTools:

#### Installing: 
#### Configuring: 
#### Using:

### Filemaker Pro 17:

#### Installing: 
#### Configuring: 
#### Using:

### Forensic Toolkit:

#### Installing: 
#### Configuring: 
#### Using:

### FTK Imager:

#### Installing: 
#### Configuring: 
#### Using:

### gtar:

#### Installing: 
#### Configuring: 
#### Using:

### HFS Explorer:

#### Installing: 
#### Configuring: 
#### Using:

### Iromlab:

#### Installing: 
#### Configuring: 
#### Using:

### IsoBuster:

#### Installing: 
#### Configuring: 
#### Using:

### Java:

#### Installing: 
#### Configuring: 
#### Using:

### MediaInfo:

#### Installing: 
#### Configuring: 
#### Using:

### miniVmac:

#### Installing: 
#### Configuring: 
#### Using:

### openssl:

#### Installing: 
#### Configuring: 
#### Using:

### Oracle VM VirtualBox:

#### Installing: 
#### Configuring: 
#### Using:

### pip:

#### Installing: 
#### Configuring: 
#### Using:

### Python3:

#### Installing: 
#### Configuring: 
#### Using:

### QuickTime Player:

#### Installing: 
#### Configuring: 
#### Using:

### QuickView Plus:

#### Installing: 
#### Configuring: 
#### Using:

### rclone:

[*Rclone*](https://rclone.org/) is a command line tool for managing files on cloud storage, and is one tool used by Digital Archives for moving files between Digital Archives workstations, Google Shared Drives for Divisions, and long term storage. This page lists instructions for installing and configuring rclone.

#### Installing rclone:

For detailed installation instruction tailored to your operating system see the [rclone documentation](https://rclone.org/install/).

For MacOS:
Use Homebrew to install rclone via the terminal by entering:
```
brew install rclone
``` 

For Windows:
[Download and run Windows installation file.](https://rclone.org/downloads/)

#### Configuring rclone:

Once installed, you must configure Rclone which involves setting the remote locations you will be accessing. Detailed configuration instruction can be found in the [rclone configuration docs](https://rclone.org/docs/) separated by cloud storage systems. This section details configuration instructions for MacOS users accessing Google Drive. 

* In terminal, type in ```rclone config```
  
* Select “n” for “New Remote”
  
* Enter the name for your remote when Rclone prompts you to, try to keep the name as short as possible while still being descriptive and specific. 
  
* rclone will then ask you to select from a list of storage platforms. Enter the number that corresponds on the list to Google Drive (Note: Google Cloud Storage is different from Google Drive!)

* rclone asks for a Google Application Client Id, this is optional and you can select enter to choose default. 
  
* rclone asks for an OAuth Client Secret Id, this is optional and you can enter to select enter to choose default.
    * To set your own application and OAuth client IDs see instructions on [creating a google application client id](https://rclone.org/drive/#making-your-own-client-id) in the rclone docs.
  
* rclone will provide a list of scopes of access ranging from full access to all files to read-only access to file metadata. For our purposes enter the number corresponding to full access to all files. 
  
* Rclone asks for a root folder id, this is optional and you can enter to select enter to choose default.
  
* Rclone asks for service account credentials, this is optional and you can enter to select enter to choose default.
  
* Rclone asks you to edit advanced configuration, select “n” for No. Follow up prompt asks if you would like to use auto configuration, enter “y” for Yes. 
  
* A browser window should then open asking you to log into your google account and allow access to Rclone. Move through the prompts in browser. Once you see the success window, return to the terminal
  
* Rclone asks if you would like to configure this remote as a shared drive. Select Y for yes. This opens a list of the shared drives associated with your account. 
  
* Enter the number associated with the shared drive you will be uploading requested items to. 
  
* Rclone then asks if the configuration you’ve been doing is okay. Enter y for Yes and configuration is complete!

To see all currently configured remotes (rclone term for any cloud storage locations) enter ```rclone listremotes``` into terminal. 

#### Using rclone:


### rsync:

#### Installing: 
#### Configuring: 
#### Using:

### Sha1deep:

#### Installing: 
#### Configuring: 
#### Using:


### Sheepshaver:

#### Installing: 
#### Configuring: 
#### Using:

### Siegfried:

#### Installing: 
#### Configuring: 
#### Using:

### tree:

#### Installing: 
#### Configuring: 
#### Using:

### VLC:

#### Installing: 
#### Configuring: 
#### Using:

### Windows Subsystem for Linux (WSL):

#### Installing: 
#### Configuring: 
#### Using:

### WinUAE:

#### Installing: 
#### Configuring: 
#### Using:

## Working Scripts:

Working Scripts are defined as scripts written internally and maintained by Digital Archives staff for use in our workflows.

### CMS metadata import 
### iterative scripts 
### kryofluxmove.sh 
### makesips script 
### moveimages script 
### report ftk extents script 
### report HDD extents script

## Deprecated and Legacy Scripts:

Deprecated and Legacy Scripts are any scripts which may have been previously used in workflows but are no longer in use, were planned but not completed or replaced by a Working Script.

### ft.sh 
### metadata.sh 
### movemetadata script 
### movephotograph script 
{% endcomment %}
