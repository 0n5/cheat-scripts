Windows paths and directories
=============================

#### Operating System Version #'s

	NT 5.1 XP
	NT 5.2 XP 64bit, Server 2003 and R2
	NT 6.0 Vista, Server 08
	NT 6.1 Windows 7, Server 08 r2
	NT 6.2 Windows 8, Server 2012
	NT 6.3 Windows 8.1, Server 2012 R2
	10.0   Windows 10, Server 2016

	> ver # prints out OS version

#### Event logs

	C:\Windows\System32\Config      # XP
	C:\Windows\System32\winevt\Logs # Vista, 7

#### Recycle Bin

	C:\Recycler\[USER_SID\	     # XP
	C:\$Recycle.Bin\[USER_SID\   # vista, 7

#### LNK files

	C:\Users\[USER]\AppData\Roaming\Microsoft\Office\Recent	                   # vista, 7
	C:\Documents and Settings\[USER]\Application\Data\Microsoft\Office\Recent  # XP
	C:\Users\[USER]\AppData\Roaming\Microsoft\Windows\Recent               	   # vista, 7
	C:\Documents and Settings\[USER]\Recent	                                   # XP

#### Search Index

	C:\All Users\Application\Data\Microsoft\Search\Data\Applications\Windows 	# vista, 7

#### Setup API logs:

	C:\windows\setupapi.log	  # stored in plaintext

#### NPAPI

	%APPDATA%\Macromedia\Flash Player\#SharedObjects\  # NT 5 and 6
	%APPDATA%\Macromedia\Flash Player\macromedia.com\support\flashplayer\sys\

#### PPAPI

Chrome pepperflash

	%APPDATA%\..\Local Settings\Application Data\Google\Chrome\User Data\Default\Pepper Data\Shockwave Flash\WritableRoot\#SharedObjects


#### Thumbs db

	\Users\%username%\AppData\Local\Microsoft\Windows\Explorer    # vista, 7
	
#### Temp files

	/Document and Settings/%username%/Local Settings/Temp	# xp
	C:\Users\%/username%\AppData\Local\Temp	                # vista, 7
