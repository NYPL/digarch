---
title: Networking
layout: default
nav_order: 4
parent: Tools
has_children: True
---

# Networking
{: .no_toc }


## Networks
### Wireless Network
Computers can connect to the NYPL (public) and NYPL2 (password required) wireless networks. These networks provide the same functionality as they do everywhere else in the NYPL system. If you are only connected to this network, it is not possible to connect to lab computers.

### Wired Network
The wired network is the primary connection for all workstations.

Each desk at LSC 205 is equipped with three RJ-45 telecommunications ports. The red port is used for phones. The middle port is used for 1 Gbps computer networking. The remaining port can be used for computer networking, but must be activated by IT.

The wired network connections are separated into their own subnet by IT. This subnet separates the computers within the lab from all other networked computers at NYPL, protecting both from each other. In order to connect to network resources outside the subnet:
* open a VPN connection
* disconnect from the wired ethernet and connect to the wireless network
* work with IT to create a permanent exception to the subnet

### Fiber Network
The fiber network is primarily used for high-speed connections to the Isilon Storage Cluster. LSC205 has 6 multi-mode 10 Gbps fiber lines and 2 single-mode fiber lines. The multi-mode fiber lines are terminated at a junction box at each row of desks.

Teal fiber cables run through channels under the desks to connected workstations. **As much as possible, do not disturb these cables.** Doing so, may significantly degrade them.

## Connecting to the networks
Workstations should only be connected to one kind of network when possible. Permanent workstations are connected to either the fiber or wired networks. Guest workstations should connect to the wireless network. Before attempting to connect to the fiber or wired network, contact lab staff for permission and equipment.

### Connecting to the fiber network
Connecting to the fiber ports requires a fiber network adapter. The lab has 2 types of adapters, depending on the ports available on the computer to connected.

* 2x Promise SANlink2 SFP+ 10G - using the Thunderbolt 2 protocol over a Mini DisplayPort connector.
* QNAP Thunderbolt3 10GbE - using the Thunderbolt 3 protocol over a USB-C connector

When using these adapters, if it is possible move the computer to the adapter and cable instead of moving adapter and cable. Fiber network cables 

In order to use the adapters:
* Plug in the power adapter and connect it to the adapter. (Promise adapter only)
* Disconnect the computer from any other network connections.
* Plug in the Thunderbolt cable to the adapter and the computer.
* Test the network connection. A tool like [https://fast.com/](https://fast.com/) should report at least a 1Gbps download speed.
	* If the internet is not connecting, the computer may need drivers for the adapter. [Promise drivers](https://www.promise.com/Support/DownloadCenter/sanlink/SANLink2/10G-SFP) [QNAP drivers](https://www.marvell.com/support/downloads.html)
	* If the result of the speed test is under 1 Gbps, the cable may be kinked and require replacement.

### Mounting drives within the subnet
All devices are visible to one another within the subnet. For the IP address, username, and password for a specific device, see this [document](http://secret.example.com).

#### Mounting a drive on a Windows machine
Follow the standard [Windows directions](https://support.microsoft.com/en-us/help/4026635/windows-10-map-a-network-drive). The location of any drive should be formatted as follows:
* `\\`
* `IP address` - see this [document](http://secret.example.com)
* `\path\to\folder\on\device`

For example to mount the `Staging` folder for a device at `192.168.1.101`, the address would be `\\192.168.1.1\Staging`

#### Mounting a drive on a Mac
Follow the [Mac directions](https://support.apple.com/guide/mac-help/connect-mac-shared-computers-servers-mchlp1140/mac) for connecting by entering an address. The location of any drive should be formatted as follows:
* `protocol://` - this may vary depending on the drive, commonly `nfs` or `smb`
* `IP address` - see this [document](http://secret.example.com)
* `/path/to/folder/on/device`

For example to mount the `Staging` folder for a device at `192.168.1.101` using the samba protocol, the address would be `smb://192.168.1.1/Staging`

### Connecting to hosts outside the subnet or through a VPN
To connect to any host outside of the network or to add a connection to a VPN profile, open a ServiceNow ticket with IT. The ticket should contain the following details:
* IP address of the host being connected
* Protocol used for the connection. Examples include `https` (typically the default), `http`,  `smb`, `nfs`, `vnc`, and `rdp`
* Specific ports and whether they are used for `TCP`, `UDP`, or both.
* IP address(es) of the computers connecting to the host. If the entire subnet needs access, `/24` address listed in this [document](http://secret.example.com)
