## Scenario 1: Failed Login Attempts

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
