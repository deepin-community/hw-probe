INSTALL HOWTO FOR BSD
=====================

HW Probe 1.6.5 (Sep 18, 2022)

This file explains how to install and setup environment for the tool in your computer.

Just find the name of your BSD variant on this page.

See more info in the [README.md](README.md).


Contents
--------

* [ Install on FreeBSD     ](#install-on-freebsd)
* [ Install on OpenBSD     ](#install-on-openbsd)
* [ Install on NetBSD      ](#install-on-netbsd)
* [ Install on helloSystem ](#install-on-hellosystem)
* [ Install on MyBee       ](#install-on-mybee)
* [ Install on DragonFly   ](#install-on-dragonfly)
* [ Install on MidnightBSD ](#install-on-midnightbsd)
* [ Install on OPNsense    ](#install-on-opnsense)
* [ Install on TrueNAS     ](#install-on-truenas)
* [ Install on FreeNAS     ](#install-on-freenas)
* [ Install on pfSense     ](#install-on-pfsense)
* [ Install on XigmaNAS    ](#install-on-xigmanas)
* [ Install on other BSD   ](#install-on-other-bsd)
* [ Easy way to contribute ](#easy-way-to-contribute)
* [ Run without Installing ](#run-without-installing)


Install on FreeBSD
------------------

On FreeBSD and derivatives (GhostBSD, NomadBSD, FuryBSD, TrueOS, PC-BSD, HardenedBSD, DesktopBSD, ArisbluBSD, helloSystem, etc.).

###### Latest systems

For FreeBSD 11.x, 12.x and newer and derivatives install this port: https://www.freshports.org/sysutils/hw-probe/

    pkg install hw-probe

or manually:

    cd /usr/ports/sysutils/hw-probe
    make install

Probe your computer:

    hw-probe -all -upload

###### From upstream

Get latest version of the tool:

    fetch http://bsd-hardware.info/hw-probe

Install dependencies manually:

    pkg install dmidecode smartmontools hwstat lscpu curl perl5

or automatically:

    perl hw-probe -install-deps

Probe your computer:

    perl hw-probe -all -upload

###### Old systems

Get the tool from upstream (see above) and install deps in the following way:

For old FreeBSD releases < 9.3:

    env PACKAGESITE='http://ftp-archive.freebsd.org/pub/FreeBSD-Archive/ports/<ARCH>/packages-<FREEBSD_RELEASE>-release/Latest/' pkg_add -r dmidecode smartmontools hwstat cpuid curl perl

For older FreeBSD releases < 8.0 you need also `usbutil` package to be installed:

    pkg_add -r usbutil

For older FreeBSD releases < 7.0:

    pkg_add -r p5-Digest-SHA

Oldest supported FreeBSD version is currently 6.4.

Probe your computer:

    perl hw-probe -all -upload

###### Graphical desktops

Desktop users should enable `sudo` by installing `sudo` package and adding user to `sudoers` file (https://www.freebsd.org/doc/handbook/security-sudo.html) to preserve user environment variables:

    sudo -E hw-probe -all -upload


Install on OpenBSD
------------------

On OpenBSD and derivatives (AdJ, FuguIta, etc.).

###### Latest systems

For OpenBSD, a package is available (see https://cvsweb.openbsd.org/ports/sysutils/hw-probe/):

    pkg_add hw-probe

Probe your computer:

    hw-probe -all -upload

###### From upstream

Get the tool:

    ftp http://bsd-hardware.info/hw-probe

Install dependencies manually:

    pkg_add dmidecode smartmontools usbutil lscpu curl

or automatically:

    perl hw-probe -install-deps

Probe your computer:

    perl hw-probe -all -upload

###### Old systems

For old OpenBSD releases < 6.5:

    PKG_PATH=https://ftp.nluug.nl/OpenBSD/<OPENBSD_RELEASE>/packages/<ARCH> pkg_add dmidecode smartmontools usbutil lscpu curl


Install on NetBSD
-----------------

On NetBSD and derivatives (OS108, etc.).

Get the tool:

    ftp http://bsd-hardware.info/hw-probe

Install dependencies manually:

    pkgin install dmidecode smartmontools usbutil curl perl

or automatically:

    perl hw-probe -install-deps

Probe your computer:

    perl hw-probe -all -upload


Install on helloSystem
----------------------

Pre-installed on helloSystem 0.3.0 and newer. From the menu, launch the __Hardware Probe__ utility and follow the on-screen instructions:

![image](https://user-images.githubusercontent.com/2480569/103484839-12564480-4df2-11eb-8c57-d6ee6ef48e2b.png)


Install on MyBee
----------------

Pre-installed on MyBee 13.1 and newer.


Install on DragonFly
--------------------

###### Latest systems

For DragonFlyBSD 5.8 and newer install this dport: https://github.com/DragonFlyBSD/DPorts/tree/master/sysutils/hw-probe

    pkg install hw-probe

Probe your computer:

    hw-probe -all -upload

###### From upstream

Get latest version of the tool:

    fetch http://bsd-hardware.info/hw-probe

Install dependencies manually:

    pkg install dmidecode smartmontools hwstat lscpu curl perl5

or automatically:

    perl hw-probe -install-deps

Probe your computer:

    perl hw-probe -all -upload


Install on MidnightBSD
----------------------

###### Latest systems

For MidnightBSD 1.2.7 and newer install this mport: https://www.midnightbsd.org/mports/sysutils/hw-probe/

    mport install hw-probe

Probe your computer:

    hw-probe -all -upload

###### From upstream

Get latest version of the tool:

    fetch http://bsd-hardware.info/hw-probe

Install dependencies manually:

    mport install dmidecode smartmontools cpuid curl perl

or automatically:

    perl hw-probe -install-deps

Probe your computer:

    perl hw-probe -all -upload


Install on OPNsense
-------------------

For OPNsense 20.7.8 and newer.

Install os-hw-probe plugin under Menu->System->Firmware->Plugins.


Install on TrueNAS
------------------

For TrueNAS 12 and newer:

    pkg add https://pkg.freebsd.org/FreeBSD:12:amd64/latest/All/lscpu-1.2.0.txz https://pkg.freebsd.org/FreeBSD:12:amd64/latest/All/hwstat-0.5.1.txz https://pkg.freebsd.org/FreeBSD:12:amd64/latest/All/hw-probe-1.6.b2.txz

Alternatively you can enable FreeBSD repository and install the package from there:

    sed 's/enabled: yes/enabled: no/' /usr/local/etc/pkg/repos/local.conf
    sed 's/enabled: no/enabled: yes/' /usr/local/etc/pkg/repos/FreeBSD.conf
    pkg install hw-probe

Probe your computer:

    hw-probe -all -upload


Install on FreeNAS
------------------

For FreeNAS 11.x:

    pkg add https://pkg.freebsd.org/FreeBSD:11:amd64/latest/All/lscpu-1.2.0.txz https://pkg.freebsd.org/FreeBSD:11:amd64/latest/All/hwstat-0.5.1.txz https://pkg.freebsd.org/FreeBSD:11:amd64/latest/All/hw-probe-1.6.b2.txz

Alternatively you can enable FreeBSD repository and install the package from there:

    sed 's/enabled: yes/enabled: no/' /usr/local/etc/pkg/repos/local.conf
    sed 's/enabled: no/enabled: yes/' /usr/local/etc/pkg/repos/FreeBSD.conf
    pkg install hw-probe

Probe your computer:

    hw-probe -all -upload


Install on pfSense
------------------

For pfSense 2.5.x:

    pkg add https://pkg.freebsd.org/FreeBSD:12:amd64/latest/All/lscpu-1.2.0.txz https://pkg.freebsd.org/FreeBSD:12:amd64/latest/All/hwstat-0.5.1.txz https://pkg.freebsd.org/FreeBSD:12:amd64/latest/All/hw-probe-1.6.b2.txz

For pfSense 2.4.x:

    pkg add https://pkg.freebsd.org/FreeBSD:11:amd64/latest/All/lscpu-1.2.0.txz https://pkg.freebsd.org/FreeBSD:11:amd64/latest/All/hwstat-0.5.1.txz https://pkg.freebsd.org/FreeBSD:11:amd64/latest/All/hw-probe-1.6.b2.txz

Alternatively you can enable FreeBSD repository and install the package from there:

    sed 's/enabled: no/enabled: yes/' /usr/local/etc/pkg/repos/pfSense.conf
    pkg install hw-probe

Probe your computer:

    /usr/local/bin/hw-probe -all -upload


Install on XigmaNAS
-------------------

Install package:

    pkg install hw-probe

Probe your computer:

    /usr/local/bin/hw-probe -all -upload


Install on other BSD
--------------------

Get the tool:

    curl -s http://bsd-hardware.info/hw-probe > hw-probe

On first run the tool will ask to install missed dependencies (perl, dmidecode, smartmontools, lscpu, curl). You can install them manually or automatically with the help of the following option:

    perl hw-probe -install-deps

Probe your computer:

    perl hw-probe -all -upload


Easy way to Contribute
----------------------

Everyone can contribute to the database even without having BSD installed on their computers by writing [helloSystem Live image](https://github.com/helloSystem/ISO/releases) to a USB stick once and then probing all the computers around w/o the need to install or modify anything!

Just do:

* Download and write the [helloSystem Live image](https://github.com/helloSystem/ISO/releases) to any USB stick
* Plug it to any computer
* Power on the computer, enter the Boot Menu and select the USB stick
* Connect to WiFi or just plug the Ethernet cable
* From the menu, launch the __Hardware Probe__ utility and follow the on-screen instructions

Now you can probe all your computers around by booting from this USB stick!

The same can be done with the help of [NomadBSD Live USB image](https://www.nomadbsd.org/download.html). In this case follow the [FreeBSD instructions](#install-on-freebsd) on it to install and run hw-probe. Note that at first start NomadBSD will run the setup wizard to prepare the USB stick.


Run without Installing
----------------------

From Github:

    curl -s https://raw.githubusercontent.com/linuxhw/hw-probe/master/hw-probe.pl | perl

From upstream (mirror):

    curl -s http://bsd-hardware.info/hw-probe | perl


Enjoy!
