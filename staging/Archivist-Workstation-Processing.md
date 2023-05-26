---
title: Archivist Workstation Processing Instructions
layout: default
nav_order: 7
has_children: false
parent: Processing
---

# Archivist Workstation Processing Instructions
{: .no_toc }
&nbsp;
{: .no_toc .text-delta }
1. TOC
{:toc}

Archivists processing electronic records without using FTK or ePADD will receive an external hard drive or thumb drive with copies of files to be arranged.  

## Using an External Hard Drive

* Attach the external hard drive or thumb drive to your workstation.  

<!--*Will need to add new language around SPEC updates*-->
* Open SPEC and navigate to the object inventory of the associated collection for information on the digital carriers being processed.

* Note you may also need to update fields in individual SPEC object records at various points during processing.  

## Arranging and Describing Files from a Workstation

The goal of the arrangement and description phase is to approximate the
process in which an archivist works with a physical collection. By using
their workstation the archivist will be able to appraise records as they are contained
on their original media, create a set of intellectual components
(arrangement), summarize the logical extents (size) and date ranges of
the components, and enter them into ArchivesSpace.

### Navigating the Drive

* Double-click the drive icon to display the drive folders in Windows Explorer.
* The folders will have the following structure:  
    * \M12345_workingfiles
		* \M12345-0001
			* \metadata
			* \objects 
        
* Note the metadata folder may contain metadata created during the transfer of the files.  
* Note a file directory listing of the files in .csv format, if present.
* Navigate to the objects folder to view the files to be arranged.  
* Navigate to the data folder in the objects folder to view the files to be arranged.
<!--* Note manifest.txt files contain a directory listing. --> 

### Processing  

* Appraise the files.  
* Ascertain the arrangement of the files.
* Note file naming conventions, how the files relate to each other, and  possible duplicates.

### Arrangement  

* Create a new folder on the drive you received at the same folder level as \M12345_workingfiles.  
* Use the naming convention ```CollectionID_FAcomponents``` to create a collection folder.  
* Name the folder /M12345_FAcomponents, for example.  
* Create a folder for each FA Component using ```CollectionID_ER_1```, ```CollectionID_ER_2```.  
* Create an objects folder within each ER_# folder. ```CollectionID_ER_1\objects```
* Move the files into the new FA Component objects folders as your process the files.
* Calculate the size of each FA Component by right clicking on the FA Component folder.
* Select Properties from the drop down menu.  
* Note the file count and byte extent, when you are done processing.  

### Entering your collection in ArchivesSpace
After arrangement is complete Processing Archivists notify Digital Archives and deliver the external hard drive containing FA Components to Digital Archives for review.  Digital Archives staff then create a JSON file containing extents for import into ASpace. For detailed instruction on importing the extents JSON to ASpace review the [Importing FTK ERs in ArchiveSpace](https://docs.google.com/document/d/1BVMaDOzdcPFIht5yN5V16zmsnjMTwG_3e73HPTdVzSg/edit) guide.

* Note in some situations ERs may have to be manually created in ASpace instead of imported. Contact the Manager of Archival Metadata when deciding whether manual creation or JSON import is pertinent to your processing.
