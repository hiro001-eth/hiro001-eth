<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0d1117&height=220&section=header&text=Manjil%20Katuwal&fontSize=56&fontColor=7DF0B7&fontAlignY=40&desc=Security%20Engineer%20%E2%80%94%20I%20Build%20The%20Tools%20Most%20SOCs%20Buy&descAlignY=63&descSize=18&descColor=8b949e&animation=fadeIn&stroke=7DF0B7&strokeWidth=1" width="100%" />

<br/>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=15&duration=3200&pause=1400&color=7DF0B7&center=true&vCenter=true&width=680&lines=6+Production+Security+Platforms.+Shipped.+Open+Source.;Detection+Engineering+%C2%B7+GRC+%C2%B7+Threat+Intel+%C2%B7+NDR+%C2%B7+FIM;TryHackMe+Top+1%25+%E2%80%94+8+Certifications+%E2%80%94+Zero+To+SOC+L2+in+21+Months;VALENCE+%C2%B7+SENTINEL+%C2%B7+ARGUS+%C2%B7+RTD-MTA+%C2%B7+CERBERUS+%C2%B7+FIM" />

<br/>

[![Portfolio](https://img.shields.io/badge/Portfolio-manjilkatuwal.com.np-7DF0B7?style=flat-square&logo=google-chrome&logoColor=0d1117)](https://manjilkatuwal.com.np/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Manjil%20Katuwal-7DF0B7?style=flat-square&logo=linkedin&logoColor=0d1117)](https://linkedin.com/in/manjil-katuwal-5b39212b0)
[![Topmate](https://img.shields.io/badge/Topmate-Book%20a%20Mentorship%20Session-7DF0B7?style=flat-square&logo=calendly&logoColor=0d1117)](https://topmate.io/manjil_katuwal)
[![TryHackMe](https://img.shields.io/badge/TryHackMe-LEGEND%20%C2%B7%20Top%201%25-7DF0B7?style=flat-square&logo=tryhackme&logoColor=0d1117)](https://tryhackme.com/p/Hiro001)
[![Email](https://img.shields.io/badge/Email-katuwalmanjil609%40gmail.com-7DF0B7?style=flat-square&logo=gmail&logoColor=0d1117)](mailto:katuwalmanjil609@gmail.com)
[![Open to Opportunities](https://img.shields.io/badge/Status-OPEN%20TO%20OPPORTUNITIES-brightgreen?style=flat-square&logo=target&logoColor=0d1117)](#-contact)

</div>

<br/>

> **One-liner for recruiters:** In 21 months I went from zero security experience to SOC Analyst L2 — not by collecting certificates, but by **rebuilding the commercial security stack in Python and shipping it open source**. SIEM engineers operate dashboards. I build the dashboards' engines.

<br/>

##  The 30-Second Pitch

Most candidates *use* security tools. I **reverse-engineered, architected, and shipped** five of them — GRC, CTI, vuln management, NDR, and FIM — each with cryptographic audit trails, MITRE ATT&CK mapping, and pytest suites. When I triage alerts at work, I'm running my own tooling against the same problems my code already solved.

| Metric | Number | Why It Matters |
| --- | --- | --- |
|  Production platforms shipped | **6** | Full SDLC: architecture → code → tests → docs → deployment |
|  MITRE ATT&CK-mapped detections | **60+** | Across Sigma, KQL, SPL, EQL, YARA, Suricata — not just theory |
|  Compliance frameworks automated | **10** | SOC 2 · ISO 27001 · NIST CSF 2.0 · PCI DSS · HIPAA · GDPR · DORA · NIS2 · CMMC · FedRAMP |
|  Alert triage time at work | **8 min → 3 min** | Measured, via Python auto-enrichment I wrote |
|  Automated tests across projects | **300+** | pytest-driven, CI-ready, production-grade |
|  TryHackMe rank | **Top 1% · LEGEND** | 323 rooms · 35 badges — hands-on, not slideware |

<br/>

---

## ⚔️ ARSENAL — What I Built (And Why It's Not a Toy)

> Each platform replaces a $10K–$200K/yr commercial tool. Every claim below is verifiable in the repo — click through.

<table width="100%">
<tr>
<th width="18%">Platform</th>
<th width="16%">Domain</th>
<th width="34%">The Hard Part I Solved</th>
<th width="32%">Receipts</th>
</tr>
<tr>
<td><b>VALENCE</b><br/><sub>flagship</sub></td>
<td>GRC Platform</td>
<td>Connects <b>live SIEM telemetry</b> (Elastic · Splunk · Wazuh · Sentinel) to executive risk metrics. FAIR quantification engine running <b>10,000 Monte Carlo simulations</b> per assessment → dollar-denominated ALE.</td>
<td>10 frameworks · 81 automated control checks · SHA-256 signed audit chain · Docker deploy in &lt;5 min</td>
</tr>
<tr>
<td><b>SENTINEL</b> v1.2.0</td>
<td>Vendor Risk / GRC</td>
<td><b>Deterministic scoring</b> — Decimal-precision math, zero black boxes. Three SHA-256 hashes per assessment (weights · schema · responses) so any score is reproducible months later. Category-floor enforcement kills "95% overall, 10% on encryption" pass-throughs.</td>
<td>Validated vs OneTrust · Archer · Vanta · Panorays · streams 50K vendor CSVs on 4GB RAM</td>
</tr>
<tr>
<td><b>ARGUS</b> v3.0.0</td>
<td>Threat Intel / CTI</td>
<td>Fixes the #1 CTI failure mode: <b>IOC dumps without context</b>. Six-phase pipeline, dual-vector cross-reference (IOC match + TTP applicability against your actual tech stack), confidence decay engine that ages out stale intel by design.</td>
<td>OTX · CISA KEV · MISP ingestion · 30 ATT&CK-mapped rules · advisory SOAR (human-in-the-loop) · D3.js force-graph</td>
</tr>
<tr>
<td><b>RTD-MTA</b> v3.0.1</td>
<td>Network Detection / NDR</td>
<td>5-layer pipeline: Scapy capture → protocol parsing (DNS/HTTP/TLS/SMB/Kerberos/LDAP/FTP) → 3 parallel engines (signature · behavioral sliding-window · Isolation Forest ML on 11 features). DGA via Shannon entropy, C2 beaconing via KS-statistical testing.</td>
<td>1,229 pps · 0.597ms median latency · 30 detection rules · 231/233 tests · VirusTotal/AbuseIPDB/MaxMind enrichment</td>
</tr>
<tr>
<td><b>CERBERUS</b> v2.0.0</td>
<td>Vuln Management</td>
<td>NVD + CISA KEV synced against internal inventory via CPE correlation. SLA deadlines assigned in code (24h for critical internet-facing). Full state machine: Detected → Assigned → Patched → Verified Closed.</td>
<td>Celery + Redis horizontal scaling · SHA-256 lineage to US-GOV source per CVE · ISO 27001 A.8.8 · SOC 2 CC7.1</td>
</tr>
<tr>
<td><b>FIM</b> v1.0.0</td>
<td>File Integrity / SIEM</td>
<td>OS-level watchdog real-time monitoring, ECS-compliant event shipping to Elasticsearch, behavioral ransomware detection (mass-modification + low extension diversity → CRITICAL alert before encryption spreads).</td>
<td>PCI DSS 11.5 · HIPAA §164.312 · SOC 2 CC6.1 · NIST 800-53 SI-7 · 62 pytest tests · graceful SIEM-outage fallback</td>
</tr>
</table>

<details>
<summary><b>🔬 Under the hood — click if you want the engineering depth</b></summary>

<br/>

```yaml
architecture_patterns:
  - cryptographic_score_lineage: "SHA-256 on every export — tamper-evident by design, not by promise"
  - deterministic_scoring:      "Decimal precision, YAML-driven weights, no hidden variables"
  - confidence_decay:           "Stale indicators age out automatically — FP reduction is structural"
  - human_in_the_loop:          "SOAR proposes containment, never executes autonomously"
  - ecs_compliance:             "All SIEM events ship ECS-compliant — drop into any Elastic stack"
  - test_discipline:            "300+ pytest tests across platforms; 231/233 on RTD-MTA alone"

verified_integrations:
  siem:      [Elastic Security, Splunk, Wazuh, Microsoft Sentinel]
  intel:     [AlienVault OTX, CISA KEV, MISP, VirusTotal, AbuseIPDB, MaxMind GeoLite2]
  frameworks:[SOC 2, ISO 27001, NIST CSF 2.0, PCI DSS v4.0, HIPAA, GDPR, DORA, NIS2, CMMC, FedRAMP]
```

</details>

<br/>

---

##  Impact at Work — Udaan Agencies (Security Engineer, Aug 2025 – Present)

> Not a portfolio fantasy — this is my day job.

-  **Cut false-positive noise** in Wazuh + Elastic by tuning thresholds, then documented real findings with timelines for management
-  **Reduced per-alert triage from ~8 min to ~3 min** with Python IOC auto-enrichment and evidence-pulling scripts I wrote
-  **Replaced monthly spreadsheet compliance copy-paste** with a GRC platform that auto-generates SHA-256-signed PDF audit reports (SOC 2 · ISO 27001 · PCI DSS · NIST CSF)
-  **Shipped ~30 MITRE ATT&CK-mapped detection rules to production SIEM** — ransomware, lateral movement, credential abuse
-  **Contained live incidents** via network segmentation + tunnels; tracked vulns against KEV/NVD, enforced SLA patch deadlines by asset criticality

<br/>

---

##  Why I'm Different

<table width="100%">
<tr>
<td width="33%" valign="top">

**01 · I Read The Attack**

Full-stack dev background means I read code for the logic flaws scanners miss — and hand developers fixes they can actually merge.

</td>
<td width="33%" valign="top">

**02 · I Architect The Defense**

I don't operate someone's dashboard. I design and build detection, intel and integrity systems from first principles — Python, FastAPI, Docker, ELK.

</td>
<td width="33%" valign="top">

**03 · I Prove It Mathematically**

Hash-chained audit trails, deterministic scoring, Monte Carlo risk quantification. My results are reproducible and tamper-evident — auditor-grade.

</td>
</tr>
</table>

<br/>

---

## Core Competencies

<table width="100%">
<tr>
<td width="33%" valign="top">

**Detection & Response**

- SIEM: Wazuh · Splunk · ELK · Sentinel
- Sigma · KQL · SPL · EQL · YARA authoring
- Network threat hunting · NDR
- MITRE ATT&CK adversary mapping
- Malware PCAP analysis · ransomware behavior
- IR workflows · forensic triage

</td>
<td width="33%" valign="top">

**GRC & Risk Quantification**

- FAIR risk quantification · Monte Carlo ALE
- CVSS v3.1 / v4.0 triage · CISA KEV priority
- SOC 2 · ISO 27001 · NIST CSF · PCI DSS · HIPAA
- Vendor risk · SLA patch governance
- Cryptographic audit chain design

</td>
<td width="33%" valign="top">

**Security Engineering**

- Python · FastAPI · Celery · Redis · PostgreSQL
- Docker · Kubernetes · Nginx · Linux
- Elasticsearch / ECS pipelines
- ML-assisted detection (Isolation Forest · LSTM)
- Scapy · Pydantic · ReportLab · pytest

</td>
</tr>
</table>

<br/>

---

##  Verified Credentials

<div align="center">

[![CBTP](https://img.shields.io/badge/CBTP-Certified%20Blue%20Teamer%20(with%20Merit)-7DF0B7?style=flat-square&logoColor=0d1117)](https://api.us.credly.com/v1/earned/11534619)
[![CASA](https://img.shields.io/badge/CASA-Certified%20API%20Security%20Analyst-7DF0B7?style=flat-square&logoColor=0d1117)](https://www.credly.com/badges/68800f05-fbd9-407a-8aab-ec17baa3a878)
[![CAP](https://img.shields.io/badge/CAP-Certified%20AppSec%20Practitioner%20(with%20Merit%2C%2083%25)-7DF0B7?style=flat-square&logoColor=0d1117)](https://secops.group)
[![CWAP](https://img.shields.io/badge/CWAP-Certified%20Web%20App%20Pentester-7DF0B7?style=flat-square&logoColor=0d1117)](https://secops.group)
[![CEHPT](https://img.shields.io/badge/CEHPT-Ethical%20Hacking%20Practitioner-7DF0B7?style=flat-square&logoColor=0d1117)](https://secops.group)
[![CDWS](https://img.shields.io/badge/CDWS-Digital%20Workplace%20Security-7DF0B7?style=flat-square&logoColor=0d1117)](https://secops.group)
[![OCI](https://img.shields.io/badge/Oracle%20Cloud-%C3%974%20Professional%20Certs%20(Oct%202025)-7DF0B7?style=flat-square&logo=oracle&logoColor=0d1117)](https://www.credly.com)

<br/>

[![TryHackMe](https://img.shields.io/badge/TryHackMe-LEGEND%20%C2%B7%20Top%201%25%20Globally%20%C2%B7%20323%20Rooms%20%C2%B7%2035%20Badges-7DF0B7?style=flat-square&logo=tryhackme&logoColor=0d1117)](https://tryhackme.com/p/Hiro001)
[![Cisco](https://img.shields.io/badge/Cisco-Ethical%20Hacker%20(Mar%202025)-7DF0B7?style=flat-square&logo=cisco&logoColor=0d1117)](https://www.netacad.com)

</div>

> **Currently pursuing:** GRCP · ISO 27001 Lead Implementer · CRISC

<br/>

---

## 📊 Open Source Activity

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=hiro001-eth&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=7DF0B7&icon_color=7DF0B7&text_color=c9d1d9&rank_icon=github&custom_title=Stats" />
&nbsp;&nbsp;
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=hiro001-eth&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=7DF0B7&text_color=c9d1d9&langs_count=6" />

<br/><br/>

<img src="https://streak-stats.demolab.com/?user=hiro001-eth&theme=github-dark-blue&hide_border=true&background=0d1117&stroke=7DF0B7&ring=7DF0B7&fire=7DF0B7&currStreakLabel=7DF0B7&sideLabels=c9d1d9&dates=666666" />

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=hiro001-eth&bg_color=0d1117&color=7DF0B7&line=7DF0B7&point=ffffff&area=true&area_color=7DF0B740&hide_border=true&custom_title=Contribution+Timeline" width="95%" />

<br/>

<img src="https://raw.githubusercontent.com/hiro001-eth/hiro001-eth/output/github-contribution-grid-snake-dark.svg" width="95%" />

</div>

<br/>

---

## 🛤️ Trajectory

```javascript
Dec 2023 ── zero security experience
    │
Apr 2024 ── IT Engineer (Global Foods UK, remote) ── systems bridge into security
    │
Aug 2025 ── Security Engineer (Udaan Agencies) ── SIEM ops · 60+ detections · GRC platform in prod
    │
NOW      ── 6 platforms shipped · Top 1% THM · 8 certs → pursuing GRCP · ISO 27001 LI · CRISC
    │
NEXT     ── Detection engineering / security platform roles — I build, not just operate
```

<br/>

---

## Writing & Research

I document the *why* behind every build — architecture decisions, attack chains, detection logic:

- 📄 [Why I Built VALENCE: From SIEM Telemetry to Audit-Grade Evidence](https://manjilkatuwal.com.np) *(Jun 2026)*
- 📄 [The Death of the Black Box: Why GRC Needs Cryptographic Certainty](https://manjilkatuwal.com.np) *(Jun 2026)*
- 📄 [I Built an Enterprise Threat Intelligence Pipeline From Scratch](https://manjilkatuwal.com.np) *(Jun 2026)*
- 📄 [SOC Raw Log Analysis: The Complete Field Manual (L1→L3)](https://manjilkatuwal.com.np) *(Apr 2026)*
- 📄 Plus 20+ responsible disclosures on Bugcrowd (auth bypass · sensitive-data exposure · session handling)

<br/>

---

## Mentorship

I mentor people breaking into blue-team/SOC on Topmate — roadmaps, labs, honest career direction.

> *"Had a great 1-on-1 session with Manjil... his clear explanations and practical guidance helped me gain clarity and confidence."* — Topmate mentee, Jun 2026

<br/>

---

## Contact

<div align="center">

**If you need someone who builds the tools, reads the raw logs, and proves the results — let's talk.**

[![Email](https://img.shields.io/badge/Email-katuwalmanjil609%40gmail.com-7DF0B7?style=flat-square&logo=gmail&logoColor=0d1117)](mailto:katuwalmanjil609@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-7DF0B7?style=flat-square&logo=linkedin&logoColor=0d1117)](https://linkedin.com/in/manjil-katuwal-5b39212b0)
[![Schedule](https://img.shields.io/badge/Schedule-1%3A1%20Meeting-7DF0B7?style=flat-square&logo=calendly&logoColor=0d1117)](https://topmate.io/manjil_katuwal)
[![Portfolio](https://img.shields.io/badge/Portfolio-manjilkatuwal.com.np-7DF0B7?style=flat-square&logo=google-chrome&logoColor=0d1117)](https://manjilkatuwal.com.np/)

</div>

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0d1117&height=120&section=footer&text=Understand%20the%20attack.%20Architect%20the%20defense.%20Prove%20it%20mathematically.&fontSize=16&fontColor=7DF0B7&fontAlignY=65&animation=fadeIn&stroke=7DF0B7&strokeWidth=1" width="100%" />
