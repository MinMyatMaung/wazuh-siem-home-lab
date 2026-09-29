## Scenario 4: User Account Deletion

### Simulation

A test domain account, `jilldoe`, was deleted from Active Directory to simulate an account removal event.

### Detection & Investigation

Windows generated **Event ID 4726**, indicating that a user account was deleted. The event was reviewed in Windows Event Viewer and then 
located in Wazuh Threat Hunting.

<img width="1711" height="937" alt="image" src="https://github.com/user-attachments/assets/a1ace92b-4102-40ed-8277-a52439d5a328" />

The event details were investigated to confirm:

- Deleted user: `jilldoe`
- Domain: `HOMELAB`
- Event ID: `4726`
- Source system: Windows Server Domain Controller

### Results

Wazuh successfully detected and displayed the account deletion event. The event confirmed that `jilldoe` was removed from the `HOMELAB` domain, 
demonstrating that the SIEM can monitor Active Directory account lifecycle activity.

<img width="1707" height="825" alt="image" src="https://github.com/user-attachments/assets/2a60d5b0-ec21-4e0e-a510-c6113ffa0c87" />

