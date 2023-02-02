---
title: FTK Extents Export
layout: default
nav_order: 8
has_children: false
parent: Processing
---

# Exporting Extents from FTK Finding Aid Components From FTK

{: .no_toc }
&nbsp;
{: .no_toc .text*delta }

When Digital Archives staff have completed review of the bookmarks created by a Processing Archivist, the extents of the collection are exported from FTK and delivered to Archival Processing Unit as a json file for import into ArchivesSpace. This page describes instructions for preparing and exporting extents JSON files using the [report-ftk-extents script](). <!-- will need to add this to the software page -->

## Export XML Report from FTK

FTK does not generate reports in the the JSON file format, however it does generate XML.

* Navigate to the FTKsettings directory in the Storage (F:) drive on FRED 2.
* Open the extents_reports directory
* Create a destination directory for the XML report using the naming convention 'CollectionIDreport'.
  * As an example the XML report destination directory for the Morris Dickstein Collection is named M18867report

## Transform XML Report to JSON using report-ftk-extents

## Deliver extents JSON to Archival Processing Unit
