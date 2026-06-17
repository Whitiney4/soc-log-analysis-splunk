\# Incident Report: Suspected Brute-Force Attack and Suspicious Network Activity



\## 1. Executive Summary



This report documents a small SOC investigation using Splunk. The investigation reviewed authentication logs, firewall logs and web access logs from a simulated environment. The main finding was a suspected brute-force attack against the `admin` account, followed by one successful login from the same source IP address.



Additional suspicious activity was also identified, including port scanning, unusual outbound traffic and suspicious web access attempts. These findings suggest possible reconnaissance, credential attack activity and potential command-and-control or data exfiltration behaviour.



\## 2. Data Sources Reviewed



The investigation used three log sources:



\- `auth\_logs.csv`: VPN authentication events, including successful and failed login attempts.

\- `firewall\_logs.csv`: Firewall events, including allowed and blocked network connections.

\- `web\_access\_logs.csv`: Web server access events, including normal and suspicious web requests.



\## 3. Key Findings



\### Finding 1: Multiple Failed Login Attempts



The source IP address `203.0.113.50` generated 18 failed login attempts against the `admin` account. This pattern may indicate password guessing or brute-force activity.



MITRE ATT\&CK mapping:



\- Brute Force - T1110



\### Finding 2: Successful Login After Failed Attempts



The same source IP address `203.0.113.50` also recorded 1 successful login after the failed attempts. This is more serious because it may indicate that the attacker successfully accessed the account.



MITRE ATT\&CK mapping:



\- Brute Force - T1110

\- Valid Accounts - T1078



\### Finding 3: Port Scan Activity



The source IP address `198.51.100.23` attempted to connect to 15 different ports on the internal host `10.0.0.10`. This suggests possible network reconnaissance or port scanning.



MITRE ATT\&CK mapping:



\- Network Service Scanning - T1046



\### Finding 4: Unusual Outbound Connection



The internal host `10.0.0.31` sent 2.50 MB of outbound traffic to the external IP address `192.0.2.99` over destination port `4444`. This is suspicious because it involves a high-volume outbound connection to an uncommon port.



MITRE ATT\&CK mapping:



\- Exfiltration Over C2 Channel - T1041



\### Finding 5: Suspicious Web Access Pattern



The source IP address `203.0.113.88` sent multiple suspicious web requests, including access attempts to `/admin`, `/wp-login.php`, `/.env`, and `/../../etc/passwd`. It also attempted SQL injection-style requests such as `OR '1'='1` and `UNION SELECT`.



MITRE ATT\&CK mapping:



\- Active Scanning - T1595

\- Exploit Public-Facing Application - T1190



\## 4. Incident Timeline



| Time | Event | Source |

|---|---|---|

| 2026-06-01 10:00 - 10:34 | Multiple failed login attempts against `admin` | Authentication logs |

| 2026-06-01 10:40 | Successful login from the same source IP | Authentication logs |

| 2026-06-01 11:00 - 11:14 | Port scanning against internal host `10.0.0.10` | Firewall logs |

| 2026-06-01 12:00 - 12:12 | Suspicious web access attempts | Web access logs |

| 2026-06-01 14:00 - 14:21 | Unusual outbound connection from `10.0.0.31` | Firewall logs |



\## 5. Severity Assessment



The overall severity is assessed as \*\*Medium to High\*\*.



The authentication activity is the most serious finding because a successful login occurred after multiple failed login attempts. This may indicate account compromise. The port scan and suspicious web requests also show reconnaissance activity, while the unusual outbound connection may indicate possible command-and-control or data exfiltration behaviour.



\## 6. Recommended Response Actions



The security team should take the following actions:



1\. Reset the password of the affected `admin` account.

2\. Revoke active sessions associated with the account.

3\. Enable multi-factor authentication for privileged accounts.

4\. Block or monitor the suspicious source IP addresses.

5\. Investigate the internal host `10.0.0.31` for suspicious processes or malware.

6\. Review web server logs to confirm whether any suspicious request succeeded.

7\. Create Splunk alerts for repeated failed logins, port scanning and unusual outbound traffic.



\## 7. Lessons Learned



This investigation shows the value of combining multiple log sources in Splunk. Authentication logs helped identify possible credential attacks. Firewall logs helped identify port scanning and unusual outbound communication. Web access logs helped identify suspicious access attempts.



For future improvement, the organisation should enable stronger authentication controls, improve alerting rules, and regularly review network and web access logs.

