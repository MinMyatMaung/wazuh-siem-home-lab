# Wazuh SIEM Home Lab

## Overview

This project demonstrates a small Security Operations Center (SOC) lab using
Wazuh SIEM to monitor a Windows Active Directory environment.

The goal of the lab is to collect Windows security logs, generate simulated
security events, detect them in Wazuh, and investigate the resulting alerts.

## Lab Environment

- Wazuh SIEM
- Wazuh Agent
- Windows Server 2025
- Windows 11 Pro
- Active Directory Domain Services
- VMware Workstation

## Architecture

```text
Windows Server 2025
├── Active Directory Domain Services
├── Domain Controller
└── Wazuh Agent
          │
          ▼
      Wazuh SIEM
          ▲
          │
Windows 11 Pro
├── Domain-joined workstation
└── Wazuh Agent
```

## Wazuh Agent Deployment

I installed the Wazuh agent on both the Windows 11 workstation and the
Windows Server domain controller.

After enrollment, both endpoints appeared as active agents in the
Wazuh dashboard.

<img width="1692" height="596" alt="image" src="https://github.com/user-attachments/assets/b98e8a72-24de-4d34-a55d-1180e29d533c" />

## Skills Practiced

- SIEM monitoring
- Wazuh
- Windows Event Logs
- Active Directory
- Security event investigation
- Windows Event ID analysis
- Endpoint monitoring
- SOC alert triage
