# DoS DoS DoS DoS DoS
I built this lab as part of CodePath’s CYB102 cybersecurity course to gain hands-on experience with Denial of Service (DoS) attacks and server-side mitigation. The goal was to simulate a Slowloris attack against an nginx web server and configure nginx with defensive rules to stop the attack. After completing this lab, I learned how to monitor real-time server traffic with nginx Amplify, deploy a Slowloris DoS attack, and configure nginx rules to mitigate DoS attacks.

## Tools & Technologies Used
- Ubuntu 22.04 LTS VM
- nginx (web server)
- Slowloris (DoS attack tool)
- nginx Amplify (cloud-based nginx monitoring platform)
- Wireshark (for analyzing .pcap network capture files)

## What This Lab Does
- Sets up nginx on a virtual machine and enables traffic monitoring through nginx Amplify.
- Simulates a Slowloris attack to flood the web server with slow, incomplete HTTP requests.
- Implements custom nginx configuration rules in /etc/nginx/conf.d/default.conf to mitigate DoS attacks.
- Verifies mitigation effectiveness by monitoring connection counts before and after applying the defenses.
- Analyzes provided .pcap files to distinguish between a vulnerable server and a mitigated server.

## Screenshots

### Creating a new file with the stub_status configuration
<img src="https://github.com/user-attachments/assets/f5949ada-48d6-41a4-8c72-a02d725ebd50" width="600"/>

### nginx Amplify dashboard showing pre-mitigation Slowloris attack: 
<img src="https://github.com/user-attachments/assets/e774ff05-0fa3-464b-ba9c-04374ec670e9" width="600"/>
<img src="https://github.com/user-attachments/assets/19e2251f-58b1-4187-8c41-41da3cc7d04e" width="600"/>

### nginx Amplify dashboard after mitigation rules are applied: 
<img src="https://github.com/user-attachments/assets/e8d798b4-ab70-4e20-8353-ebc4487022c1" width="600"/>
<img src="https://github.com/user-attachments/assets/8b523cb3-ece0-4721-9985-e362a79134ac" width="600"/>

### Custom nginx mitigation rules in default.conf:
<img src="https://github.com/user-attachments/assets/71624843-bb6b-44ec-844e-cbbac2ac6182" width="600"/>

### Wireshark analysis of vulnerable server (.pcap file comparison):
#### A.pcapng
<img src="https://github.com/user-attachments/assets/73b54859-9ca7-45de-a553-4c6120d1844f" width="600"/>

#### B.pcapng
<img src="https://github.com/user-attachments/assets/6d43307f-da79-4b44-91a5-6e75f4f02ef0" width="600"/>

#### Why is A.pcapng the vulnerable server?
I filtered by tcp.analysis.flags and saw many TCP RST packets where the server was actively closing slow or incomplete connections. This blocked the Slowloris attack. On the other hand, File B allowed the connections to remain open without closing them, showing it was the vulnerable server.
<img src="https://github.com/user-attachments/assets/be73bc77-5bb8-4771-8ead-9b91136b5bbc" width="600"/> 
