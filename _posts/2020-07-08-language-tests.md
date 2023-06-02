---
layout: post
title: "Unveiling the Gozi Infection: Detecting Gozi in an Active Directory (AD) Environment Using Wireshark.
"
---

In this blog post, we delve into the realm of Gozi infections within Active Directory (AD) environments. Specifically, we explore how Wireshark, a popular network analysis tool, can be utilized to identify and uncover the presence of Gozi within AD networks. By understanding the history and evolution of Gozi, we gain valuable insights into its behavior and techniques, equipping us with the knowledge needed to detect and mitigate this persistent threat.

Gozi, a notorious banking trojan, has plagued the cybersecurity landscape for over a decade. With its evolution and various iterations, such as Ursnif, Snifula, Gozi v1.0, and Gozi v2.0, this malware has left a trail of financial theft and compromised systems in its wake. In 2006, Gozi v1.0 emerged as a sophisticated piece of code, borrowing elements from Ursnif and other spyware kits. Its initial release, known as Gozi CRM or CRM, introduced a formgrabber module that enabled sensitive data interception.

The Gozi saga took an intriguing turn in September 2010 when the source code for a specific Gozi CRM dll version was leaked. This event led to the creation of Vawtrak/Neverquest, in combination with Pony, through two modified versions of Gozi: Gozi Prinimalka, a slightly altered Gozi v1.0, and Gozi v2.0, also referred to as Gozi ISFB or ISFB, and sometimes Pandemyia. These iterations included a powerful webinject module, adding another layer of threat to their capabilities.

Join us as we embark on a journey to unravel the secrets of Gozi, shed light on its complex history, and empower defenders with the tools to identify and combat this elusive malware within AD environments using the power of Wireshark.

Narrative:
For the Initial part of the investigation, I opened up the Pcap the provided Pcap on wireshark then filtered for HTTP/TLS/TCP/DNS traffic by using the command (http.request or tls.handshake.type eq 1) and !(ssdp), I found an interesting file HTTP request and looked up the IPV4 our user  connected to (173.254.32.85),by looking it up in the Virustotal/urlhaus database results shown in the Images below.

For the Initial part of the investigation, I opened up the Pcap the provided Pcap on wireshark then  filtered for HTTP/TLS/TCP/DNS traffic by using the wireshark filter (http.request or tls.handshake.type eq 1) and !(ssdp), I found an interesting file HTTP request, I took a closer look, this URL https://image-thaihometown.com/mise/Cliente.zip came up as malicious on the Virustotal/urlHaus database results shown in the image came up as malicious on the Virustotal/urlHaus database results shown in the image.

<img width="804" alt="Screen Shot 2023-05-31 at 7 11 31 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/1675b300-1c44-4647-ad14-07c7b83587cd">

<img width="1440" alt="Screen Shot 2023-06-01 at 6 15 40 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/42ef9897-a1ce-4779-9953-e13ea3e7268f">

The filter on the green shows a .zip file, the stream follow feature in wireshark shown below, Wireshark downloaded data using Use the File → Export Objects → HTTP menu path to export Cliente.zip from the found objects Pcap as shown in the image as C2 inicial actiavity.

<img width="832" alt="Screen Shot 2023-06-01 at 7 07 36 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/d269ed18-d2d2-42e0-8ace-b8c6fe9866cb">

Virus total/URLhaus results:

<img width="1440" alt="Screen Shot 2023-06-01 at 6 15 40 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/b617aec8-e691-447b-9f86-dd45d745d7b0">

<img width="1440" alt="Screen Shot 2023-06-01 at 7 14 44 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/14d77a1b-c644-4db9-a0ea-6d4415b692b3">

<img width="1440" alt="Screen Shot 2023-06-01 at 7 15 52 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/9778ba81-2d6f-40cc-93d6-186c0f4c8b25">

<img width="1440" alt="Screen Shot 2023-06-01 at 7 16 13 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/4585f7bf-d8bb-4afc-8743-3218a6db5ba6">

Results led to this data.
Malware Gozi,ISFB
IoC:
File clinte.zip
IPV4  173.254.32.85/80
MAC
URL https://image-thaihometown.com/mise/Cliente.zip
Hash SHA 256
33db5b2a2cc592fd10c65ba38396e4c7574ad78e786d78e8a3acdc93a90c3209  Cliente.zip
Exchanged 189 packets with malicious IPV4 172.16.1.137/80
Identified as a C2 server.

Then again kept looking for more factual data by filtering for SMB objects extracted by  wireshark, I downloaded SMB files reusing the previous process to extract the file, menu → Export Objects → SMB menu path to export from the found objects Pcap as shown in the image.

<img width="719" alt="Screen Shot 2023-06-01 at 7 58 47 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/cd02a59a-5f26-48ee-bfb6-b440d0dfb696">


1-Unzip Cliente.zip
<img width="739" alt="Screen Shot 2023-05-31 at 7 19 00 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/c070339c-83d2-4cb3-bd49-2efa38d28626">

<p>2-cd Cliente</p>
<p>3-less Cliente.url</p>
<p>This payload will start windows proccess from C:\Windows\sytem32\SHELL32.dll if it's allow to run.</p>
<img width="743" alt="Screen Shot 2023-06-01 at 8 01 35 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/7e563360-7660-4580-a53d-c13067305b94">

<img width="741" alt="Screen Shot 2023-06-01 at 8 02 06 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/09b4443d-7802-433c-8068-40ead8061cc0">

Command: Shasum -a 256 cliente.url revealed hashes that let to malicious files ending in .exe.  

<img width="536" alt="Screen Shot 2023-06-01 at 8 04 42 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/4d0ddeb3-06c5-4ec4-ac3c-de487a59b6fa">


URLs often start with http or https. However, the extracted internet shortcut contains a URL with a file instead of http or https, This URL starting with file generates traffic for the Server Message Block (SMB) protocol over TCP port 445. On a Windows host, content from this URL can be accessed through Windows File Explorer unpacking the malicious C2 process which created the traffic below.

Start time 2023-03-06 21:02:25.519712 , End time 2023-03-06 21:08:45.414338
ex 46.8.19.32/445   172.16.1.137/59376	
IPV4 46.8.19.32 Russia 
MAC 00:0b:46:93:86:da
Files SMB 
Packets 886
Bytes 660.188 KiB
Exchanged  46.8.19.32/445   172.16.1.137/59376	

SMB files containing IoC
The Export SMB object list window has six entries for server.exe from \\46.8.19[.]32\mise as 
ce7dc991d53b07af883e086f37546a1a9a81b371dfae139ebc1ae58f2fc5d5a0  %5cserver(1).exe
925772aed16838f97057edb841c7ffbb682ed577d54173134bce2e32c8e2be7f  %5cserver(2).exe
bad4dae58e7af621287cc2ac78a9f7e6d8d6de2296f270505ba671b7267cc505  %5cserver(3).exe
f3a2cfa158fa80ca84aba9d3e3d9b5374f27db8a2cd03055f07fe00cd98b1322  %5cserver(4).exe
a254c26767435ab507dd40d13c3b96df086248c25afb75356144ad9263135682  %5cserver(5).exe
3bf853d8b536c1c5c9ac4e5df084456378990d869928d36fadbc9b303dca9af0  %5cserver.exe
Enyels-Air:SMB.05-19-23.

IPV4 46.8.19.233 /80 Russia 
5.44.45.201
SHA 256
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855  x.gif
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855  xI2j65.gif

e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855  zE4l.gif
Files  3Y.gif, 4b.gif,  4qYN.gif,  93tEp.gif
IPV4 46.8.19.233 Russia 
Exchanged 16 Packets with  172.16.1.137

Next I applied the search filter to locate the victim's user names and host machine were identified her by looking into kerberos authorization traffic. The Wireshark filter used and applying a CNameString as a column will show the host username of sherita.kolb image.after the Victim  made connection with the C2 server via HTTP GET request.IPV4 172.16.1.137 victim's host. machineMAC 00:02:fb:34:b4:fa
Uname:sherita.kolb

<img width="763" alt="Screen Shot 2023-06-01 at 8 06 49 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/9cbdaf3f-5f93-4e06-aab2-6b9c34ef36fe">

image
Founds:
after the Victim made connection with the C2 server
via HTTP GET request.
IPV4 172.16.1.137 
victim's host. machine
MAC 00:02:fb:34:b4:fa
Uname:sherita.kolb

Next after looking at the suspicious TCP port, I Followed the IPV4 in the picture. 

<img width="788" alt="Screen Shot 2023-06-01 at 8 09 35 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/3da2033c-a2e2-42f4-802e-435cf211b173">

Post-infection traffic for Gozi:
After unsuccessfully filtering for TLS, SMTP,POP,VNC traffic all I found was HTTP/80 traffic by using the wireshark filter.
Gozi traffic consists of encoded data most often sent using unencrypted HTTP GET and POST requests over TCP port 80.
In this particular case, the command and control (C2) servers for Gozi use IP addresses instead of domains.
62.173.140.103 . I was able to spot the post infection  C2 Server by going back to virus total and looking up the linked IPV4.
image.

Note: These URLs were found http malicious because of the post -infection between the time of occurrence at start time  2023-03-06  21:01:56.617313,  end time  2023-03-06  21:32:56.640999.
<img width="828" alt="Screen Shot 2023-06-01 at 8 12 35 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/7c8d84c3-55a8-4688-94ef-f7f0a6b0b671">


Gozi traffic consists of HTTP GET and POST requests with long URLs that contain base64 text with backslashes and underscores. Data sent to and received from these C2 servers are encoded or encrypted. an example from the initial HTTP GET request for Gozi C2 traffic.
Gozi uses modules or plugins that perform various functions like stealing passwords from a victim’s browser cache. These modules are sent as encoded or encrypted binaries using relatively short URLs ending in .rar, such as:
These URLs end in .rar, and HTTP response headers from the C2 server identify the returned files as Content-Type:application/x-rar-compressed. However, these files are not .rar archives. They are encoded or encrypted binaries.

6-[Full request URI: http://62.173.149.243/stilak32.rar]

7-[Full request URI: http://62.173.149.243/stilak64.rar]

11-[Full request URI: http://62.173.149.243/cook32.rar]

12-[Full request URI: http://62.173.149.243/cook64.rar]


Here are 3 links that provide more details, one including the mitre attack, the other 2 are articles that will help understand Gozi's history and malicous payloads.

https://mitre-attack.github.io/attack-navigator//#layerURL=https%3A%2F%2Fattack.mitre.org%2Fsoftware%2FS0386%2FS0386-enterprise-layer.json

https://0xtoxin.github.io/threat%20breakdown/Gozi-Italy-Campaign/

https://medium.com/csis-techblog/chapter-1-from-gozi-to-isfb-the-history-of-a-mythical-malware-family-82e592577fef


In conclusion, the discovery and detection of Gozi infections in an Active Directory environment using Wireshark are crucial steps in protecting organizations against this persistent banking trojan. By tracing the origins and evolution of Gozi, we have gained valuable knowledge about its techniques and behaviors. Armed with this understanding, we can leverage the power of Wireshark to analyze network traffic, identify suspicious patterns, and uncover the presence of Gozi within AD networks.

The battle against Gozi and its variants, such as Ursnif, Snifula, Gozi v1.0, and Gozi v2.0, is an ongoing endeavor. However, by staying vigilant, keeping abreast of the latest developments, and utilizing advanced tools like Wireshark, organizations can significantly enhance their defense capabilities.

Through continuous research, collaboration, and proactive measures, we can strive to stay one step ahead of Gozi and other malware threats, safeguarding sensitive information, and ensuring the security of our digital ecosystems. Let us remain committed to the pursuit of cybersecurity excellence, armed with knowledge, tools, and a resilient mindset. Together, we can fortify our defenses and mitigate the risks posed by Gozi and other malicious actors in the ever-evolving landscape of cyber threats.
Screenshot
Regenerate response.











