# SOC Lab 02 - Enterprise SIEM

## Overview

This project extends the enterprise infrastructure created in **SOC Lab 01 - Small Enterprise** by deploying a centralized Security Information and Event Management (SIEM) environment.

The objective is to collect, centralize, and analyze security telemetry from the Windows and Linux systems already deployed in the enterprise lab.

---

## Objective

Build a centralized enterprise SIEM environment using **Splunk Enterprise** to collect and analyze security telemetry from the Windows and Linux systems created in SOC Lab 01.

The lab focuses on:

- Deploying a dedicated Splunk Enterprise server.
- Deploying Splunk Universal Forwarders.
- Collecting Windows Event Logs.
- Deploying Sysmon for enhanced Windows telemetry.
- Collecting Linux security and system logs.
- Verifying centralized log ingestion.
- Creating initial SOC monitoring dashboards.

---

## Environment

| Hostname | Operating System | Role |
|----------|------------------|------|
| DC01 | Windows Server 2022 | Domain Controller / DNS / DHCP / Log Source |
| HR-PC01 | Windows 11 Pro | HR Workstation / Log Source |
| FIN-PC01 | Windows 11 Pro | Finance Workstation / Log Source |
| web01 | Ubuntu Server | Linux Web Server / Log Source |
| attack01 | Kali Linux | Security Testing Workstation |
| splunk01 | Ubuntu Server | Splunk Enterprise SIEM |

---

## SIEM Architecture

```text
                 Enterprise Infrastructure
                          │
             ┌────────────┴────────────┐
             │                         │
        Windows Systems            Linux Systems
             │                         │
       Event Logs + Sysmon        System/Auth Logs
             │                         │
             └────────────┬────────────┘
                          │
                Splunk Universal
                   Forwarders
                          │
                          ▼
                    ┌──────────┐
                    │ splunk01 │
                    │  Ubuntu  │
                    │  Splunk  │
                    └────┬─────┘
                         │
                         ▼
                  Splunk Enterprise
                         │
                         ▼
                SOC Monitoring
                   & Analysis
```

---

## Network

The SIEM environment uses the existing **AshagLab** internal network created in Lab 01.

```text
192.168.10.0/24
```

| Host | Internal IP | Role |
|------|-------------|------|
| DC01 | 192.168.10.10 | AD / DNS / DHCP |
| web01 | 192.168.10.20 | Linux Web Server |
| splunk01 | 192.168.10.40 | Splunk Enterprise |
| HR-PC01 | DHCP | Windows Endpoint |
| FIN-PC01 | DHCP | Windows Endpoint |
| attack01 | DHCP / Lab Network | Security Testing |

---

## Technologies

- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon
- Windows Event Logs
- Linux system logs
- Windows Server 2022
- Windows 11 Pro
- Ubuntu Server
- Kali Linux

---

## Implementation

### Phase 1 - SIEM Deployment

- [ ] Create `splunk01` virtual machine
- [ ] Install Ubuntu Server
- [ ] Configure hostname
- [ ] Configure network
- [ ] Configure static IP
- [ ] Install Splunk Enterprise
- [ ] Verify Splunk Web

### Phase 2 - Log Collection

- [ ] Install Universal Forwarder on DC01
- [ ] Install Universal Forwarder on HR-PC01
- [ ] Install Universal Forwarder on FIN-PC01
- [ ] Install Universal Forwarder on web01
- [ ] Configure Windows Event Log collection
- [ ] Configure Linux log collection
- [ ] Verify centralized log ingestion

### Phase 3 - Windows Telemetry

- [ ] Install Sysmon
- [ ] Configure Sysmon
- [ ] Forward Sysmon events to Splunk
- [ ] Verify Sysmon event ingestion

### Phase 4 - SOC Dashboards

- [ ] Failed login dashboard
- [ ] Successful login dashboard
- [ ] Account lockout dashboard
- [ ] PowerShell activity dashboard
- [ ] USB activity dashboard
- [ ] Windows security events dashboard
- [ ] Linux authentication events dashboard

---

## Repository Structure

```text
README.md
LICENSE
.gitignore

docs/
├── Installation.md
├── Splunk.md
└── Troubleshooting.md

diagrams/

screenshots/

configs/
```

---


## Project Status

**In Progress**

The current phase is deployment of the dedicated `splunk01` SIEM server.

---

## Documentation

Detailed implementation, configuration, and troubleshooting information is available in the `docs/` directory.

---

## License

This project is intended for educational and portfolio purposes.