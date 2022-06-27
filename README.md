# Final-Final-Project--Cybersecurity
created Alerts on Kibana and attacked a machine and on the network
Ardavan Moghaddam
Final Project
Blue Team: Summary of Operations (Defensive)
Name of VM : ELK
Operating System: Ubuntu 18.04
Purpose: The ELK Stack
IP Address: 192.168.1.100
Name of VM : Kali
Operating System: Debian Kali 5.4.0
Purpose: The Penetration Tester
IP Address: 192.168.1.90
Name of VM : Target 1
Operating System: Debian GNU/Linux 8 Purpose: The WordPress Host
IP Address: 192.168.1.10
Description of Targets Target 1 (192.168.1.110) . Target 2 (192.168.1.115) optional.
Ports 80 and 22 are possible ports of entry for attackers. Monitoring the Targets
Configuring Alerts
Alert 1:
Excessive HTTP Errors
WHEN count() GROUPED OVER top 5 'http.response.status_code' IS ABOVE 400 FOR THE LAST 5 minutes
Selected the packetbeat indice
Metric: WHEN count() GROUPED OVER top 5 ‘http.response.status_code’
Threshold: IS ABOVE 400
Vulnerability Mitigated: Enumeration/Brute Force
Alert 2:
HTTP Request Size Monitor
Selected the packetbeat indice
Metric:
WHEN sum() of http.request.bytes OVER all documents IS ABOVE 3500 FOR THE LAST 1 minute
Threshold: ABOVE 3500
Vulnerability Mitigated: Code injection in HTTP requests (XSS and CRLF) or DDOS
Reliability: Alert could create false positives. There is a possibility for a large non malicious HTTP request or legitimate HTTP traffic.
Alert 3:
CPU Usage Monitor
Selected the metricbeat indice
Metric: WHEN max() OF system.process.cpu.total.pct OVER all documents
Threshold: ABOVE 0.5
Vulnerability Mitigated: Malicious software, programs (malware or viruses) running taking up resources.
Reliability: The alert is highly reliable. Even if there isn’t a malicious program running this can still help.
After created 3 Alerts:
