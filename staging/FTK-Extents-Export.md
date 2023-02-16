---
title: FTK Extents Export
layout: default
nav_order: 8
has_children: false
parent: Processing
---
# Exporting Extents from FTK

{: .no_toc }
&nbsp;
{: .no_toc .text*delta }

When Digital Archives staff have completed review of the bookmarks created by a Processing Archivist, the extents of the collection are exported from FTK and delivered to Archival Processing Unit as a json file for import into ArchivesSpace. This page describes instructions for preparing and exporting extents JSON files using the [report-ftk-extents script](). <!-- will need to add this to the software page -->

## Export XML Report from FTK

FTK does not generate reports in the the JSON file format, however it does generate XML.

* Prepare a destination directory
  * Navigate to the FTKsettings directory in the Storage (F:) drive on FRED 2.
  * Open the extents_reports directory
  * Create a destination directory for the XML report using the naming convention 'CollectionIDreport'.
    * As an example the XML report destination directory for the Morris Dickstein Collection is named M18867report

* Export XML report
  * Open collection to be exported in FTK.
  * Navigate to Bookmarks tab.
  * Navigate to the "File" menu
  * Select Report
  * Select the checkbox for "Bookmarks" in the "Report Options" dialog box. (Bookmarks is the only option that needs to be checked.
  * Click on the "Bookmarks" option to open the bookmarks hierarchy. Make sure that "Shared" and all subsequent bookmarks are actually checked by expanding the Bookmarks hierarchy.
  * Select "OK" after verifying that all bookmarks have been checked.
  * Select the report destination folder you created earlier by selecting the elipses "..." and navigating to the destinaton folder or entering the destination path.
  * Select the checkbox for "XML" in the "Report Output" dialog box
  * Select "OK" in the "Report Output" dialog box.
  * After export is complete, return to the collection report destination folder to verify report export took place. The destination folder.
    * The report destination directory will now contain a folder called "Report_Files" and two files: "Report.fo" and "Report.xml".

## Transform XML Report to JSON using report-ftk-extents

## Deliver extents JSON to Archival Processing Unit

Digital archives staff should deliver the extents JSON file to the Processing Archvist(s) for the associated collection. The Manager of Archival Metadata should be included in any correspondence for assistance with and troublshooting for JSON import into ArchivesSpace.