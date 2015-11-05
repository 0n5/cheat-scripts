Windows System Commands
=======================

#### Operating System Version #'s

	NT 5.1 XP
	NT 5.2 XP 64bit, Server 2003 and R2
	NT 6.0 Vista, Server 08
	NT 6.1 Windows 7, Server 08 r2
	NT 6.2 Windows 8, Server 2012
	NT 6.3 Windows 8.1, Server 2012 R2
	10.0   Windows 10, Server 2016

	> ver # prints out OS version

#### Users

	> echo %USERNAME%  # prints out current user

	lusrmgr.msc        # local user manager


#### Services

	services.msc    # services control panel


#### Proccesses

	taskmgr.exe       # task manager

	> tasklist /svc   # show processes and services
	> tasklist /m     # show processes and dlls


#### Events

	eventvwr.msc   #event viewer


#### Networking

	> ipconfig /displaydns       # local DNS cahce
	> netstat -ano               # open connections
	> route print                # routing table
	> arp -a                     # arp table
	
	> netsh wlan show profiles                       # wireless profiles
	> netsh wlan export profile folder=. key=clear   # export wifi pwd

#### File System
	
	> dir   # list contents of directory

	> find /I "string" [FILE]       # find "string" in the file 
    > fsutil fsinfo drives          # list drives and info
	> tree /F /A c:\ > [OUTPUT]     # exports full directroy tree of C:\


#### Registry

	> reg query HKLM /f password /t REG_SZ /s  # search registry for pwd
	> reg save HKLM\Security security.hive     # dumps security hive


