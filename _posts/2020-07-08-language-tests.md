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


<img width="1440" alt="Screen Shot 2023-05-19 at 9 26 13 AM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/b7ba7fbf-7253-453e-bf3d-8cfcef09c4f4">


