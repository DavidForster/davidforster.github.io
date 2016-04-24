---
layout: "post"
title: "Installing OpenWRT on the Linksys WRT1900ACS Wireless Router"
date: "2016-04-24 13:55"
category: openwrt
permalink: /openwrt/installing-openwrt-linksys-wrt1900acs/
excerpt: In this post I will detail the steps that I took to flash a brand new Linksys WRT1900ACS wireless router with the latest OpenWRT firmware.
---

Following a nasty issue with Virgin Media's Super Hub 2 whereby, for the last few months, one of the wireless networks would go down every four to five hours I decided to quit trying to convince Virgin Media that they had a problem and switch it over to modem mode with my trusty old D-Link DIR-615 running DD-WRT acting as a router instead. After a couple of weeks of continuous uptime with no further issues, I decided that I should invest in a more capable router. The little 615 is great, but it only supports up to 802.11n in the 2.4GHz spectrum and I have many devices that are capable of achieving much faster speeds and utilising my 200MBps broadband connection.

After copious Googling I concluded that the Linksys WRT1900ACS was the choice for me. This looked like a powerful router that supported the latest wireless standards and also satisfied my inner geek with a design that harked back to the good old days of the insanely popular WRT54G. I did notice a few gripes regarding the stability of Linksys' firmware, but this didn't trouble me as I intended to take full advantage of Linksys' stated support for the open source firmware OpenWRT. As long as the out-of-the-box firmware would let me log in and flash it with OpenWRT that's all that mattered.

So, here are the steps I followed to get my router up and running with OpenWRT...

1. Obtain the correct firmware

    According to the [hardware page](https://wiki.openwrt.org/toh/linksys/wrt1900acs) this router is codenamed "Shelby" and uses a Marvell Armada 385 SoC, meaning that you need to download the [`openwrt-mvebu-armada-385-linksys-shelby-squashfs-factory.img`](https://downloads.openwrt.org/snapshots/trunk/mvebu/generic/openwrt-mvebu-armada-385-linksys-shelby-squashfs-factory.img) firmware image from [https://downloads.openwrt.org/snapshots/trunk/mvebu/generic/](https://downloads.openwrt.org/snapshots/trunk/mvebu/generic/).

2. Connect to the router

    Power up the router and connect to it via cable. This is a more reliable connection for transmitting something as important as a firmware image and you may well need a cable connection to access it after rebooting. Access the Linksys admin interface at [http://192.168.1.1](http://192.168.1.1).

    It may also be worth verifying that you can connect out to the internet at this point, as my Virgin Media Super Hub decided that it didn't like me disconnecting one router and connecting another and it needed to be turned off and on again before it would allow any outbound communication from the new device. This caused me a stupid amount of wasted time trying to figure out what had happened after I flashed the firmware and discovered that I couldn't talk to the outside world or install any packages!

3. Flash firmware & reboot

    Login to the Linksys admin interface (default password should be `admin`), navigate to the **Connectivity** section and locate the **Router Firmware Update** section on the right hand side. Click on the Choose File button in the Manual section, select the firmware image that you downloaded from OpenWRT earlier and then hit Start.

    You may get a warning about an unrecognised file name. That's ok, it's just that the OpenWRT download ends in a different file extension (.img) to what the Linksys firmware expects. Just click on Yes to continue and also click on Yes and OK to any subsequent warnings about firmware updates and reboots.

    Once the new firmware is uploaded your router will reboot and will be running OpenWRT! Any devices connected to it should be able to access the internet.

4. SSH to router and set a root password

    The first thing we should do is set a root password... Our router is not very secure without one! Connect to the router with `ssh root@192.168.1.1`. Then set a [strong password](https://open.buffer.com/creating-a-secure-password/) for the root user by running the passwd command.

6. Fix the 2.4GHz network

    With my particular install, I found that the 2.4GHz network didn't start up. This was easily fixed by changing the hwmode from 11a to 11g (i.e. changing the band from 5GHz to 2.4GHz) of the corresponding wifi-device in the wireless configuration file. Running `uci set wireless.radio1.hwmode=’11g' && uci commit wireless`, followed by `wifi down && sleep 2 && wifi up` brought my 2.4GHz network up.

7. Install LuCI

    As mentioned on the hardware page, some builds do not include the LuCI web GUI and this was the case for me. This was easily rectified by running `opkg update` followed by `opkg install luci`. After that I could access LuCI by browsing to [http://192.168.1.1](http://192.168.1.1) from my machine. Use the same root password as you set in step 4 to log in.

8. Maximise wireless settings

    Following the advice in [tdcat's video](http://tdcat.com/2015/10/openwrt-wireless-settings/) I set the htmode for my wifi-devices to VHT80 for radio0 (5GHz) and HT40 for radio1 (2.4GHz). Now that you have LuCI installed you can probably do this through the web GUI, but I opted to change the wireless configuration file manually via SSH and vim.
