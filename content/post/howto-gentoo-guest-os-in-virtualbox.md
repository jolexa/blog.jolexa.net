---
author: Jeremy Olexa
categories:
- gentoo
date: 2008-07-10T00:00:00Z
guid: http://jolexa.wordpress.com/?p=11
id: 11
tags:
- howto
- virtualbox
- virtualization
title: 'Howto: Gentoo Guest OS in VirtualBox.'
aliases:
    - /2008/07/howto-gentoo-guest-os-in-virtualbox/
---

I spent a few tries on this as I have never used <a href="http://virtualbox.org/" target="_blank">VirtualBox</a> before. I think this may be randomly documented on the web but I am putting this here for archive purposes (myself) and in case other stumble upon this.

Step 1:  
Create a VM in Virtual box and set the type as Gentoo Linux. I think anyone can handle this because there is a pretty nice wizard that helps you out. Some notables: Base Memory: 512, Boot hardisk: 20 gigs (8 is plenty for a minimal install and not much else).  
Fire it up and it will ask for a boot disk. An .iso on the hard drive works fine. I choose to try out the new <a href="http://www.gentoo.org/" target="_blank">Gentoo Linux 2008.0 Minimal Install CD</a>.

Step 2:  
If you have never installed Gentoo before. Please follow the detailed install <a href="http://www.gentoo.org/doc/en/handbook/index.xml" target="_blank">handbook</a>. If you have installed Gentoo before, this is no different than any other Gentoo install, take your time and read the instructions!

Step 2a:  
When you get to the compilation of your kernel step. You may have good luck with these notes:  
`<br />
1. Processor type and features`

* Processor family->  
* Enable Tickless System (Dynamic Ticks)  
* Remove High Resolution Timer Support  
* Remove Symmetric multi-processing support  
* Subarchitecture Type->PC-compatible  
* Remove Machine Check Exception  
* Remove 64 bit Memory and IO resources  
* High Memory Support (off)

2. Power Management Options

* Remove Suspend to RAM and standby  
* Remove Hibernation  
* Enable ACPI Support

3. Device Drivers

* Remove Macintosh device drivers  
* Remove Virtualization

4. Device Drivers -> ATA/ATAPI/MFM/RLL support

* enable Generic PCI bus-master DMA support -> Intel PIIXn chipsets support  
* enable PCI IDE chipset support

5. Device Drivers -> Serial ATA and Parallel ATA drivers

* enable Intel ESB, ICH, PIIX3, PIIX4 PATA/SATA support

6. Device Drivers -> Network device support

* Remove Ethernet (1000 Mbit)  
* Remove Ethernet (10000 Mbit)

7. Device Drivers -> Ethernet device support -> Ethernet (10 or 100Mbit)

* Remove 3COM cards  
* Remove “Tulip” family network device support  
* Remove Broadcom 4400 ethernet support  
* Remove nForce Ethernet support  
* Remove Intel(R) PRO/100+ support  
* Remove RealTek RTL-8139 C+ PCI Fast Ethernet Adapter Support  
* Remove RealTek RTL-8129/8130/8139 PCI Fast Ethernet Adapter Support  
* Enable AMD PCnet32 PCI support

8. Device Drivers -> Graphics support

* Remove Lowlevel video output switch controls  
* Enable Support for frame buffer devices  
* Enable Support for frame buffer devices -> VESA VGA graphics support

Step 3:  
Continue with the install and when you get to the reboot step you should also unmount the boot cd from virtualbox.

Step 4:  
Fire up your new VM and start configuring it how you like it. It should seem like a brand new Gentoo install which is pretty bare bones in itself. I would recommend picking a WM to install like GNOME, KDE, or <a href="http://www.gentoo.org/doc/en/xfce-config.xml" target="_blank">Xfce4</a>

Step 5:  
Have fun. You may be interested in the &#8216;snapshot' feature of virtualbox. I also hit &#8220;Save State' when I close my VM. I guess you could analogue that to hibernating or &#8216;pausing' as it literally comes back to where you were when you fire it up again.