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

## Next Steps

- Install Universal Forwarders.
- Configure Windows log collection.
- Configure Linux log collection.
- Deploy Sysmon.
- Verify centralized log ingestion.
- Create SOC dashboards.