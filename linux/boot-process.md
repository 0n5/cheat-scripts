Linux Boot Process
=====


### sysvinit

* package containing a group of processes that control the basics functions of the system
* includes `init` application, the first app started by the kernel after boot loader starts boot process
* init controls all the startup, running and shutdown of all other programs, becoming the parent
* processes are assigned a number based on the order that they start
* init is always going to be PID 1

sysvinit runelevels

* Never set the runlevels to 0 or 6 as initdefault

0. HALT (shutdown)
1. Single User
2. Multi User (no network or remote filesystems)
3. Full Multi User (networking and remote systems mounted)
4. Unused
5. X11 (full multi user with GUI desktop)
6. Reboot

```
cat /etc/inittab   # shows default runlevel
```

```
runlevel  # tells you what your current runlevel number is
```

Change the `id:[ID]:initdefualt` line to change the default runlevel

Modern systems use upstart and read from the /etc/init directory

#### Boot Process for sysvinit

1. System powers on
2. BIOS and / or EFI loads
3. BIOS finds primary or chosen disk's boot sector 
4. Boot Sector provides the Master Boot Record within first 512 bytes (can be external drive as well)
5. Boot Loader is executed (LILO, GRUB, or GRUB2 starts) and scans the system to determines what can start
6. Menu may load allowing you to chooose from a list of Operating systems, kernel versions etc or loads default
7. Linux kernel is read and executed
8. Devices are initialized, modules loaded into memory (initrd)
9. Root filesystem is mounted
10. init program loads and becomes first PID /sbin/init
11. /etc/inittab is read and runlevel scripts are run 
12. modules indicated inside the runlevel scripts are loaded
13. root file system is checked
14. remaining local file systems are mounted
15. network devices are started
16. remote filesystems (if any) are mounted
17. init rescans /etc/inittab file and changes the runlevel and completes execution of scripts
18. runlevel scripts are executed in numerical order  
19. TTY sessions are loaded (if listed in /etc/inittab)
20. System login prompt displayed


### RC Scripts - sysvinit

runlevel scripts and services

* Located at `/etc` directory for debian based systems
* Located at `/etc/rc.d` on rhel systems
* services (such as sshd, nfs, smb etc) located at `/etc/init.d` or `/etc/rc.d/init.d`
* rc.d scripts will execute scripts that are linked to init.d scripts and run in a specific numerical order based on S & K tags
* scripts executed in rc0.d thru rc6.d will be executed when the inittab is read on boot for that particular runlevel selection
* anything in rc.d scripts that start with `K` is a kill script
* anything in rc.d scripts that start with `S` is a startup script


### Upstart

* primarily used by Ubuntu
* asynch boot and shutdown process
* compatible with sysvinit
* no longer used after Ubuntu 12 LTS



### systemd

* initialization system for bootstrapping the user space and managing all processes for system start
* replacement for sysvinit
* default on all modern Linux distributions

systemd runlevels

0. poweroff.target (shutdown)
1. rescue.target (Single user /rescue Shell)
2. multi-user.target (Non GUI, Full Network, Multi user)
3. multi-user.target (Non GUI, Full Network, Multi user)
4. multi-user.target (Non GUI, Full Network, Multi user)
5. graphical.target (GUI, Multi User)
6. reboot.target (Reboot)

* Never set the runlevel targets to 0 or 6

```
runlevel  # tells you what your current runlevel number is
```

```
/usr/lib/systemd/system
# contains all the services and targets files and symlinks

/lib/systemd/system
# Ubuntu 14 LTS
```

#### Boot Process for systemd

1. System powers on
2. BIOS and / or EFI loads
3. BIOS finds primary or chosen disk's boot sector 
4. Boot Sector provides the Master Boot Record within first 512 bytes (can be external drive as well)
5. Boot Loader is executed (LILO, GRUB, or GRUB2 starts) and scans the system to determines what can start
6. Menu may load allowing you to chooose from a list of Operating systems, kernel versions etc or loads default
7. Linux kernel is read and executed
8. Devices are initialized, modules loaded into memory (initrd)
9. Root filesystem is mounted
10. systemd runs
11. default run target and dependencies are executed
12. modules indicated within the runlevel target and dependencies are executed
13. root filesteym is checked
14. remaining local filesystems are mounted
15. systemd sets runlevel as indicated in default target
16. System login prompt displayed