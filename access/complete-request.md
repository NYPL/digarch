---
title: Completing a Digital Item Request
layout: default
nav_order: 1
parent: Access Services
---

# Completing a Digital Item Request
This page describes steps for Digital Archives staff completing digital item requests once a request has been received. 

### Item Request is received and assigned:
* Once [a requester creates and submits a service now ticket](making-request.html), add a Trello card to the **Received** list on the [Digital Item Requests Tracker](https://trello.com/b/BvWkrdpE/digital-item-requests). 
  * Name the Trello card is using the Collection Title and Service Now Ticket number. 
      
* Once Digital Archives staff members are assigned a request, move the request Trello card to **Assigned** list on the [Digital Item Requests Tracker](https://trello.com/b/BvWkrdpE/digital-item-requests). 

### Locate associated media id(s) and objects(s)
* Using information like collection name, class-mark, and description from the request (and moving between SPEC and CMS); identify the collection number (the id beginning with M*) associated with the requested item(s). 
  * You may also utilize inscriptions on the associated media carrier(s) for the requested items. 

* Once the collection number has been identified, search the collection for the media carrier(s) that may hold the requested item.      
  * The relationship between M* number and requested item(s) is not always one-to-one as requested items may have come from a range of media carriers.  For instance, a requested set of images from a performance may have been received as several CD-R disks. 
  * Any inscription on the associated media carrier(s), or recorded in the CMS record of associated media carrier(s) may also be helpful in finding requested items.  

### Prepare Items for Sharing 
* Create a folder for requested items. 
  * Folder should be named with the service now ticket number of request. 
  
* On Digital Archives workstation navigate to the associated collection folder. 
  
* Navigate to the /objects folder. 
  
* Copy items from /objects folder to the folder you created and named with the service now ticket number.  

### Uploading requested images to Google Drive:
* Once the requested item(s) have been located and prepared, upload the item folder to the Collection Share google drive folder named for the curatorial division of the requester. Instructions for uploading item folders to google drive using rclone are listed below. 

#### Using rclone: 
[*Rclone*](https://rclone.org/) is a command line tool for managing files on cloud storage, and is one tool  used by Digital Archives for moving files between Digital Archives workstations, Google Shared Drives for Divisions, and long term storage . 

##### Installing Rclone:

For MacOS:
Use Homebrew to install rclone via the terminal by entering:
```
brew install rclone
``` 

##### Configuring Rclone:
Once installed, you must configure Rclone which involves setting the remote locations you will be accessing. Detailed configuration instruction can be found in the [rclone configuration docs](https://rclone.org/docs/) separated by cloud storage systems. This section details configuration instructions for MacOS users accessing Google Drive. 

- In terminal, type in ```rclone config```
  
- Select “n” for “New Remote”
  
- Enter the name for your remote when Rclone prompts you to, try to keep the name as short as possible while still being descriptive and specific. 
  
- rclone will then ask you to select from a list of storage platforms. Enter the number that corresponds on the list to Google Drive (Note: Google Cloud Storage is different from Google Drive!)
- rclone asks for a Google Application Client Id, this is optional and you can select enter to choose default. 
  
- rclone asks for an OAuth Client Secret Id, this is optional and you can enter to select enter to choose default.
    - To set your own application and OAuth client IDs see instructions on [creating a google application client id](https://rclone.org/drive/#making-your-own-client-id) in the rclone docs.
  
- rclone will provide a list of scopes of access ranging from full access to all files to read-only access to file metadata. For our purposes enter the number corresponding to full access to all files. 
  
- Rclone asks for a root folder id, this is optional and you can enter to select enter to choose default.
  
- Rclone asks for service account credentials, this is optional and you can enter to select enter to choose default.
  
- Rclone asks you to edit advanced configuration, select “n” for No. Follow up prompt asks if you would like to use auto configuration, enter “y” for Yes. 
  
- A browser window should then open asking you to log into your google account and allow access to Rclone. Move through the prompts in browser. Once you see the success window, return to the terminal
  
- Rclone asks if you would like to configure this remote as a shared drive. Select Y for yes. This opens a list of the shared drives associated with your account. 
  
- Enter the number associated with the shared drive you will be uploading requested items to. 
  
- Rclone then asks if the configuration you’ve been doing is okay. Enter y for Yes and configuration is complete!

To see all currently configured remotes (rclone term for any cloud storage locations) enter ```rclone listremotes``` into terminal. 

### Completing Image Request
* Share google drive folder with initial item requester and notify them via email that items have been shared. 

* On Trello, move the request card to the **Awaiting Deletion** list.
  
* Delete Images from Google Drive.