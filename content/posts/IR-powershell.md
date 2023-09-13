+++
author = "s0vi"
title = "Incident response and Powershell!"
date = "2023-05-06"
description = "Powershell snippets useful for IR"
tags = [
    "powershell",
    "IR",
]
categories = [
    "howto",
    "incident response",
]
draft = true
+++

These are some handy snippets of powershell commands used to get a basic live data forensics (LDF).
<!--more-->
## Overview and background
We need as much relevant information we can get ASAP. I've analyzed numerous dead systems, where some information can be really hard to find, but easy to find on a live system. This is due to differences between Windows 10/11 and 

## NIST Methodology

## OODA-loop
I initially learned about the OODA-loop when I was in the military. Now that I've been heading into incident response with both legs, I saw Dr. Brian Carrier had written an excellent [blog post](https://www.cybertriage.com/blog/training/how-to-use-ooda-loop-in-your-incident-response-process/) at CyberTriage.

From the blog post I have just copied the four phases:

* Observe: Observe the situation using a variety of sources that are available. You will never be able to collect all data before making your first decision
* Orient: Use your experience and training to make sense of what you are seeing. Make hypotheses about what is happening and predictions about what could happen next
* Decide: Based on your goals, orientation, and timing needs, decide on what action to take and when. Actions could include testing a hypothesis about the current state (i.e. get more data) or to try to change the predictions about what will happen next (i.e. thwart a bad guy)
* Act: Implement the decision.

## 4WH
If there is an investigation, we should aim to answer the following questions:

1. Where did it happen?
2. Who did it?
3. What happened?
4. When did it happen?
5. Why did it happen?
6. And how did it happen?

However, this is more relevant in digital forensics when the law enforcement units are investigating crime. 

Question    |   Answer      | Why it is important
------------|---------------|--------------------
Where?      |               |                   

## Conclusion and my take on all this
