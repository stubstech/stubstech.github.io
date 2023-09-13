+++
author = "s0vi"
title = "Backdoor: Villain - IOCs for you to use"
date = "2023-09-10"
description = "My notes from looking at Villain"
tags = [
    "vmem",
    "vmware",
    "memory forensics",
    "IR",
]
categories = [
    "forensics",
    "incident response",
]
draft = true
+++
Hoaxshell/Villain Powershell Backdoor Generator Payloads in the  Wild, and How to Detect in Your Environment.
<!--more-->

## Background
I wanted to test out if my memory dumps contained information about backdoors, and needed a quick and easy backdoor to use. I found [Villain](https://github.com/t3l3machus/Villain), and it was very easy to set up and inject my Windows VM to get a working backdoor in my lab setup.

## Other work
Securonix Threat Labs has done threat research on the subject, and I urge you to check out their [blog post](https://www.securonix.com/blog/hoaxshell-villain-powershell-backdoor-generator-payloads-in-the-wild-and-how-to-detect-in-your-environment/).

## Indicators of Compromise
I was also in the process of relearning volatility (going from vol2 to vol3) and learning how to write and use yara rules. 

## Detection
While I did some research using volatility3 and used the windows.cmdline.CmdLine module, I forgot that I had Defender enabled.
Defender took action and deleted the file containing the payload under the name "Trojan:PowerShell/ReverseShell.SA". Note that I did not obfuscate or encode the payload.

Resources:
* https://www.securonix.com/blog/hoaxshell-villain-powershell-backdoor-generator-payloads-in-the-wild-and-how-to-detect-in-your-environment/
* [Microsoft Description](https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?name=Trojan%3APowerShell%2FReverseShell.SA&threatid=2147792911&enterprise=1)