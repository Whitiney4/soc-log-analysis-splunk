# SOC Incident Investigation Report

## Incident title
Example: Suspected VPN brute-force attack followed by successful login

## Executive summary
Briefly describe what happened, the affected account or host, and why the activity is suspicious.

## Data sources reviewed
- Authentication logs
- Firewall logs
- Web access logs

## Timeline
| Time | Log source | Event | Analyst interpretation |
|---|---|---|---|
| | | | |

## Key evidence
Add Splunk screenshots and the SPL queries used to obtain the evidence.

## MITRE ATT&CK mapping
| Activity | Technique | Technique ID |
|---|---|---|
| Brute-force login attempts | Brute Force | T1110 |
| Valid account used after compromise | Valid Accounts | T1078 |
| Port scan | Network Service Scanning | T1046 |
| Possible exfiltration channel | Exfiltration Over C2 Channel | T1041 |

## Severity assessment
State the severity and explain your reasoning.

## Recommended response actions
1. Reset the affected account password and revoke active sessions.
2. Block malicious source IP addresses.
3. Review endpoint activity for the affected host.
4. Search for similar indicators across the environment.
5. Improve alerting thresholds and account protection controls.

## Lessons learned
Explain what monitoring improvements should be made.
