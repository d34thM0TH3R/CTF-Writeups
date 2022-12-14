---
exclude: true
---
# Passing On Complexity

[deadface 2022](..)  

## Problem Description

ESU's IT staff swears up and down that the backup user's password is secure and follows best practice. Their internal auditors are not convinced and are asking for your help to determine the backup user's password at the time of the breach.

Submit the flag as flag{password}.

Use the packet capture from Scans.

## Write Up

The problem tells us we are looking for the backup user's password, so searching the file with this filter `tcp contains "backup"` gives us the below result.

![PCAP filtered for backup](backupFiltered.PNG "Backup filter in place")



Following the TCP stream shows us what was happening in the stream. The commands ran look like someone who just got access to a system. Scrolling to the bottom of the stream a script is executed containing the password.

![PCAP with backup password](backupPassword.PNG "Backup password shown")



The python code `-u backup -pbackup123` indicates the backup user has the password "backup123".

## Flag

flag{backup123}
