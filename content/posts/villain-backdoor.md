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
+++
Hoaxshell/Villain Powershell Backdoor Generator Payloads in the  Wild, and How to Detect in Your Environment.
<!--more-->

## Background
I wanted to test out if my memory dumps contained information about backdoors, and needed a quick and easy backdoor to use. I found [Villain](https://github.com/t3l3machus/Villain), and it was very easy to set up and inject my Windows VM to get a working backdoor in my lab setup.

## Other work
Securonix Threat Labs has done threat research on the subject, and I urge you to check out their [blog post](https://www.securonix.com/blog/hoaxshell-villain-powershell-backdoor-generator-payloads-in-the-wild-and-how-to-detect-in-your-environment/).

## Indicators of Compromise
I was also in the process of relearning volatility (going from vol2 to vol3) and learning how to write and use yara rules. 

Resources:
* https://www.securonix.com/blog/hoaxshell-villain-powershell-backdoor-generator-payloads-in-the-wild-and-how-to-detect-in-your-environment/