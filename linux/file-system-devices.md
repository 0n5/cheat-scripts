Linux File System and Devices 
=================

Everything in Linux is treated as a file (files, folders, devices)


#### Pseudo filesystems

procfs

* file system that contains information on system hardware and state of the system contained in psuedo filesystem
* mounted at /proc
* numbers in this directory are process ID's of running processes on system
* interrupts are numbers associated with a process used by kernel modules or drivers to interrupt CPU

```
cat /proc/interrupts   # contains info about the interrupts on the system and whats using them
```

* ioports are addresses that identify a device and the kernel module associated with it

```
cat /proc/ioports   # shows all plugged in devices such as drives, (SATA, IDE etc)
```

* dma allows a device to access system memory directory 

```
cat /proc/dma
```

sysfs

* mounted at /sys
* directories correspond to hardware and kernel modules assoicated with the system
* there are no process IDs in sysfs
* System device info such as loop, ram, vda a vdb are located here


#### Devices

* located at /dev and includes a list of device files (disks, ttys, loops, ram, urandom etc)
* udev is the device manager that detects and configures the devices when connected (hotplugging)
* dbus allows desktop apps to send messages to other apps or to and from linux kernel



#### Tools and Utilities

    lsmod   # shows the kernel modules, size and the process ID / device associated with it
    
    lscpu          # displays information about the CPU architecture such as threads, # of CPUs, Byte Order, size, chip type etc
    lscpu --parse  # returns info in CSV format 
    
    lsblk     # lists block devices such vda, vdb
    lsblk -f  # includes info about filesystem including the label, mount point and file system type
    lsblk -t  # includes info about partitions

    lspci      # lists Ethernet, VGA, USB etc that may be plugged into the PCI drive
    lspci -v   # verbose mode with more info about device hardware, manufacturer name etc
    lspci -m   # space delimited

    lsscsi     # lists SCSI attached devices (may require installation)
    lsscsi -g  # lists generic SCSI device name
    lsscsi -s  # lists size info
    lsssci -l  # long view, lets you know if the state is running
    lsssci -v  # verbose mode

    lsusb                # list of USB devices ID, name and the BUS they are plugged into
    lsusb -s [BUS]:[ID]  # lists info for just the one BUS and device 
    lsusb -d [VENDOR_ID] # lists info for just the specific vendor
    lsusb -t             # lists output in ascii tree format

    lsraid  # lists any RAID devices connected to system (typically not installed)

    lsdev   # lists everything detected by the running kernel ( may need to `apt-get install procinfo` first)
