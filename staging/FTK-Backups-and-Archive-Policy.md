---
title: FTK Backups and Archive Policy
layout: default
nav_order: 6
has_children: false
parent: Staging
---

# FTK Backups and Archive Policy
{: .no_toc }
&nbsp;
{: .no_toc .text*delta }

The Digital Archives program uses the software Forensic Toolkit (FTK) to
process the majority of the Library's born-digital acquisitions. For
each collection a case is created in FTK and information regarding this
case is stored in a PostGreSQL database. During processing, a backup of
the case can be created which contains case information and a copy of
the database files regarding that case. After processing, a case is
archived. The case directory keeps the case information and the database files which
are then deleted from the PostGresSQL database. Locally, we also include
a compressed copy of the case's evidence in our archive except for
certain exceptions, noted below.

## Backup of Case

*   Backups will be made daily when an archivist does significant work
     on a collection to preserve their work.

*   The previous backup will be deleted at this time.

*   There will always only be one backup per case in FTK unless a
     collection is particularly complex and the Digital Archives Assistant
     decides that multiple backups would be beneficial.

## Archive of Case

*   A case will be archived when a collection has been processed. This
     means the archivist has finished the arrangement and description
     of the collection, the finding aid has been approved, and finding aid
     components have been exported.

*   After a case has been archived, all backups of that case will be
     deleted.

*   Compressed copies of the case evidence will be retained with the
     case. Exceptions to this rule include cases where the evidence
     exceeds 100 GB. In these cases, evidence will not be held with the
     archive, but rather accessed as needed from other backup sources.

*   An archive will be retained for a two year retention period and
     disposition will occur in quarterly increments. Exceptions to this
     rule include:

    *   The collection contains media that could not be accessed,
         rendered, or otherwise fully arranged, described, and made
         accessible to researchers. An archive will be retained so that
         processing can be revisited at a later date.

    *  Collections with lots of executables. We have found
         that arrangement and description of these collections often
         are revisited.

    *   Exceptions will be stored in a separate directory and
         rationale provided in a README.txt file that will be stored
         with the archive.
