+++
author = "s0vi"
title = "Running .e01 in VirtualBox"
date = "2023-05-04"
description = "A nice howto for own reference"
tags = [
    "e01",
    "virtualbox",
    "tools",
]
categories = [
    "forensics",
    "tools",
]
+++

Doing forensically sound investigations running a image live. Excellent to show what the user might have seen. <!--more-->

## Requirements
Install Virtual Box and FTK Imager. Mount the image to Drive. Not sure if you need both Physical & Logical (to be testet).

Mount method: Block Device/ Writable
Write Cache Folder: Specify where you want it.

The mounting will take som time. In the Mapped Image List you will see what drive and partition it is. Choose the right PhysicalDriveX where X is the number. Depending on how many physical drives you have (e.g. If you have mounted external harddrives etc), the number will change.

```
VBoxManage.exe createmedium disk --filename="C:\image\image.vmdk" --variant=RawDisk --format=VMDK --property RawDrive=\\.\PhysicalDrive4
```

Create a new Virtual Machine. Choose the correct OS and remember to use UEFI if its a newer Windows OS (e.g. 10 or 11). If it is a seized object, remember to turn off the network adapters. 

If you forgot the password to the account, make sure to have an USB handy and use a password tool. Enable USB Controll and use USB 2.0.

SATA usually works, but you might change the harddrive to a SCSI if it doesn't.