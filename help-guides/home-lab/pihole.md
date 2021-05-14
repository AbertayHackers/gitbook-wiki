---
description: How to set up a PiHole
---

# PiHole

_An install guide by Kyle_

Using a Raspberry Pi as the networks DNS server, [Pi-Hole](https://pi-hole.net/) “blocks ads for all your devices without the need to install client-side software. The Pi-hole blocks ads at the DNS-level, so all your devices are protected.”[1\)](https://wiki.hacksoc.co.uk/guides/pihole#fn__1) This also allows ad blocking on devices which do not support it \(think mobile/tablet\)

### Install Guide <a id="install_guide"></a>

This guide has been tested using Raspbian Jessie, macOS Sierra 10.12.3 & PiFiller 1.3 and works.

#### Requirements <a id="requirements"></a>

* MicroSD card \(min 4GB\)
* MicroSD card reader to USB depending on your computer
* A way to burn images onto SD card - I choose [PiFiller for macOS](http://ivanx.com/raspberrypi/)
* Raspberry Pi with a power cable, monitor \(just for install set up, can be run headless later\), keyboard for initial input, - Ethernet cable to connect the RPi to the router, Wi-Fi adapter for RPi
* [Raspbian Jessie image](https://www.raspberrypi.org/downloads/raspbian/)
* Access to administration panel on the router \(this information is typically next to the SSID on the bottom of the router\)

#### Initial things <a id="initial_things"></a>

1. Download latest [Raspbian Jessie image](https://www.raspberrypi.org/downloads/raspbian/)
2. Burn this image to the SD card using [PiFiller for macOS](http://ivanx.com/raspberrypi/). You can optionally use dd or another method to burn it. PiFiller is the fastest and easiest way I have found to do it.
3. Attach Raspberry Pi to monitor & keyboard, connect via Ethernet to the router and insert the SD
4. Then power on. _If its done in a different order it can fall over_.

#### Configuring the Raspberry Pi <a id="configuring_the_raspberry_pi"></a>

1. Check you are connected to the internet \(ping 8.8.8.8 is easy way to check, this is Google’s DNS server so if thats down today will be a bad day\)
2. Update the Pi using `sudo apt-get update -y`
3. _Optional: install a different text editor, nano is installed by default. `sudo apt-get install vim -y`_
4. Configure a static IP address to allow headless use of the Pi
5. run route -ne and note the default gateway IP address \(routers IP address\)
6. Now we need to edit the dhcpcd.conf file using `sudo vim /etc/dhcpcd.conf`
7. The following information needs to be added to the bottom of the file:
8. ```text
   interface eth0 (interface ethernet)
   static ip_address=192.168.0.88       # the ip to give the Pi
   static routers=192.168.0.1           # the gateway/routers IP
   ```
9. `sudo reboot` will allow all changes to take effect
10. To check it has worked run `ifconfig` and eth0 should be assigned 192.168.0.88 \(or whatever you chose\)
11. Enabling SSH: this is on by default on the Raspberry Pi - if it is not working run `sudo raspi-config` and enable it in the advanced &gt; ssh menu.
12. Generate SSH-Keys to allow passwordless entry - this is an easy to follow [guide](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
13. Optional: create a bash alias in `.bash_profile` to allow easy entry. I added `alias pihole='ssh pi@192.168.0.88`' so logging into PiHole is as easy as just typing it into terminal.

#### Installing & Testing <a id="installing_testing"></a>

[Install guide](https://github.com/pi-hole/pi-hole/#one-step-automated-install) on their GitHub is best

* Run sudo curl -sSL [https://install.pi-hole.net](https://install.pi-hole.net/) \| bash
* The Web interface will be installed automatically so you can view stats and change settings. You can find it at: [`http://192.168.1.x/admin/index.php`](http://192.168.1.x/admin/index.php) or [`http://pi.hole/admin`](http://pi.hole/admin)
* The install covers it all, its very easy to do, remember and note the admin password produced.

#### Misc <a id="misc"></a>

The default credentials for the Raspberry Pi is username: `pi` & password: `raspberry`

### Deploying on Devices <a id="deploying_on_devices"></a>

You cannot edit the DNS servers on the Virgin HomeHub and after searching around it also seems to be the same for Sky, BT and other broadband providers. DNS servers must be modified on devices on the network.

* **iOS**
  * `Settings > Wi-Fi > “Networking Name” > DNS` \(192.168.0.88 in this example\)
* **Android**
  * `Settings > Long press on the Network Name > Manage Network Settings > Show Advanced Options > DNS 1`
* **macOS**
  * `System Preferences > Network > Advanced > DNS Tab > +DNS Server`
* **Windows 10**
  * . `Network and Sharing Centre > Click on the connection type > Properties > Internet Protocol Version 4 (TCP/IPv4) > Properties > Select “Use the following DNS server addresses”` and add in the IP address of the Pi

[1\)](https://wiki.hacksoc.co.uk/guides/pihole#fnt__1) Quoted from their [GitHub](https://github.com/pi-hole/pi-hole)

