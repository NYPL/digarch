---
title: Rclone
layout: default
nav_order: 8
parent: Software
grand_parent: Tools
has_children: False
---

# Rclone:
[*Rclone*](https://rclone.org/) is a command line tool for managing files on cloud storage, and is one tool used by Digital Archives for moving files between Digital Archives workstations, Google Shared Drives for Divisions, and long term storage. This page lists instructions for installing and configuring rclone. 

## Installing Rclone:
For detailed installation instruction tailored to your operating system see the [rclone documentation](https://rclone.org/install/).

For MacOS:
Use Homebrew to install rclone via the terminal by entering:
```
brew install rclone
``` 

For Windows:
[Download and run Windows installation file.](https://rclone.org/downloads/)

## Configuring Rclone:
Once installed, you must configure Rclone which involves setting the remote locations you will be accessing. Detailed configuration instruction can be found in the [rclone configuration docs](https://rclone.org/docs/) separated by cloud storage systems. This section details configuration instructions for MacOS users accessing Google Drive. 

- In terminal, type in ```rclone config```
  
- Select “n” for “New Remote”
  
- Enter the name for your remote when Rclone prompts you to, try to keep the name as short as possible while still being descriptive and specific. 
  
- rclone will then ask you to select from a list of storage platforms. Enter the number that corresponds on the list to Google Drive (Note: Google Cloud Storage is different from Google Drive!)
- rclone asks for a Google Application Client Id, this is optional and you can select enter to choose default. 
  
- rclone asks for an OAuth Client Secret Id, this is optional and you can enter to select enter to choose default.
    - To set your own application and OAuth client IDs see instructions on [creating a google application client id](https://rclone.org/drive/#making-your-own-client-id) in the rclone docs.
  
- rclone will provide a list of scopes of access ranging from full access to all files to read-only access to file metadata. For our purposes enter the number corresponding to full access to all files. 
  
- Rclone asks for a root folder id, this is optional and you can select enter to choose default.
  
- Rclone asks for service account credentials, this is optional and you can select enter to choose default.
  
- Rclone asks you to edit advanced configuration, select “n” for No. Follow up prompt asks if you would like to use auto configuration, enter “y” for Yes. 
  
- A browser window should then open asking you to log into your google account and allow access to Rclone. Move through the prompts in browser. Once you see the success window, return to the terminal
  
- Rclone asks if you would like to configure this remote as a shared drive. Select Y for yes. This opens a list of the shared drives associated with your account. 
  
- Enter the number associated with the shared drive you will be uploading requested items to. 
  
- Rclone then asks if the configuration you’ve been doing is okay. Enter y for Yes and configuration is complete!

To see all currently configured remotes (rclone term for any cloud storage locations) enter ```rclone listremotes``` into terminal. 

## Using Rclone with Google Drive:
When using rclone with google drive accessing files in "My Drive" and Shared Drives" differs from accessing any files in "Shared with me". To access the "Shared with me" subdirectory:

* Create an rclone remote location for the drive the collection has been shared with. 

* Use the following syntax for accessing anything in the the “Shared With Me” subdirectory:

```rclone copyto remote:shared/with/me/remote/directory —name-of-drive-shared-with-me /path/to/destination```

