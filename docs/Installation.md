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

- [ ] Create `splunk01` virtual machine.
- [ ] Install Ubuntu Server.
- [ ] Configure hostname.
- [ ] Configure network connectivity.
- [ ] Configure static IP address.
- [ ] Install Splunk Enterprise.
- [ ] Verify Splunk Web.

## Notes

- `DC01` remains dedicated to Active Directory, DNS, and DHCP.
- `web01` remains the Linux web server and will be used as a Linux log source.
- `splunk01` is a dedicated SIEM server.