# Wazuh SIEM Home Lab

## Overview

This project demonstrates a small Security Operations Center (SOC) lab using
Wazuh SIEM to monitor a Windows Active Directory environment.

The goal of the lab is to collect Windows security logs, generate simulated
security events, detect them in Wazuh, and investigate the resulting alerts.

## Lab Environment

- Wazuh SIEM
- Windows Server 2025
- Active Directory Domain Services
- Windows 11 Pro
- VMware Workstation
- Wazuh Agent

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

## Detection Scenario 1: Failed Login Attempts

### Simulation

I intentionally entered an incorrect password several times for a domain
account on the Windows 11 workstation.

### Detection

Wazuh detected four authentication failures.

<img width="1703" height="797" alt="image" src="https://github.com/user-attachments/assets/6096b462-410a-4c62-808b-55ec66671ebf" />

### Investigation

The Windows security event showed:

- Event ID: 4625
- Wazuh Rule ID: 60122
- Rule Level: 5
- Logon Type: 2
- Status: 0xC000006D
- Workstation: COMPUTER01
- Security Channel: Security

Event ID 4625 represents a failed Windows logon.

Logon Type 2 indicates an interactive login attempt, such as a user trying
to sign in directly from the Windows login screen.

The status code indicated invalid authentication credentials.

<img width="790" height="817" alt="image" src="https://github.com/user-attachments/assets/ee22e4c3-1d4d-467e-a275-9f6682803a6f" />

## Result

Wazuh successfully collected and detected the failed Windows authentication
events. I was able to investigate the affected account, workstation, event
type, login method, and authentication failure information.


## Detection Scenario 2: Creating a new user account

### Simulation

A test domain user named `Jill Doe` was created in Active Directory.

Windows generated Security Event ID `4720`, which indicates that a new user
account was created.

<img width="1717" height="936" alt="image" src="https://github.com/user-attachments/assets/947e27c9-b9f3-48d8-9eff-b320a4d443d8" />

### Dectection & Investigation

The Wazuh agent collected the Windows Security event and forwarded it to the
Wazuh manager.

<img width="1710" height="867" alt="image" src="https://github.com/user-attachments/assets/3094bf3a-da97-4b33-bbe5-2469eb1fa1e3" />

## Result

Wazuh successfully detected the event and displayed:

- Event ID: 4720
- Target user: jilldoe
- Domain: HOMELAB
- Host: FileServer01
- Event message: A user account was created

## Skills Practiced

- SIEM monitoring
- Wazuh
- Windows Event Logs
- Active Directory
- Security event investigation
- Windows Event ID analysis
- Endpoint monitoring
- SOC alert triage
