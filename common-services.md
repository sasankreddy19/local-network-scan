# Common Services by Port

---

## Port 135/tcp - msrpc (Microsoft RPC)

- **Service**: Microsoft Remote Procedure Call (RPC)  
- **Description**:  
  Used for communication between processes on different systems, often in Windows environments for services like DCOM (Distributed Component Object Model) and Windows Management Instrumentation (WMI). It facilitates tasks such as remote administration and service coordination.  
- **Security Notes**:  
  Port 135 is often targeted by attackers due to its role in Windows RPC services. Vulnerabilities like those exploited by worms (e.g., Blaster) make it a high-risk port if exposed to the public internet. It’s recommended to restrict access to trusted networks.

---

## Port 139/tcp - netbios-ssn (NetBIOS Session Service)

- **Service**: NetBIOS over TCP/IP  
- **Description**:  
  Used for file and printer sharing in Windows environments, part of the NetBIOS protocol suite. It supports network communication for legacy Windows systems and applications.  
- **Security Notes**:  
  Port 139 is vulnerable to attacks like NTLM hash capture and brute-forcing credentials. It’s often associated with older, less secure implementations and should be disabled if not needed. Firewalls should limit access to this port.

---

## Port 445/tcp - microsoft-ds (Microsoft Directory Services)

- **Service**: Server Message Block (SMB)  
- **Description**:  
  Used for file and printer sharing in Windows environments. SMB is the modern protocol for sharing resources across a network, replacing older NetBIOS-based methods.  
- **Security Notes**:  
  Port 445 is notoriously vulnerable, notably exploited by the WannaCry ransomware in 2017 via the EternalBlue vulnerability in SMBv1. Ensure SMB versions are updated, and restrict access to trusted networks to mitigate risks.

---

## Port 902/tcp - iss-realsecure

- **Service**: VMware ESXi or ISS RealSecure  
- **Description**:  
  Commonly associated with VMware ESXi for communication with the VMware vSphere client or management tools. Alternatively, it may be used by ISS RealSecure, a network security monitoring tool by IBM.  
- **Security Notes**:  
  If running VMware, ensure the ESXi instance is patched. For ISS RealSecure, verify the service is legitimate. Limited public information exists on non-VMware uses, so investigate the service running on this port.

---

## Port 912/tcp - apex-mesh

- **Service**: APEX Mesh (VMware vSphere Replication)  
- **Description**:  
  Used by VMware vSphere for replication services, particularly in environments using VMware’s Site Recovery Manager or vSphere Replication for disaster recovery.  
- **Security Notes**:  
  Ensure proper authentication and network segmentation to prevent unauthorized access to replication data. Misconfiguration could expose sensitive virtual machine data.

---

## Port 1521/tcp - oracle

- **Service**: Oracle Database (SQLnet)  
- **Description**:  
  The default port for Oracle database communication, used by clients to connect to Oracle database servers for SQL queries and data management.  
- **Security Notes**:  
  Oracle databases can be targeted for unauthorized access. Ensure strong authentication, updated patches, and restricted network access.

---

## Port 3306/tcp - mysql

- **Service**: MySQL  
- **Description**:  
  The default port for MySQL database servers, used for client-server communication in MySQL-based applications.  
- **Security Notes**:  
  MySQL servers are common targets for brute-force attacks. Use strong passwords, enable encryption (e.g., TLS), and limit access to trusted IPs.

---

## Port 5432/tcp - postgresql

- **Service**: PostgreSQL  
- **Description**:  
  The default port for PostgreSQL database servers, used for client connections to manage and query PostgreSQL databases.  
- **Security Notes**:  
  Like MySQL, PostgreSQL is vulnerable to brute-force attacks. Implement strong authentication, use SSL/TLS, and restrict access.

---
