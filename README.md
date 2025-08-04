
Task 1: Local Network Port Scan – Cyber Security Internship

 Objective
To learn and demonstrate basic network reconnaissance skills by scanning the local network for live hosts and open ports using **Nmap**, and understanding the potential security exposur

 Tools Used
[Nmap](https://nmap.org/) – for performing a TCP SYN scan
[Wireshark](https://www.wireshark.org/) (Optional) – for capturing and analyzing packets

---

 Network Details
- Local IP Range Scanned**: `192.168.1.0/24`
- Scanning Method**: TCP SYN scan (`nmap -sS`)
- Devices Found**: 3 live hosts

---

 Scan Results

 Host: `192.168.1.1` (ZTE Router)
- Open Ports:
  - `53/tcp` – DNS
  - `80/tcp` – HTTP
  - `443/tcp` – HTTPS
- Filtered Port:
  - `23/tcp` – Telnet *(filtered, possible security concern)*

 Host: `192.168.1.3`  
- All ports closed (reset)** – No open TCP ports found.

Host: `192.168.1.5` (Likely Windows machine)
- Open Ports:
  - `135/tcp` – MSRPC
  - `139/tcp` – NetBIOS Session Service
  - `445/tcp` – Microsoft-DS (SMB file sharing)
  - `902/tcp` – ISS RealSecure
  - `912/tcp` – Apex Mesh
  - `2869/tcp` – ICSLAP (Internet Connection Sharing)

---

 Security Risk Analysis

| IP Address   | Port | Service     | Risk Summary                                               | Recommendation                     |
|--------------|------|-------------|------------------------------------------------------------|------------------------------------|
| 192.168.1.1  | 23   | Telnet      | Insecure, unencrypted protocol (filtered)                 | Disable Telnet if not used         |
|              | 80   | HTTP        | Unencrypted traffic                                        | Use HTTPS instead                  |
|              | 53   | DNS         | DNS open to local access                                   | Acceptable in router context       |
| 192.168.1.5  | 135   | MSRPC       | Commonly targeted on Windows networks                      | Restrict access or firewall        |
|              | 139   | NetBIOS     | Vulnerable to SMB-related attacks                          | Disable NetBIOS if not needed      |
|              | 445   | SMB         | Exploitable via EternalBlue, WannaCry, etc.                | Block/disable or isolate network   |
|              | 902   | ISS         | Intrusion detection port, could reveal info to attacker    | Close unless specifically needed   |
|              | 2869  | ICSLAP      | UPnP-related service, often misused                        | Disable UPnP on LAN unless needed  |

---

 Steps Performed

1. Identified IP range using `ipconfig`.
2. Installed Nmap and ran scan:
   ```bash
   nmap -sS 192.168.1.0/24 -oX scan_result.xml
   ```
3. Parsed and analyzed the results using XML output.
4. Mapped services and performed security risk analysis.

---

Key Learnings

- Learned how to use Nmap to discover live hosts and open ports.
- Understood how services running on open ports can present attack vectors.
- Learned how to interpret filtered, open, and closed port states.
- Understood basics of LAN reconnaissance and port security.

---

Files Included
- `scan_result.xml` – Raw Nmap XML output
- `README.md` – This file

---

 Submission
- **GitHub Repository:(https://github.com/HariHaran2112003/task1-network-scan.git)]
- Submission Form: [https://forms.gle/8Gm83s53KbyXs3Ne9](https://forms.gle/8Gm83s53KbyXs3Ne9)

---

> Task completed as part of Cyber Security Internship for practicing vulnerability assessment and network scanning techniques.
