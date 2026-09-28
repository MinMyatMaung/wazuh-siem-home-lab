## Detection Scenario 2: Creating A New User Account

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
