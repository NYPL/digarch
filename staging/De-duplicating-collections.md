---
title: De-duplicating Collections
layout: default
nav_order: 7
has_children: false
parent: FTK Processing Instructions
grand_parent: Processing
---
# De-duplicating Collections
Using a filter to hide duplicate files is an optional method of managing the amount of files surveyed.

## Running a De-duplication Job

* Select Additional Analysis from
the Evidence menu. 

* Select Flag Duplicate Files from the File Hashes group and click OK.

![](dapi/media/image12.png)

* This will start a comparison of the checksums of all files in the
collection.

![](dapi/media/image7.png)

* When complete close the Data Processing window.

## Adding a Duplicate File Column Set to a FTK Case

* Click the column
settings![](dapi/media/image8.png) button from the File List window.  
* Click the import button and navigate to Storage(F:)\\FTKsettings\\ColumnDefs\\Duplicates.xml  
* Click OK and close the column settings window.

* Select Duplicates from the column dropdown.

![](dapi/media/image9.png)

## Reading the Duplicate File Field
* Note the Duplicate File field in the File List.  
* Note the number in the Duplicate File field.  

![](dapi/media/image3.png)

* If the Duplicate File field is blank the file has not been analyzed
for duplication.

* 1 indicates the file is duplicated but it is the first instance of that file hashed in the case.  
* 2 indicates the file is a duplicated and not the first instance of that file hashed in the case.  
* 3 indicates the file is unique and does not have a duplicate in the collection.  

## Adding a Duplicate Filter

* Click the import filter button from the Filter Manager
![](dapi/media/image5.png)  
* Navigate to Storage(F:)\\FTKsettings\\FilterDefs\\DuplicateSecondary.xml  
* Click open and OK to import it into the case.  
* Use the filter to either include or exclude secondary
duplicates from the File List.  

Example: File list **excluding** secondary duplicates.
![](dapi/media/image15.png)

Example: File list **including** only secondary data sets.
![](dapi/media/image13.png)