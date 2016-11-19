---
author: "Damien Roche"
date: 2016-10-27
linktitle: Pine64 Cluster
title: Creating a Pine64 Cluster
highlight: true
url: /blog/pine64/index.html
---
# DRAFT - Work in progress...
![Pine64 Got Wood](/static/img/pine64_got_wood.jpg)
### **Introduction**
The Pine64 is a Quad Core 64-bit single board computer available in several configurations. The following is my documentation effort on the building of packages for the latest Docker cli and damon, Containerd and Runc in order to further build out a Mesos and Marathon deployment ontop of ARM-V8 powered hardware

### **Flash the Debian image**
On OSX 
Using `diskutil list` we can find out the disks attached and determine which we want to target.

In my case it's ... Now using `dd` tool I'm going to image the disk. 
```
dd if=<image-path/filename.img> of=/dev/<slash-dev-disk>
```

### **Gotcha - Updating the network MAC Address**
You'll need to update the network MAC address if you plan on deploying more than one board to your network. Note only power one on at a time to remove any potential for conflicting/duplicate MAC address issues.

Edit `/boot/uEnv.txt` updating the `etchaddr` with a unique value for each of your boards.
```
console=tty0 console=ttyS0,115200n8 no_console_suspend
kernel_filename=pine64/Image
initrd_filename=initrd.img
optargs=disp.screen0_output_mode=720p60
ethaddr=36:c9:e3:f1:b8:00
```


### Building Docker from source - oh the fun :D


### Building Containerd

### Building Runc

### Now lets build it all again "official"
Docker uses docker to build within a sandboxed environment this seems to be the "official / supported method"..

