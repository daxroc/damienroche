---
author: "Damien Roche"
date: 2011-10-18
linktitle: FreeNAS mount an NTFS ISCSI extension as a local disk
title: FreeNAS mount an NTFS ISCSI extension as a local disk
highlight: true
url: /blog/database/mysql_point_datatype.html
---
This is how to mount a local ISCSI extension image as if it were an actual physical drive.

First make sure you disable access to this ISCSI target as you could irrevocably damage your data trying to access it twice.

Then create a virtual pointer using mdconfig

```
mdconfig -a -f /mnt/Storage/extents/image.img
```
The above command will return a device name eg md3

Now Load the fuse module

```
kldload /usr/local/modules/fuse.ko
```
Create a mount point for the drive and mount it using ntfs-3g

```
mkdir /mnt/mountpoint
ntfs-3g /dev/md? /mnt/mountpoint
```
Unmount the drive.

```
umount /mnt/Storage/mountpoint
```
Unlink the device from the file.

```
mdconfig -d -u md?
```
Check out the FreeNAS Documentation
Check out mdconfig man page.

If you have any questions or tips please post them, I’ll try and get back to you.
