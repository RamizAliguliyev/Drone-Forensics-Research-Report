# 🚁 Drone Forensics Research Report (COM6016)

## Overview

This repository hosts the final, compiled PDF of an academic research report submitted for the module **COM6016: Cyber Threat Hunting and Digital Forensics** at The University of Sheffield.

The report provides a detailed analysis of the discipline of **Drone Forensics (Unmanned Aerial Vehicle Forensics)**, covering the current state of the field, major challenges faced by investigators, and the necessary technical and procedural solutions for successful digital evidence acquisition.

## Repository Contents

The primary deliverable is the compiled report PDF:

| File Name | Description |
| :--- | :--- |
| `[Drone-Forensics.pdf].pdf` | The full, final research report on Drone Forensics. |
| `README.md` | This overview file. |

***

## Key Topics Covered in the Report

The research addresses the core areas of drone investigation as required for the assignment:

1.  **Drone Forensics Definition and Importance:** Explaining what drone forensics involves and why it is critical for modern digital security, law enforcement, and national security.
2.  **Forensic Tooling:** A detailed description and categorization of tools used, including:
    * **Commercial Suites:** Tools like Cellebrite UFED and Magnet AXIOM.
    * **Specialized Open-Source Tools:** Utilities such as DatCon (for proprietary DJI logs), ExifTool, and Binwalk.
3.  **Significant Challenges:** Describing and justifying major obstacles:
    * **Lack of Vendor Standardization** (proprietary hardware/software).
    * **Evidence Volatility** and **Anti-Forensic Capabilities** (remote wipeout, volatile memory).
4.  **Solutions in Practice:** Practical methods to address these challenges:
    * **First Responder Protocols:** Immediate steps to preserve evidence (network isolation, maintaining power).
    * **Reverse Engineering** and the use of specialized parsers to decrypt proprietary data (e.g., DJI's `.DAT` files).
5.  **Locations of Interest:** Identifying crucial sources of evidence if a drone is hacked remotely (UAV firmware, flight controller logs, mobile terminal devices, and external cloud servers).

***
*Authored by Ramiz Aliguliyev, The University of Sheffield (November 2025).*
