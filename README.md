# Digital Forensics & Incident Response: Case Studies

Two reports from **COM6016 Cyber Threat Hunting and Digital Forensics** at the University of Sheffield (2025):

1. **Forensics Case Study:** a hands-on investigation covering disk image forensics, incident response from security logs, and network packet analysis
2. **Research on Drone Forensics:** a literature-based study of tools, challenges and evidence collection for UAV investigations

---

## 1. Forensics Case Study

A three-part practical investigation into a simulated insider threat and a related security incident.

### Task 1: Disk Image Investigation

An investigation of a Product Manager's workstation disk image, using **Autopsy**, to find out whether sensitive data was being leaked outside the company.

**Key findings**

- **Suspicious personal files:** meeting "minutes" files with names, dates and payment amounts that had no place on a product-management workstation
- **Password notes:** a recently opened `Shake.odt` document, found through its `.lnk` shortcut, held what looked like a list of passwords and hints, including the hint `cesar 6`
- **Hidden archives:** a corrupted `formule.7z` archive and a `Minutes.7z` archive holding more sensitive meeting records
- **Covert communication:** use of an external encrypted mail service (Tutanota) and a personal Gmail account to send messages outside company channels. One email was disguised as a "cake recipe", and applying a **Caesar cipher with shift 6** to its subject line linked it to the hidden archive.

**Conclusion:** the evidence shows sensitive data being deliberately collected, hidden and protected, not stored by accident.

### Task 2: Incident Response Analysis

Correlated **firewall logs, web application logs and SIEM alerts** from a single day to reconstruct a multi-stage attack.

- Identified **Indicators of Attack (IOAs):** high-rate blocked inbound requests, SSH brute-forcing, SYN flood alerts, suspicious outbound connections, repeated failed logins followed by success, and a ~1 GB customer-data export
- **Prioritised alerts:** credential misuse leading to data exfiltration was ranked the most dangerous, because it damages confidentiality and slips past signature-based detection
- Proposed a **containment → eradication → recovery → lessons learned** response plan, plus the first three actions for the morning response
- Showed that both event sets belong to **one attack chain:** external reconnaissance and brute force led to compromised credentials, then unauthorised access and data exfiltration

| Time | Event |
|------|-------|
| 01:12–01:13 | Sustained blocked inbound requests (scanning / DoS) |
| 01:15 | Multiple failed SSH logins |
| 02:30 | Unusual outbound traffic from an internal host |
| 03:15 | SYN flood alert on an internal system |
| 19:00–19:20 | Failed logins from a known malicious IP |
| 19:20–19:30 | Successful login followed by large data export |

### Task 3: Network Forensics Analysis

A packet capture analysed in **Wireshark**.

- Found a large number of **TCP SYN packets** from a single source, with no completed three-way handshakes and many retransmissions
- Uniform packet structure (same sequence pattern, window size and MSS) with no payload pointed to **automated tooling**, not real application traffic
- **Conclusion:** a **TCP SYN port scan**, i.e. reconnaissance in the early stage of the intrusion lifecycle, rather than a DoS attack

---

## 2. Research on Drone Forensics

A research report on how investigators acquire and analyse digital evidence from UAVs (drones) used in crimes such as smuggling contraband into prisons or flying near airports.

**Contents**

- **Tools**
  - Commercial suites: Cellebrite UFED, Magnet AXIOM
  - Open-source and free tools: Autopsy, DatCon (DJI `.DAT` flight logs), ExifTool (GPS metadata in photos), Binwalk (firmware analysis)
  - DJI Mini 2 case study showing why a multi-tool approach is needed
- **Challenges**
  - No standard file systems or formats across vendors
  - Volatile evidence that is lost when the battery dies
  - Anti-forensic features such as remote wipe
- **Solutions**
  - Isolate the drone from wireless networks and keep it powered
  - Use Telnet access to browse system files
  - Reverse-engineer encrypted logs (XOR-encrypted DJI `.DAT` payloads, the DRDP parser)
- **Evidence locations after a remote hack:** UAV firmware, the onboard flight controller, the paired mobile device, and external or cloud servers

---

## Repository Structure

```
├── <forensics-case-study>.pdf   # Disk, incident response & network forensics investigation
├── <drone-forensics>.pdf        # Research report on UAV forensics
└── README.md
```

## Tools & Techniques

**Autopsy** · **Wireshark** · **SIEM log analysis** · **Caesar cipher analysis** · **7-Zip archive analysis** · **Incident response lifecycle (NIST)** · **Indicators of Attack** · **Cellebrite UFED** · **Magnet AXIOM** · **DatCon** · **ExifTool** · **Binwalk**

## Note

All scenarios, people, organisations and data in the case study are **fictional** and were provided as part of the coursework.

## Author

**Ramiz Aliguliyev**, University of Sheffield
