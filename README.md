\# SOC Log Analysis Project Using Splunk



\## Project Overview



This project is a beginner-friendly SOC log analysis project using Splunk.



The purpose of this project is to practise basic SOC analyst skills, including log ingestion, SPL searching, detection use case development, dashboard creation and incident reporting.



The project uses simulated authentication logs, firewall logs and web access logs. The logs include both normal activity and suspicious security events.



The investigation focuses on identifying:



\* Brute-force login activity

\* Successful login after repeated failed attempts

\* Port scanning

\* Unusual outbound network traffic

\* Suspicious web access patterns



\## Tools Used



\* Splunk Enterprise

\* SPL Search Processing Language

\* CSV log files

\* MITRE ATT\&CK Framework

\* Markdown documentation



\## Data Sources



| Log File              | Description                                                             |

| --------------------- | ----------------------------------------------------------------------- |

| `auth\_logs.csv`       | VPN authentication logs, including successful and failed login attempts |

| `firewall\_logs.csv`   | Firewall traffic logs, including allowed and blocked connections        |

| `web\_access\_logs.csv` | Web access logs, including normal and suspicious web requests           |



\## Detection Use Cases



This project includes five detection use cases:



1\. Multiple failed login attempts from one IP

2\. Successful login after several failed attempts

3\. Port scan detection

4\. Unusual outbound connection

5\. Suspicious web access pattern



The full detection write-up is available here:



\[detection\_use\_cases.md](detection\_use\_cases.md)



\## Key Findings



The Splunk analysis identified several suspicious activities:



\* The source IP address `203.0.113.50` generated 18 failed login attempts against the `admin` account.

\* The same source IP later recorded 1 successful login, which may indicate a successful brute-force attack.

\* The source IP address `198.51.100.23` scanned 15 different ports on the internal host `10.0.0.10`.

\* The internal host `10.0.0.31` sent 2.50 MB of outbound traffic to `192.0.2.99` over destination port `4444`.

\* The source IP address `203.0.113.88` sent suspicious web requests, including attempts to access `/admin`, `/wp-login.php`, `/.env`, `/../../etc/passwd`, and SQL injection-style URLs.



\## Dashboard



A simple Splunk dashboard was created to show the main SOC findings.



The dashboard includes:



\* Failed logins by source IP

\* Successful login after failed attempts

\* Port scan detection

\* Unusual outbound connection

\* Suspicious web access pattern



Dashboard screenshots:



!\[Dashboard overview 1](screenshots/dashboard-overview1.png)



!\[Dashboard overview 2](screenshots/dashboard-overview2.png)



\## Screenshots



Screenshots of the Splunk searches and dashboard are stored in the `screenshots` folder.



Screenshot list:



\* `dashboard-overview1.png`

\* `dashboard-overview2.png`

\* `brute-force-failed-logins.png`

\* `successful-login-after-failures.png`

\* `port-scan-detection.png`

\* `unusual-outbound-connection.png`

\* `suspicious-web-access-pattern.png`



\## Incident Report



A short incident report was prepared to summarise the investigation findings, severity assessment and recommended response actions.



The report is available here:



\[reports/incident\_report.md](reports/incident\_report.md)



\## MITRE ATT\&CK Mapping



| Activity                               | MITRE ATT\&CK Technique               |

| -------------------------------------- | ------------------------------------ |

| Multiple failed login attempts         | Brute Force - T1110                  |

| Successful login after failed attempts | Valid Accounts - T1078               |

| Port scanning                          | Network Service Scanning - T1046     |

| Unusual outbound traffic               | Exfiltration Over C2 Channel - T1041 |

| Suspicious web requests                | Active Scanning - T1595              |



\## Project Outcome



This project demonstrates basic SOC analyst skills, including:



\* Importing log files into Splunk

\* Searching and filtering security events

\* Writing SPL detection queries

\* Identifying suspicious authentication, firewall and web activity

\* Creating a basic Splunk dashboard

\* Mapping findings to MITRE ATT\&CK

\* Preparing a simple incident investigation report



\## Repository Structure



soc-log-analysis-splunk/



\* README.md

\* detection\_use\_cases.md

\* data/



&#x20; \* auth\_logs.csv

&#x20; \* firewall\_logs.csv

&#x20; \* web\_access\_logs.csv

\* screenshots/



&#x20; \* dashboard-overview1.png

&#x20; \* dashboard-overview2.png

&#x20; \* brute-force-failed-logins.png

&#x20; \* successful-login-after-failures.png

&#x20; \* port-scan-detection.png

&#x20; \* unusual-outbound-connection.png

&#x20; \* suspicious-web-access-pattern.png

\* reports/



&#x20; \* incident\_report.md

&#x20; \* incident\_report\_template.md

\* spl\_queries/



&#x20; \* soc\_detection\_queries.spl



\## Notes



This is a simulated training project. The log files and IP addresses are created for learning purposes only and do not contain real user or company data.



This project is designed as a beginner SOC portfolio project. It focuses on clear detection logic, simple investigation steps and readable documentation rather than complex enterprise-level deployment.

