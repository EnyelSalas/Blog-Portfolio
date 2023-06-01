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
For the Initial part of the investigation, I opened up the Pcap the provided Pcap on wireshark then  filtered for HTTP/TLS/TCP/DNS traffic by using the command (http.request or tls.handshake.type eq 1) and !(ssdp), I found an interesting file HTTP request and looked up the IPV4 our user  connected to (173.254.32.85),by looking it up in the Virustotal/urlhaus  database results shown in the Images below.

For the Initial part of the investigation, I opened up the Pcap the provided Pcap on wireshark then  filtered for HTTP/TLS/TCP/DNS traffic by using the wireshark filter (http.request or tls.handshake.type eq 1) and !(ssdp), I found an interesting file HTTP request, I took a closer look, this URL https://image-thaihometown.com/mise/Cliente.zip came up as malicious on the Virustotal/urlHaus database results shown in the image came up as malicious on the Virustotal/urlHaus database results shown in the image.
<img width="804" alt="Screen Shot 2023-05-31 at 7 11 31 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/1675b300-1c44-4647-ad14-07c7b83587cd">
<img width="1440" alt="Screen Shot 2023-06-01 at 6 15 40 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/42ef9897-a1ce-4779-9953-e13ea3e7268f">

The filter on the green shows a .zip file, the stream follow feature in wireshark shown below. wireshark downloaded data using Use the File → Export Objects → HTTP menu path to export Cliente.zip from the found objects Pcap as shown in image
C2.
<img width="832" alt="Screen Shot 2023-06-01 at 7 07 36 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/d269ed18-d2d2-42e0-8ace-b8c6fe9866cb">

Virus total/urlHAUSresults:
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


<img width="728" alt="Screen Shot 2023-05-31 at 7 17 15 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/af019a53-2dfd-4968-ad70-be5d862ccb0d">

1-Unzip Cliente.zip
<img width="739" alt="Screen Shot 2023-05-31 at 7 19 00 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/c070339c-83d2-4cb3-bd49-2efa38d28626">

2-cd Cliente 
3-less Cliente.url
<img width="739" alt="Screen Shot 2023-05-31 at 7 19 00 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/fb70b5fb-cc21-4fbc-8365-3ea068995318">





