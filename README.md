This repository contains a poc for CVE-2023-23388, which is described in [this series](https://ynwarcs.github.io/z-btadv-cves), particularly in [this post](https://ynwarcs.github.io/v-cve-2023-23388). It's an LPE in the bluetooth service (aka **bthserv**) in Windows 10/11 that allows an unprivileged user to escalate to LOCAL SERVICE. This repo doesn't contain an exploit, only a poc.

## building, running, etc.

**Use a VM. This could be a virus.**

MS fixed the vulnerability in March 2023 security update so you'll need to target a system that doesn't have that applied. You could also dirty patch the fix for testing, it shouldn't be too hard once you read the post. The system also needs bluetooth to be turned on, as the service may not run otherwise or may discard RPC requests. To compile the poc, open up the solution in VS 2022 and build it either in Debug or Release. Then run **poc.exe** with no arguments. It will trigger the vulnerability with `EventType=-0x50C`. There's no particular reason I chose that value, it just showcased the behaviour nicely since it guaranteed a crash.