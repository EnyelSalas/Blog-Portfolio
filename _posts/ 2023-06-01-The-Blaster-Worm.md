---
layout: post
title: Blaster Worm 
date: 2023-06-01
---

By: Enyel 
04/19/23

<h1>Buffer Overrun In RPC Interface Allows Code Execution</h1>

Summary:
The Blaster worm is a type of computer virus that exploits a vulnerability in Remote Procedure Call  RPC  ports. It spreads without user action and distributes copies of itself across networks. The worm can also be known by other names, such as W32.Blaster.Worm or WORM_MSBLAST.A. Infected computers may experience symptoms such as error messages or unexpected shutdowns. To detect the virus, search for files named Msblast.exe, Nstask32.exe, Penis32.exe, Teekids.exe, Winlogin.exe, Win32sockdrv.dll, or Yuetyutr.dll in the Windows\System32 folder, or download the latest antivirus software signature from your antivirus vendor and scan your computer.


Description:
A buffer overrun vulnerability in the RPC interface could allow an attacker to execute arbitrary code on a vulnerable system.


Explanation:
A buffer overrun occurs when more data is written to a buffer than it can hold. This can allow an attacker to overwrite adjacent memory locations, potentially leading to the execution of arbitrary code.
The Remote Procedure Call:
 RPC  interface is a protocol that allows one program to execute code on another system. A vulnerability in this interface means that an attacker could exploit this protocol to execute arbitrary code on a vulnerable system.

<h2>The vulnerability:</h2>
Is in the part of RPC that handles message exchange over TCP/IP, specifically the Distributed Component Object Model  DCOM  interface. This interface listens on
 RPC enabled ports and handles DCOM object activation requests. A failure in the system occurs due to the incorrect handling of malformed messages, which can lead to an attacker running code on an affected system with Local System privileges. An attacker would need to send a specially formed request to the remote computer on specific RPC ports. If an attacker is able to exploit this vulnerability, they could execute code on a vulnerable system with the same privileges as the affected application. This could allow an attacker to take control of the system, steal sensitive information, or launch further attacks.

<h2>Symptoms of infection:</h2>
If your computer is infected with this worm, you may not experience any symptoms, or you may experience any of the following symptoms:
You may receive the following error messages:
The Remote Procedure Call  RPC  service terminated unexpectedly.The system is shutting down. Save all work in progress and log off.Any unsaved changes will be lost.This shutdown was initiated by NT AUTHORITY\SYSTEM.


<h2>Solution:</h2>
To exploit the vulnerability, the attacker would require the ability to send a specially crafted request to port 135, 139, 445 or 593 or any other specifically configured RPC port on the remote machine. In intranet environments, these ports would normally be accessible, but for internet-connected machines, these would normally be blocked by a firewall. Therefore, it is recommended to block all TCP/IP ports that are not being used, and most firewalls including the Windows Internet Connection Firewall  ICF  block those ports by default.
RPC over UDP or TCP is not intended to be used in hostile environments such as the Internet. Instead, more robust protocols such as RPC over HTTP are provided for hostile environments.
Download the 824146 security patch from Microsoft, and install it on all your computers to address the vulnerability identified in Microsoft Security Bulletins MS03 026 and MS03 039. This patch replaces the 823980 security patch and includes fixes for the issues addressed in Microsoft Security Bulletin MS03 026  823980 .
Install or update your antivirus signature software, and run a complete system scan.

Download and run the worm-removal tool from your antivirus vendor.
Regularly update your antivirus software and apply any security patches or updates for your operating system and other software.
Additional technical details about the Blaster worm can be obtained from antivirus software vendors who are participating in the Microsoft Virus Information Alliance  VIA .

<h2>Warninng of infections images:</h2>

<img width="959" alt="Screen Shot 2023-06-01 at 4 16 42 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/0a4f4ff8-fc2d-46ea-ae5f-a4785be3e723">
<img width="949" alt="Screen Shot 2023-06-01 at 4 16 55 PM" src="https://github.com/EnyelSalas/Blog-Portfolio/assets/115824437/c57951b0-6059-49ba-b67f-d5e18aeb7caf">
  
 
 
