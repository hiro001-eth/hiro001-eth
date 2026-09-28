<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0d1117&height=200&section=header&text=Manjil%20Katuwal&fontSize=52&fontColor=7DF0B7&fontAlignY=45&desc=Security%20Engineer%20%C2%B7%20Detection%20%C2%B7%20GRC%20%C2%B7%20Security%20Tooling&descAlignY=68&descSize=17&descColor=8b949e&animation=fadeIn" width="100%" />

[Portfolio](https://manjilkatuwal.com.np/) &middot; [LinkedIn](https://linkedin.com/in/manjil-katuwal-5b39212b0) &middot; [TryHackMe](https://tryhackme.com/p/Hiro001) &middot; [Topmate](https://topmate.io/manjil_katuwal) &middot; [Email](mailto:katuwalmanjil609@gmail.com)

</div>

---

I work as a security engineer and SOC analyst. Most of the tooling in this profile exists because a problem annoyed me enough to fix it properly: alert queues with no context, compliance evidence nobody could verify, and risk scores produced by black boxes.

So I built the tools myself. Six platforms, all published with source, tests, and documentation. Everything below links to working code, and every performance or coverage number is reproducible from the repos.

I started in security in December 2023 with no prior experience. The trajectory since then is documented rather than claimed.

---

## Platforms

| Project | Domain | What it actually does | Verification |
| --- | --- | --- | --- |
| [VALENCE](https://github.com/hiro001-eth/VALENCE-GRC-Platform) | GRC | Pulls live telemetry from Elastic, Splunk, Wazuh, and Sentinel into one evidence store. FAIR quantification engine runs 10,000 Monte Carlo simulations per assessment and outputs dollar-denominated annual loss expectancy. Compliance testing runs continuously across 10 frameworks. | 81 automated control checks, SHA-256 signed audit exports, hash-chained records back to the source SIEM event |
| [SENTINEL](https://github.com/hiro001-eth/SENTINEL-Vendor-Risk-Scoring-Engine) v1.2.0 | Vendor risk | Deterministic scoring engine. YAML-driven weights, Decimal precision, no hidden variables. Every assessment carries three SHA-256 hashes (weights, schema, responses) so any score can be reproduced later. Category floors prevent a weak encryption score from hiding behind a high average. | Benchmarked against OneTrust, Archer, Vanta, and Panorays output. Streams 50K-row vendor CSVs on 4 GB RAM |
| [ARGUS](https://github.com/hiro001-eth/ARGUS-Enterprise-Threat-Intelligence-Pipeline) v3.0.0 | Threat intelligence | Six-phase CTI pipeline ingesting OTX, CISA KEV, and MISP. Every indicator is mapped to MITRE ATT&CK and cross-referenced against the asset inventory two ways: direct IOC match and TTP applicability against the running tech stack. A confidence decay engine ages out stale indicators instead of letting them pile up in the queue. | 30 ATT&CK-mapped rules, advisory SOAR with human approval on every action, D3.js exposure graph |
| [RTD-MTA](https://github.com/hiro001-eth/Ransomware-Traffic-Detector-Integrated-with-Malware-Traffic-Analyzer) v3.0.1 | Network detection | Live packet capture through three parallel engines: signature matching, behavioral heuristics with sliding windows, and an Isolation Forest model over 11 traffic features. DGA detection uses Shannon entropy and n-gram analysis; C2 beaconing uses Kolmogorov-Smirnov testing on inter-arrival times. | 1,229 packets/sec at 0.597 ms median latency. 231 of 233 tests passing. VirusTotal, AbuseIPDB, and MaxMind enrichment |
| [CERBERUS](https://github.com/hiro001-eth/CERBERUS-CVE-to-Risk-Register-Pipeline) v2.0.0 | Vulnerability management | Syncs NVD and CISA KEV against the internal inventory via CPE correlation. SLA deadlines are enforced in code: 24 hours for critical internet-facing assets, longer for internal dev systems. Full lifecycle state machine from detection to verified closure, with SHA-256 lineage to the original government source per record. | Celery and Redis for horizontal scaling. ISO 27001 A.8.8 and SOC 2 CC7.1 mapping |
| [FIM](https://github.com/hiro001-eth/SIEM-Integrated-File-Integrity-Monitor-FIM-) v1.0.0 | File integrity | Real-time monitoring via OS-level watchdog events, SHA-256 baselines, ECS-compliant JSON shipped to Elasticsearch. Behavioral ransomware detection fires a critical alert when mass modification with low extension diversity occurs inside a configurable window, before encryption finishes spreading. | Satisfies PCI DSS 11.5, HIPAA 164.312(c), SOC 2 CC6.1, and NIST 800-53 SI-7. 62 pytest tests. Local fallback logging when Elasticsearch is down |

The design decisions these projects share: deterministic logic over opaque scoring, cryptographic lineage on anything an auditor will ever touch, and a human in the loop wherever automation could break production.

---

## Work

**Security Engineer, Udaan Agencies** (Birtamode, Nepal, Aug 2025 to present)

- Own the morning alert queue in Wazuh and Elastic. Tuned thresholds until the false-positive rate dropped, then built Python scripts for IOC enrichment and evidence collection. Per-alert handling time went from about 8 minutes to about 3, measured across the queue.
- Built the internal GRC platform now used for SOC 2, ISO 27001, PCI DSS, and NIST CSF evidence. Monthly audit exports are generated and cryptographically signed instead of assembled by hand in spreadsheets.
- Wrote roughly 30 detection rules mapped to MITRE ATT&CK and shipped them to production SIEM. Coverage includes ransomware behavior, lateral movement, and credential abuse.
- Handled incident containment directly: network segmentation, isolation tunnels, and CISA KEV/NVD-driven patch enforcement with per-asset SLAs.

**IT Engineer, Global Foods UK** (remote, Apr 2024 to Oct 2024). Systems and infrastructure support across UK operations; the bridge from software into security.

**Backend Developer, Astral Techsoft** (Mechinagar, Nepal, Dec 2023 to Mar 2024). Backend development. This is why I read application code for logic flaws rather than relying on scanner output alone.

---

## Detection engineering

Triage is necessary but not the interesting part. The rules below are the kind of content I write and tune: correlation over single events, behavioral sequences over IOC matching, statistical baselines where indicators do not exist.

| Type | Detection | Technique | Why the logic holds |
| --- | --- | --- | --- |
| Sigma correlation | Password spray followed by successful logon | T1110.003 | Fires only on the sequence: 15+ failures from one source, then a valid session within 15 minutes. Either event alone is noise. |
| KQL | DCSync from a non-DC principal | T1003.006 | Watches 4662 for the replication GUIDs being requested by accounts that are not domain controllers or machine accounts. |
| EQL | LSASS access into outbound connection | T1003.001 to T1071 | Sequences a suspicious LSASS handle grant with an outbound non-RFC1918 connection from the same host inside two minutes. |
| SPL | C2 beaconing by jitter analysis | T1071 | Scores src/dst pairs on inter-arrival regularity (coefficient of variation under 0.15) and constant payload sizes. Catches beaconing on domains that are hours old. |
| YARA | Cobalt Strike beacon in memory | T1055 | Matches the encoded config marker, sleep-mask stub, and named-pipe convention against process memory, not on-disk strings. |
| Suricata | Known-C2 TLS by JA3 | T1071.001 | TLS payload is encrypted; the client hello is not. JA3 matching catches the framework even on a fresh domain and certificate. |
| Sigma | Kerberoasting via RC4 downgrade burst | T1558.003 | Filters to weak RC4 tickets, drops machine accounts and krbtgt, alerts only on a per-source burst. The enumeration pattern is the signal. |

Full rules, tuning notes, and false-positive guidance live in the [detection writeups](https://github.com/hiro001-eth/What-I-Learned-Today-on-SOC-GRC-) repo and on the portfolio site.

---

## Numbers

| Measure | Value |
| --- | --- |
| Production platforms published | 6 |
| ATT&CK-mapped detections authored | 60+ |
| Compliance frameworks automated | 10 (SOC 2, ISO 27001, NIST CSF 2.0, PCI DSS v4.0, HIPAA, GDPR, DORA, NIS2, CMMC, FedRAMP) |
| Automated tests across projects | 300+ |
| TryHackMe | Top 1% globally, LEGEND rank, 323 rooms, 35 badges |
| Responsible disclosures | 20+ reports on Bugcrowd (auth bypass, data exposure, session handling, rate limiting) |

---

## Certifications

| Certification | Issuer | Date |
| --- | --- | --- |
| Certified Blue Team Practitioner, with Merit | The SecOps Group | May 2026 |
| Certified API Security Analyst | APIsec University | Apr 2026 |
| Certified AppSec Practitioner, with Merit (83%) | The SecOps Group | 2025 |
| Certified Web Application Pentester | The SecOps Group | 2025 |
| CEH Practical-track certification (CEHPT) | The SecOps Group | 2025 |
| Certified Digital Workplace Security | The SecOps Group | 2025 |
| OCI Networking Professional | Oracle | Oct 2025 |
| OCI Generative AI Professional | Oracle | Oct 2025 |
| OCI Application Integration Professional | Oracle | Oct 2025 |
| Oracle Analytics Cloud Professional | Oracle | Oct 2025 |
| Ethical Hacker | Cisco Networking Academy | Mar 2025 |

Currently studying for GRCP, ISO 27001 Lead Implementer, and CRISC.

---

## Writing

- [Why I Built VALENCE: From SIEM Telemetry to Audit-Grade Evidence](https://manjilkatuwal.com.np) (Jun 2026)
- [The Death of the Black Box: Why GRC Needs Cryptographic Certainty](https://manjilkatuwal.com.np) (Jun 2026)
- [I Built an Enterprise Threat Intelligence Pipeline From Scratch](https://manjilkatuwal.com.np) (Jun 2026)
- [SOC Raw Log Analysis: The Complete Field Manual, L1 to L3](https://manjilkatuwal.com.np) (Apr 2026)
- [My 90-Day Journey to 4 Oracle Cloud Certifications](https://manjilkatuwal.com.np) (Nov 2025)

I also mentor people entering blue-team work through [Topmate](https://topmate.io/manjil_katuwal), mostly roadmaps, lab selection, and honest assessments of where someone actually stands.

---

## Activity

<div align="center">

<img height="160" src="https://github-readme-stats.vercel.app/api?username=hiro001-eth&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=7DF0B7&icon_color=7DF0B7&text_color=c9d1d9&rank_icon=github&custom_title=GitHub+Stats" />
&nbsp;&nbsp;
<img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=hiro001-eth&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=7DF0B7&text_color=c9d1d9&langs_count=6" />

<br/><br/>

<img src="https://streak-stats.demolab.com/?user=hiro001-eth&theme=github-dark-blue&hide_border=true&background=0d1117&stroke=7DF0B7&ring=7DF0B7&fire=7DF0B7&currStreakLabel=7DF0B7&sideLabels=c9d1d9&dates=666666" />

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=hiro001-eth&bg_color=0d1117&color=7DF0B7&line=7DF0B7&point=ffffff&area=true&area_color=7DF0B740&hide_border=true&custom_title=Contribution+Timeline" width="95%" />

</div>

---

## Contact

I am open to security engineering, detection engineering, and SOC roles.

Email: katuwalmanjil609@gmail.com
LinkedIn: [manjil-katuwal-5b39212b0](https://linkedin.com/in/manjil-katuwal-5b39212b0)
Portfolio: [manjilkatuwal.com.np](https://manjilkatuwal.com.np)
Schedule a call: [topmate.io/manjil_katuwal](https://topmate.io/manjil_katuwal)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0d1117&height=100&section=footer&text=Nepal+%C2%B7+Open+Source+%C2%B7+Blue+Team&fontSize=15&fontColor=7DF0B7&fontAlignY=65&animation=fadeIn" width="100%" />
