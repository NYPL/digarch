---
title: Transfers
layout: default
nav_order: 3
has_children: true
---

## Transfers
{: .no_toc }

1. TOC
{:toc}

Born digital collection material can be acquired through file transfer or forensic imaging.
The workflows vary based on media types and file types encountered but the general steps are as follows:

1. Verify that all carriers from the collection are present and recored in SPEC
2. Select an appropriate transfer method for each type of carrier found
3. [Transfer the files from the media](#choosing-a-transfer-method)
4. Collect any additional metadata from the media
5. Package the files
6. [Store the packages with backups]


### Choosing a Transfer Method

Processing archivists may help determine the most appropriate transfer process.

* If the files are only available via a cloud service:
  * [Cloud File Transfer](cloud-file-transfer.html)
* If the files are on mass storage devices and not all files are desired:
  * [File Transfer](files-transfer.html) for hard drives, usb drives, and other mass storage devices
  * [Mass Optical Transfers](nimbie-transfers.html) for optical media
* If the files must be retained in as they were on their original media:
  * [Floppy disk imaging](floppy-disk-imaging.html)
  * [Optical media imaging](optical-media-imaging.html)
  * [Iomega disk imaging](iomega-disk-imaging.html)
* If the lab does not have the required hardware:
  * Vendor transfers

If the preferred method is unsuccessful, adapting other processes may be necessary.

### Storage

During transfer work, the files generated from each carrier are stored on the local RAID.
They are organized as child folders within a parent folder for the entire acquisition.


In Development
{: .label .label-yellow }

Once all transfer work is complete for the acquisition:

1. Copy the entire acquisition folder to network storage.
```rsync -arP /path/to/ACQ_ID /path/to/network/storage```
2. Validate the results of the transfer.
```lint_ft -d /path/to/network/storage/ACQ_ID```
3. Notify Digital Repository staff that packages are ready.
4. Digital Repository staff ingest packages into Preservica
5. Digital Repository staff notify the packages have been ingested.

After 6 months, if the collection is not on a processing queue:

1. Confirm a good copy on network storage and in Preservica.
2. Delete from the local RAID
```rm /path/to/ACQ_ID```
