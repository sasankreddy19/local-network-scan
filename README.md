# Network Scanning and Security Analysis

This README documents the process of performing a network scan using Nmap, analyzing the results, and identifying potential security risks associated with open ports. 
---

## Objective

The goal was to identify active devices on a local network, determine open ports, research the services running on those ports, and assess potential security risks. The results were saved for further analysis and documentation.

---

## Steps Performed

### 1. Install Nmap

- **Action:** Downloaded and installed Nmap version 7.97 from the official website ([https://nmap.org](https://nmap.org)).
- **Details:** The installation was completed on a Windows system, ensuring the latest version was used for accurate scanning capabilities.

### 2. Find Local IP Range

- **Action:** Determined the local IP range of the network.
- **Details:** The local network was identified as using the IP range `192.168.0.0/24` (subnet mask `255.255.255.0`). This was confirmed using the `ipconfig` command on Windows, which showed the local machine’s IP address as `192.168.0.x`.

### 3. Run Nmap TCP SYN Scan

- **Action:** Executed the command:
  ```bash
  nmap -sS 192.168.0.0/24
### 4. Note IP Addresses and Open Ports

**Action:** Recorded the scan results, focusing on active hosts and their open ports.

**Details:** The scan identified one active host at `192.168.0.114` with the following open ports:

- `135/tcp` (msrpc)
- `139/tcp` (netbios-ssn)
- `445/tcp` (microsoft-ds)
- `902/tcp` (iss-realsecure)
- `912/tcp` (apex-mesh)
- `1521/tcp` (oracle)
- `3306/tcp` (mysql)
- `5432/tcp` (postgresql)
  
**Additional Notes:**  
991 other TCP ports were closed (reset). The scan completed in **0.95 seconds** with a latency of **0.00059s** for the host.

---

### 5. Analyze Packet Capture with Wireshark (Optional)

**Action:** Optionally captured network traffic during the scan using Wireshark for deeper analysis.

**Details:**  
Wireshark was used to monitor **TCP** and **TLSv1.2** traffic between the scanning host and `192.168.0.114`. The capture confirmed communication on ports like `443` and `60811`, indicating active TCP connections and **TLS-encrypted application data**. This step helped validate the scan results but was **not mandatory**.

---

### 6. Research Common Services

**Action:** Researched the services typically associated with the identified open ports.

**Details:** The following services were identified based on standard port assignments and networking conventions:

- `135/tcp` - **msrpc**: Microsoft Remote Procedure Call (RPC) for inter-process communication in Windows (e.g., DCOM, WMI).
- `139/tcp` - **netbios-ssn**: NetBIOS over TCP/IP for legacy Windows file and printer sharing.
- `445/tcp` - **microsoft-ds**: Server Message Block (SMB) for modern Windows file and printer sharing.
- `902/tcp` - **iss-realsecure**: Likely VMware ESXi for vSphere client communication or IBM ISS RealSecure.
- `912/tcp` - **apex-mesh**: VMware vSphere Replication for disaster recovery.
- `1521/tcp` - **oracle**: Oracle Database (SQLnet) for client-server database communication.
- `3306/tcp` - **mysql**: MySQL database server for client connections.
- `5432/tcp` - **postgresql**: PostgreSQL database server for client connections.
- `55555/tcp` - **unknown**: Non-standard port, potentially used by custom applications or malware.

---

### 7. Identify Potential Security Risks

**Action:** Assessed the security risks associated with each open port.

**Details:**

- `135/tcp` (**msrpc**): **High risk** due to historical exploits (e.g., Blaster worm). Vulnerable to remote code execution and information disclosure if exposed.
- `139/tcp` (**netbios-ssn**): **High risk** due to NTLM hash capture and brute-force attacks. Outdated protocol with weak security.
- `445/tcp` (**microsoft-ds**): **Critical risk** due to exploits like EternalBlue (WannaCry). Prone to ransomware and unauthorized access.
- `902/tcp` (**iss-realsecure**): **Moderate to high risk** if VMware ESXi is unpatched or exposed, as management interfaces can be targeted.
- `912/tcp` (**apex-mesh**): **Moderate to high risk** in VMware environments due to potential data exposure in replication services.
- `1521/tcp` (**oracle**): **High risk** if misconfigured. Vulnerable to SQL injection, brute-force attacks, or data breaches.
- `3306/tcp` (**mysql**): **High risk** due to brute-force attacks and potential data exposure if unencrypted or poorly configured.
- `5432/tcp` (**postgresql**): **High risk**, similar to MySQL, with vulnerabilities to brute-forcing and data breaches.
- `55555/tcp` (**unknown**): **Critical risk** due to its non-standard nature, potentially indicating malware or misconfigured services. Requires immediate investigation.
