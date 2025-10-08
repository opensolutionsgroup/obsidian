---
creation date: Wednesday 10th May 2023  2:53:20 pm
modification date: Wednesday 8th October 2025  12:56:24 pm
created by: Paul Miskovsky
tags: [note, linux]
aliases: []
publish: true
title: DD Disk Recovery
---

# DD Disk Recovery
---
### Installation

Type the following into the terminal:

```sh
sudo apt-get install smartmontools 
sudo apt-get install gsmartcontrol
```

### Checking a Drive for SMART Capability

To ensure that your drive supports SMART, type:

```sh
sudo smartctl -i /dev/sda 
```

where /dev/sda is your hard drive. This will give you brief information about your drive. The last two lines may look something like this:

```
SMART support is: Available - device has SMART capability.
SMART support is: Enabled 
```

### Enabling SMART

In the case that SMART is not enabled for your drive, you can enable it by typing:

```sh
sudo smartctl -s on /dev/sda 
```

### Testing a Drive

```sh
sudo smartctl -c /dev/sda 
```
The most useful test is the extended test (long). You can initiate the test by typing:

```sh
sudo smartctl -t long /dev/sda
```

### Recovery/Cloning

```
df -h
sudo lsblk
sudo fdisk -l
```

```sh
# Clonezilla bootable USB/Parted Magic
https://clonezilla.org/

# OpenSuperClone
https://sourceforge.net/projects/opensuperclone-live/

# R-Linux Free
https://www.r-studio.com/
sudo wget https://www.r-studio.com/downloads/RLinux6_x64.deb
```

```sh
# dd Will handle erros on the clone
sudo dd if=/dev/sdX of=/dev/sdY bs=4096 conv=sync,noerror status=progress  
```

```sh
# Clone entire disk to another device 
sudo apt install gddrescue ddrescueview
sudo ddrescue -v /dev/sdX /dev/sdY /home/user/rescue.log
# Clone in reverse, starting at the end of the drive first
sudo ddrescue -v -R /dev/sdX /dev/sdY /home/user/rescue.log

# Clone partition to a image file that you can mount
sudo ddrescue -d -r1 /dev/sdb2 rawdrive.raw rawdrive.log
# You will not be able to mount  images of entire disks, only partitions.
sudo mount -o loop,ro rawdrive.raw /mnt
# This may be diskimage or partition image.
sudo parted rawdrive.raw
```

```sh
sudo mkdir -p /usr/local/bin/testdisk-7.3-WIP
sudo wget https://www.cgsecurity.org/testdisk-7.3-WIP.linux26-x86_64.tar.bz2
tar -xjf testdisk-7.3-WIP.linux26-x86_64.bz2 -C /usr/local/bin
cd /usr/local/bin/testdisk-7.3-WIP
testdisk
```

### Other

```sh
sudo smartctl -a /dev/sdX  
```

```sh
apt install sysstat  
iostat -xtcd 2
```

---
tags: #note #linux
links: [[Note Template]]
licence: [[Licences/CC BY-SA 4.0|CC BY-SA 4.0]]
code: [[Licences/GNU-GPL-v3.0|GNU-GPL-v3.0]]
sources: