# ⚠️ Risks Caused by Open Ports

This document outlines the risks associated with several commonly open TCP ports and the vulnerabilities they expose.

---

## ⚙️ Port 135/tcp — Microsoft RPC

**Risks:**
- **Remote Code Execution (RCE):** Exploited by worms like *Blaster* and *Sasser*.
- **Unauthorized Access:** Targets Windows services like DCOM and WMI.
- **Information Disclosure:** Endpoint mapping may reveal system details.

**Severity:** 🔴 **High** — Commonly exploited in Windows environments.

---

## 📎 Port 139/tcp — NetBIOS Session Service

**Risks:**
- **NTLM Hash Capture:** For offline cracking or pass-the-hash attacks.
- **Brute-Force Attacks:** Targets file and printer sharing.
- **Legacy Protocol Weaknesses:** Lacks encryption and modern security.

**Severity:** 🔴 **High** — Especially risky in legacy networks.

---

## 📁 Port 445/tcp — SMB (Microsoft-DS)

**Risks:**
- **Ransomware (EternalBlue):** Used in *WannaCry* and *NotPetya*.
- **Unauthorized File Access:** Due to misconfigured shares.
- **DoS Attacks:** Potential system crash or service disruption.

**Severity:** 🔴 **Critical** — Must not be exposed to the public internet.

---

## 🖥️ Port 902/tcp — VMware ESXi / ISS RealSecure

**Risks:**
- **Management Interface Exploitation:** Risk of brute-force or RCE.
- **Data Exposure:** VM configurations may be visible.
- **Unknown Software:** Could be a backdoor if non-VMware.

**Severity:** 🟠 **Moderate to High** — Secure carefully if in use.

---

## 📡 Port 912/tcp — VMware vSphere Replication (APEX Mesh)

**Risks:**
- **Replication Data Exposure:** Risk of leaking sensitive VM data.
- **Unauthorized Access:** Poor authentication allows manipulation.
- **Disaster Recovery Disruption:** May affect business continuity.

**Severity:** 🟠 **Moderate to High** — Relevant for DR infrastructure.

---

## 🧠 Port 1521/tcp — Oracle SQL*Net

**Risks:**
- **SQL Injection / Brute-Force:** Common attack vector.
- **Data Breach:** Poor permissions or public exposure.
- **Remote Code Execution:** In outdated Oracle installations.

**Severity:** 🔴 **High** — Critical for data security.

---

## 🐬 Port 3306/tcp — MySQL

**Risks:**
- **Brute-Force Attacks:** Especially with default or weak credentials.
- **Unencrypted Traffic:** Susceptible to sniffing.
- **SQL Injection:** Via vulnerable web applications.

**Severity:** 🔴 **High** — Protect with firewall and strong auth.

---

## 🐘 Port 5432/tcp — PostgreSQL

**Risks:**
- **Brute-Force Attacks:** Weak authentication is a major issue.
- **Data Leakage:** Misc
