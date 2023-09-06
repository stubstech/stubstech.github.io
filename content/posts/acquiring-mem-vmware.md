+++
author = "s0vi"
title = "How to acquire memory form a VMWare server"
date = "2023-09-06"
description = "A nice howto for own reference"
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

When handling an incident or just doing some research, memory comes into play. Doing a forensically sound memory acquisition on a VMWare Workstation server is not hard, but there are some pitfalls and things we should be aware of.

## The files we need
Fortunately Volatility reads VMWare vmem files, but we need some metadata about the structure of the file.

The blog article https://angry-bender.github.io/blog/vmware_snapshots_volatility/ shows us what the different files are, but for reference let's get the three most important files depending on what method you choose. Either do a Snapshot or suspend the machine.

In both methods we need the right .vmem file.

Ext.    | Name          | Type
--------|---------------|-------
.vmsn	|vmname.vmsn	|Virtual machine snapshot data file
.vmss	|vmname.vmss	|Virtual machine suspend file
.vmem	|vmware.vmem	|Virtual Machine volatile memory file

Now let's say we do a snapshot, you would need these two files. Note: Make sure you wait until the snapshot is 100% complete!!

- Windows Analyzze-Snapshot4.vmem
- Windows Analyzze-Snapshot4.vmsn

Download/copy these two files, verify integrity (hash, md5 or sha256). Idieally we only work on copies of acquired data, so make yourself another copy and do a check using volatility3 that everything works.

```
$ vol -f "Windows Analyzze-Snapshot6.vmem" windows.info.Info
```

For this I am using version 2.4.1 and simply on Ubuntu WSL2.

The result should look something like this:

```
Volatility 3 Framework 2.4.1
Progress:  100.00               PDB scanning finished
Variable        Value

Kernel Base     0xf80679200000
DTB     0x1ae000
Symbols file:///home/user/.local/lib/python3.10/site-packages/volatility3/symbols/windows/ntkrnlmp.pdb/6DE4B1C1DC23B687940A233637EF56DC-1.json.xz
Is64Bit True
IsPAE   False
layer_name      0 WindowsIntel32e
memory_layer    1 FileLayer
KdVersionBlock  0xf80679e09960
Major/Minor     15.22621
MachineType     34404
KeNumberProcessors      4
SystemTime      2023-09-05 06:27:55
NtSystemRoot    C:\Windows
NtProductType   NtProductWinNt
NtMajorVersion  10
NtMinorVersion  0
PE MajorOperatingSystemVersion  10
PE MinorOperatingSystemVersion  0
PE Machine      34404
PE TimeDateStamp        Sun Mar  1 16:04:41 2026
```

I have experienced that windows.info.Info works fine, but when I continue the investigation we see that the memory is smeared. What this means is that while the memory was being acquired, there has been changes to the memory that renders pages invalid.  

You might experience this message:

```
Volatility was unable to read a requested page:
Page error 0xa10 in layer layer_name (Page Fault at entry 0x0 in table page table)

        * Memory smear during acquisition (try re-acquiring if possible)
        * An intentionally invalid page lookup (operating system protection)
        * A bug in the plugin/volatility3 (re-run with -vvv and file a bug)

No further results will be produced
```

This doesn't ruin the investigation, but you should do a second attempt to preserve the memory, but save all attempts. This should be documented somewhere, so we know why there are mulitple versions of the same memory. 