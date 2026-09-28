## Scenario 3: Privileged Group Member Change

### Simulation

A test domain user, jilldoe, was added to the Domain Admins group in Active Directory. 
This simulated a privilege escalation scenario where a standard user is granted administrative permissions.

<img width="1716" height="936" alt="image" src="https://github.com/user-attachments/assets/eb02be92-4d05-4d2f-8573-0b9c822a4777" />

### Dectection & Investigation

Windows generated Event ID 4728, indicating that a member was added to a security-enabled global group. The event was first reviewed 
in Windows Event Viewer and then located in Wazuh Threat Hunting. The Wazuh event details confirmed the affected user, jilldoe, 
the target group, Domain Admins, the HOMELAB domain, and the originating Windows Server.

<img width="1177" height="832" alt="image" src="https://github.com/user-attachments/assets/90e11390-ebde-4caa-aa62-3ec8e202372d" />

## Results

Wazuh successfully detected and displayed the privileged group membership change. The event confirmed that jilldoe was added to the 
Domain Admins group, demonstrating that the SIEM can monitor sensitive Active Directory privilege changes.
