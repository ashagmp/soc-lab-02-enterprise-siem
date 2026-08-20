# Splunk

## Overview

This document records the deployment and configuration of Splunk Enterprise for SOC Lab 02.

## Server

| Setting | Value |
|---------|-------|
| Hostname | splunk01 |
| IP Address | 192.168.10.40 |
| Installation Path | /opt/splunk |
| Web Interface | Port 8000 |

## Installation Status

Splunk Enterprise has been installed and verified on `splunk01`.

Splunk Web is accessible from the enterprise lab environment.

## Receiving Configuration

Splunk Enterprise is configured to receive data from Universal Forwarders.

| Setting | Value |
|---------|-------|
| Receiving Port | 9997 |
| Protocol | Splunk-to-Splunk |
| Server | splunk01 |
| IP Address | 192.168.10.40 |

The receiving port was verified with `ss` on `splunk01` and connectivity was tested from another lab machine.

Connectivity to port 9997 was successfully tested from the lab endpoints.

| Host     | Operating System    | Status |
| -------- | ------------------- | ------ |
| DC01     | Windows Server 2022 | Active |
| HR-PC01  | Windows 11 Pro      | Active |
| FIN-PC01 | Windows 11 Pro      | Active |
| web01    | Ubuntu Server       | Active |


The Universal Forwarders are configured to send data to:

192.168.10.40:9997

## Next Steps

- Configure Windows Event Log collection.
- Configure Linux log collection.
- Deploy Sysmon on Windows systems.
- Forward Sysmon events to Splunk.
- Verify centralized log ingestion.
- Create initial SOC monitoring dashboards.