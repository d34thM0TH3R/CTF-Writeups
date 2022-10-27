# Escalation

## Problem Description

Somehow, the attacker was able to gain root access to the web server. We believe the attacker leveraged an existing file to gain root access. What file was modified to allow the attacker to gain root on the web server?

Submit the name of the file and the name of the variable used to store the added command. Example: flag{backdoor.exe_var1} if backdoor.exe is the name of the file and var1 is the name of the variable.

Use the packet capture from Scans.

## Write Up

Examining the same TCP stream we see an existing file being edited.

![PCAP showing a file being edited](fileEdited.PNG "File being edited")

The file "backup.py" was copied, moved, and edited. 
The attacker added code to open a socket and allow them to run "/bin/bash". This code was saved in a variable `cmd`. 
Combining what we have learned we get the internals of the flag, "backup.py_cmd".

## Flag

flag{backup.py_cmd}
