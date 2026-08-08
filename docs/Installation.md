# Installation

## Overview

This document records the installation and configuration of the systems used in SOC Lab 02 - Enterprise SIEM.

## Environment

| Hostname | Operating System | Role |
|----------|------------------|------|
| DC01 | Windows Server 2022 | Domain Controller / DNS / DHCP |
| HR-PC01 | Windows 11 Pro | HR Workstation / Log Source |
| FIN-PC01 | Windows 11 Pro | Finance Workstation / Log Source |
| web01 | Ubuntu Server | Linux Web Server / Log Source |
| attack01 | Kali Linux | Security Testing Workstation |
| splunk01 | Ubuntu Server | Splunk Enterprise SIEM |

## Planned Installation

- [ ] Install Splunk Enterprise.
- [ ] Verify Splunk Web.

## completed Installation

- Installed Ubuntu Server on `splunk01`.
- Configured the hostname as `splunk01`.
- Configured the static internal IP address `192.168.10.40`.
- Configured DC01 (`192.168.10.10`) as the DNS server.
- Verified connectivity between `splunk01` and DC01.
- Verified DNS resolution for `dc01.ashag.local`.
- Verified Internet connectivity.

## Notes

- `DC01` remains dedicated to Active Directory, DNS, and DHCP.
- `web01` remains the Linux web server and will be used as a Linux log source.
- `splunk01` is a dedicated SIEM server.