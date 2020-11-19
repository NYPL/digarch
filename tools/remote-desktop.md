---
title: Remote Desktop
layout: default
nav_order: 3
parent: Networking
grand_parent: Tools
has_children: false
---

# Remote Desktop Support

Lab computers can be accessed remotely for use during work-from-home, remote support, or emergency response. The software used to connect remotely depends on the lab computer being accessed. This document describes how to configure a computer for remote access and how to access it.

The software used for remote desktop access depends on the computer being access and the features needed during access.

* Windows
	* Remote Desktop for full access to computer including file transfers
	* Chrome Remote Desktop for providing remote support while another user is logged on
* Mac
	* RealVNC for all functions

## Setting up Remote Desktop

### Microsoft Remote Desktop

#### Host setup
* To enable Remote Desktop:
	* Open the Settings program.
	* Select Remote Desktop.
	* Select Enable.
* To make the computer's IP address static:
	* Open the Settings program.
	* Select Network & Internet.
	* Select Change Connection Properties.
	* Scroll down to current settings and copy the IPv4 address and DNS servers.
	* Click Edit under IP Settings.
	* Set the IP address to manual, toggle the IPv4 setting, and complete the fields as follows:
		* IP address: paste the current address
		* Subnet: 24
		* Gateway: paste the current address and change the last number to 1 (e.g. for an IP 192.168.1.255, gateway would be 192.168.1.1)
		* DNS: paste the DNS servers
	* Click save and close all windows.

Open a ServiceNow Ticket with the following details:
* Static IP address of the lab computer
* Protocol: RDP
* Ports: 3389 (UDP and TCP)
* Which clients should be allowed to connect to computer (VPN accounts and/or IP ranges of the NYPL network)

#### Client Setup
* Install Microsoft Remote Desktop.
* Under Connections, select Add PC.
* Enter the static IP address of the host computer.
* Give the connection a name
* Click add.

### Chrome Remote Desktop

#### Host setup
* Install Chrome Remote Desktop using Chrome borwser.
* Login with your NYPL account.
* Follow the setup instructions by entering a name for the computer and choosing a PIN to protect access.

#### Client Setup
* Install Chrome Remote Desktop using Chrome browser.
* Login with your NYPL account.

### VNC

On the lab computer:
* Install VNC Server
	* During setup, enter credentials for the Digital Archives account.
	* Create a name and password for the computer,
* To make the computers IP static:
	* Open Preferences.
	* Select Network.
	* Select the network connection from the list on the left.
	* Copy the current IP Address.
	* Change "Configure IPv4" to "Using DHCP with manual address".
	* Paste the IP address into the field.
	* Click apply and close all windows.

Open a ServiceNow Ticket with the following details:
* Static IP address of the lab computer
* Protocol: VNC
* Ports: 5800 and 5900 (TCP)
* Which clients should be allowed to connect to computer (VPN accounts and/or IP ranges of the NYPL network)

#### Client Setup
* Install VNC Viewer.
* During setup, enter credentials for the Digital Archives account.

## Connecting to Remote Desktop

### Microsoft Remote Desktop
CAUTION: starting a Remote Desktop session will immediately force anyone currently using the computer to log off.

* Connect to VPN
* Open Microsoft Remote Desktop
* Double-click the computer you'd like to access
* Enter the username and password to login to the computer

### Chrome Remote Desktop
If you are connecting to use the computer yourself, you must have completed the Host setup with your own NYPL account:
* Open Chrome Remote Desktop.
* Select the computer you want to access and enter your PIN code.

If you are connecting to support someone currently using the computer.
* Open Chrome Remote Desktop.
* Open the Remote Support tab.
* Enter the Access code that they provided.

### RealVNC
* Connect to VPN.
* Open VNC Viewer.
* Double-click the computer you'd like to access.
* Enter the password to login to the computer.

## Issues with Remote Desktop

### Everything is too small
Your view of host computer's desktop is scaled according both to the size of the window you are using and to the relative resolutions of your monitor and the host monitor. For example, the interface of a computer that uses a 27" monitor may be shrunk to a quarter its size on a laptop with a 13" screen.

To temporarily address this issue, change the scale of the interface.

* Maximize the size of the remote desktop window on your computer.
* Then scale the rendering of the interface on the host computer.
	* Windows PC
		* Open Settings
		* Select Display
		* Under Scale and Layout, increase the percentage until the interface is more comfortable.
	* Mac
		* Open Preferences
		* Select Displays
		* Choose Scaled display and adjust the slider until the interface is more comfortable.

### The interface is choppy/laggy/skipping/etc

Remote desktop depends on:
* the bandwidth of the connection between you and the host computer
* the ability of the host computer to encode its desktop as video and export it
* the ability of your computer to render the video

If you are encountering issues:
* Improve the stability of your connection either by:
	* stopping any other bandwidth intensive processes like file uploads or streaming media
	* connecting to a different wireless network or use a wired connection
* Decrease the encoding load on the host computer by:
	* minimizing or closing any windows with very dynamic content like videos
	* reducing the total number of processes running on the computer
* Decreasing the rendering load on your computer by:
	* reducing the total number of processes running

