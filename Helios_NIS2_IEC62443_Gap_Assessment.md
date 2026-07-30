**HELIOS GRID UTILITIES**

*Frankfurt, Germany · Regional Electricity Distribution Operator*

**NIS2 / IEC 62443 Mini Gap Assessment**

**& NIST CSF 2.0 Control Mapping**

**Prepared for:** Helios Grid Utilities — IT/OT Cybersecurity Governance Programme

**Prepared by:** GRC Analyst — Cybersecurity Governance, Risk & Compliance Function

**Document type:** Mini Gap Assessment & Control Mapping (working paper)

**Classification:** Internal — Restricted

# 1. Executive Summary

Helios Grid Utilities is a mature, heavily regulated electricity distribution operator undergoing a major smart-grid modernization while continuing to run decades-old OT/SCADA systems. This working paper presents a mini gap assessment of Helios's current cybersecurity posture against the EU NIS2 Directive's Article 21 risk-management requirements and the IEC 62443 series for industrial automation and control systems (IACS) security. It then translates the identified gaps into ten concrete controls mapped to NIST CSF 2.0 subcategories, which Helios can use as the initial control backbone for its unified IT/OT cybersecurity governance programme.

The assessment confirms the risk picture implied by the scenario: the historical separation between corporate IT and OT/ICS, combined with an expanding, poorly inventoried smart-grid attack surface and fragmented vendor remote access, creates critical exposure in network segmentation, identity and access management, and OT vulnerability handling. These three areas, together with the absence of a unified IT/OT governance structure, should anchor Helios's initial remediation roadmap ahead of formal NIS2/KRITIS audits.

Section 2 sets out scope and methodology. Section 3 presents the ten-domain gap assessment against NIS2 Article 21 and IEC 62443. Section 4 maps ten priority controls to NIST CSF 2.0 subcategories, each with implementation guidance and a suggested owner and timeframe. Section 5 summarizes the resulting remediation roadmap by priority horizon.

# 2. Scope & Methodology

Scope: this mini assessment covers Helios's corporate IT environment (email, ERP, billing, customer portal), the OT/ICS environment (substation and distribution SCADA), and the smart-grid rollout (smart meters, grid-automation sensors, renewable-integration platform), together with the third-party vendors that support them.

- Gap assessment criteria: EU NIS2 Directive, Article 21 cybersecurity risk-management measures (as the primary EU-level legal driver, reflected nationally in Germany's BSI/KRITIS regime).
- OT/ICS criteria: IEC 62443 series, principally 62443-2-1 (security programme requirements for asset owners), 62443-3-2/3-3 (system security and zone/conduit requirements), 62443-2-4 (service-provider requirements), and 62443-4-1 (secure product development for suppliers).
- Control framework: NIST CSF 2.0, used as the organizing structure for translating gaps into actionable, ownable controls across the Govern, Identify, Protect, Detect, Respond, and Recover functions.
- Approach: desk-based review of the scenario facts (current state), each mapped to the applicable NIS2 article and IEC 62443 clause, with a risk rating reflecting likelihood and potential safety/operational impact given Helios's critical-infrastructure role.

This is a mini assessment intended to seed the governance programme; it should be followed by a full-scope risk analysis, an IEC 62443 zone/conduit and security-level (SL-T) exercise, and a NIS2 self-assessment against BSI's audit expectations.

# 3. NIS2 / IEC 62443 Mini Gap Assessment

Ten cybersecurity domains assessed against NIS2 Article 21 risk-management measures and the applicable IEC 62443 clauses, with current state, identified gap, and a risk rating reflecting likelihood and potential public-safety/operational impact.

| Domain | NIS2 Art. 21 Ref. | IEC 62443 Ref. | Current State at Helios | Identified Gap | Risk |
|---|---|---|---|---|---|
| **1. Governance, Risk Management & Accountability** | Art. 21(1)–(2)(a); Art. 20 | 62443-2-1 §4.2, §4.3 | IT and OT security are governed by separate teams on different reporting lines; no unified cybersecurity management system (CSMS) or single risk owner spans both domains; management-body accountability under NIS2 Art. 20 is not formalized. | No integrated IT/OT governance charter, enterprise risk-appetite statement, or CSMS; the management body has not documented approval and oversight of cybersecurity risk-management measures as NIS2 requires. | **HIGH** |
| **2. Asset Management (IT/OT Inventory)** | Art. 21(2)(a) | 62443-2-1 §4.2.3; 62443-3-2 | No consolidated asset inventory spans IT and OT; thousands of multi-vendor smart-grid field devices are being deployed without central registration. | Risk analysis, zone/conduit design, and vulnerability management cannot be reliably scoped without a validated, continuously updated IT/OT asset inventory. | **HIGH** |
| **3. Network Segmentation (Zones & Conduits)** | Art. 21(2)(a), (j) | 62443-3-2; 62443-3-3 | OT was historically air-gapped but is increasingly networked for remote monitoring and smart-grid connectivity; segmentation boundaries are not formally defined or enforced. | No documented zones/conduits model and no security-level targets (SL-T) assigned to substation/SCADA zones; de facto flat connectivity exists between IT and OT paths. | **CRITICAL** |
| **4. Identity & Access Management incl. Remote/Vendor Access** | Art. 21(2)(i) | 62443 FR1, FR2 | IAM is fragmented across legacy and modern systems; vendor remote-access pathways into OT are poorly inventoried; MFA is inconsistently applied, especially in OT. | No centralized IAM/PAM for OT, no least-privilege model for vendor remote sessions, and no consistent MFA on remote OT access points. | **CRITICAL** |
| **5. Incident Handling, Detection & Regulatory Reporting** | Art. 23 | 62443-2-1 §4.3.4.5; FR6 | IT operates a SOC and incident process; OT lacks equivalent detection capability and there is no joint IT/OT incident response plan aligned to NIS2's tiered timelines. | No unified IT/OT incident response plan, no OT-aware detection capability, and no tested workflow for meeting NIS2's 24-hour / 72-hour / 1-month reporting obligations to BSI. | **HIGH** |
| **6. Third-Party & Supply Chain / OT Vendor Risk** | Art. 21(2)(d) | 62443-2-4; 62443-4-1 | Multiple smart-meter and grid-automation vendors have been onboarded without standardized security requirements or assessment; remote-access agreements are not centrally tracked. | No vendor risk-tiering, no contractual security clauses (SBOM, patch SLAs, secure remote access) aligned to 62443-2-4/4-1, and no ongoing vendor security monitoring. | **HIGH** |
| **7. Vulnerability & Patch Management (Legacy OT)** | Art. 21(2)(e) | 62443 FR3; 62443-2-3 | OT engineers prioritize uptime and safety; many control systems are unsupported or cannot be easily patched; there is no compensating-control program for known vulnerabilities. | No documented compensating-controls process (virtual patching, isolation) for unpatchable OT assets, and no formal vulnerability handling/disclosure procedure. | **CRITICAL** |
| **8. Business Continuity, Resilience & Crisis Management** | Art. 21(2)(c) | 62443 FR7 | Physical/operational contingency plans exist for grid outages on safety grounds, but cyber-specific BC/DR and crisis-management plans covering OT remain underdeveloped. | No integrated cyber-physical crisis management plan tested against a scenario resembling the neighboring utility's OT-disrupting attack. | **MEDIUM-HIGH** |
| **9. Cryptography & Protection of Operational/Customer Data** | Art. 21(2)(h) | 62443 FR4, FR5 | Corporate IT (billing, customer portal) uses modern encryption standards; protection of grid-topology and control-system data in OT is inconsistent, particularly on legacy protocols. | No enterprise-wide cryptography policy covering OT protocols and data at rest/in transit; sensitive grid-topology data is not formally classified or consistently protected. | **MEDIUM-HIGH** |
| **10. Security Awareness, Training & Cyber Hygiene** | Art. 21(2)(g) | 62443-2-1 §4.3.2 | General security-awareness training exists for corporate staff; OT engineers and field technicians receive limited role-specific cybersecurity training. | No OT-specific security training curriculum for engineers/vendors, and no documented board/executive cyber-hygiene training to evidence NIS2 accountability. | **MEDIUM** |

**Risk rating legend:**

| Rating | Meaning |
|---|---|
| Critical | Immediate action required; direct exposure to safety/operational disruption |
| High / Medium-High | Action required within the current audit/remediation cycle |
| Medium | Action required but lower immediate exposure |

# 4. Controls Mapped to NIST CSF 2.0 Subcategories

The following ten controls address the highest-priority gaps identified in Section 3, mapped to NIST CSF 2.0 subcategories spanning the Govern, Identify, Protect, Detect, Respond, and Recover functions. Each control references the corresponding NIS2 article and IEC 62443 clause to support audit traceability.

| ID | NIST CSF 2.0 Subcategory | Control Statement | Implementation Guidance (IT/OT) | NIS2 / IEC 62443 Ref. | Priority | Owner |
|---|---|---|---|---|---|---|
| **C-01** | **GV.SC-04** — Suppliers are known and prioritized by criticality | Establish and maintain a risk-tiered register of all IT and OT suppliers/vendors (smart-meter, SCADA, grid-automation), including criticality rating and remote-access footprint. | Build a vendor register in the GRC platform; classify vendors by OT criticality (Tier 1 = direct SCADA/substation access); require signed security addenda with 62443-2-4-aligned clauses for Tier 1 vendors. | Art. 21(2)(d); 62443-2-4 | Immediate (0–3 mo) | GRC / Procurement |
| **C-02** | **ID.AM-01** — Inventories of hardware managed by the organization are maintained | Maintain a continuously updated hardware asset inventory spanning corporate IT, OT/SCADA, and field devices (smart meters, sensors). | Deploy passive OT network-discovery tooling alongside existing ITAM; reconcile against substation engineering records; assign an owner and criticality tag to every asset. | Art. 21(2)(a); 62443-2-1 §4.2.3 | Immediate (0–3 mo) | IT / OT Engineering |
| **C-03** | **ID.AM-02** — Inventories of software and services managed by the organization are maintained | Maintain an inventory of software/firmware versions and services running on IT systems and OT/ICS components, including vendor-supplied field-device firmware. | Extend the CMDB to capture OT firmware versions and service dependencies; integrate vendor SBOM submissions where available. | Art. 21(2)(a); 62443-4-1 | Short-term (3–6 mo) | IT / OT Engineering |
| **C-04** | **ID.RA-01** — Vulnerabilities in assets are identified, validated, and recorded | Operate an IT/OT vulnerability management process, including compensating controls for unpatchable legacy OT assets. | Run authenticated IT scanning plus passive OT vulnerability identification; log findings in a unified risk register with compensating-control status (segmentation, monitoring) for assets that cannot be patched. | Art. 21(2)(e); 62443 FR3 / 62443-2-3 | Short-term (3–6 mo) | OT Engineering / Security |
| **C-05** | **PR.AA-05** — Access permissions, entitlements, and authorizations are defined and managed | Implement least-privilege, centrally governed access control for all IT and OT accounts, with mandatory MFA on all remote and vendor access into OT. | Deploy a PAM solution for OT jump-host/remote-access sessions; consolidate IAM across legacy and modern systems; enforce MFA and session recording for vendor remote access. | Art. 21(2)(i); 62443 FR1 / FR2 | Immediate (0–3 mo) | IAM / Security |
| **C-06** | **PR.IR-01** — Networks/environments are protected from unauthorized logical access and misuse | Define and enforce a zones-and-conduits architecture separating corporate IT, OT/SCADA, and smart-grid field networks, with security-level targets per zone. | Conduct a zone/conduit workshop per 62443-3-2; deploy firewalls or data diodes at conduits; assign SL-T per zone criticality, with substations rated highest. | Art. 21(2)(a), (j); 62443-3-2 / 3-3 | Immediate (0–6 mo) | OT Engineering / Network Security |
| **C-07** | **PR.DS-01** — The confidentiality, integrity, and availability of data-at-rest are protected | Apply an enterprise cryptography policy covering encryption of grid-topology data, control-system configurations, and customer data at rest, aligned to data classification. | Classify grid-topology and control-system data as Restricted; apply encryption at rest for historian/engineering data stores; extend existing IT encryption standards to OT repositories where feasible. | Art. 21(2)(h); 62443 FR4 | Medium-term (6–12 mo) | Security / Data Governance |
| **C-08** | **DE.CM-01** — Networks and network services are monitored to find potentially adverse events | Extend security monitoring (SIEM/SOC) to OT network traffic and SCADA telemetry, with OT-aware detection use cases. | Deploy OT-specific network-monitoring sensors at conduits; feed anomaly alerts into the existing SOC with an OT escalation runbook; pilot on the highest-criticality substations first. | Art. 21(2)(a); 62443 FR6 | Medium-term (6–12 mo) | SOC / OT Engineering |
| **C-09** | **RS.MA-01** — The incident response plan is executed once an incident is declared | Establish and test a joint IT/OT incident response plan that meets NIS2 Art. 23 reporting timelines (24-hour early warning, 72-hour notification, 1-month report to BSI). | Build IR playbooks covering OT-disruption scenarios; run a tabletop exercise simulating a peer-utility-style OT attack; pre-stage BSI notification templates and escalation contacts. | Art. 23; 62443-2-1 §4.3.4.5 | Immediate (0–3 mo) | CISO / Incident Response |
| **C-10** | **RC.RP-01** — The recovery portion of the incident response plan is executed | Develop and test IT/OT recovery and crisis-management procedures, including manual/fail-safe grid-operation fallback, to restore safe operations after a cyber incident. | Define recovery-time objectives per substation criticality; validate OT backup/restore for engineering configurations; run a joint IT/OT/physical-safety crisis simulation annually. | Art. 21(2)(c); 62443 FR7 | Medium-term (6–12 mo) | OT Engineering / Business Continuity |

# 5. Prioritized Remediation Roadmap

Controls are grouped below by suggested implementation horizon. Immediate actions target the Critical-rated gaps in segmentation, access, and vulnerability handling identified in Section 3, and establish the governance and incident-response foundations NIS2 requires before formal BSI/KRITIS audit engagement.

## Immediate (0–3 months)

- C-01 — Risk-tiered IT/OT vendor register with security addenda (GV.SC-04)
- C-02 — Consolidated IT/OT hardware asset inventory (ID.AM-01)
- C-05 — Centralized, least-privilege IAM/PAM with MFA on OT remote access (PR.AA-05)
- C-06 — Zones-and-conduits network segmentation design and enforcement, initiated (PR.IR-01)
- C-09 — Joint IT/OT incident response plan aligned to NIS2 Art. 23 reporting timelines (RS.MA-01)

## Short-term (3–6 months)

- C-03 — IT/OT software and firmware inventory, integrated with vendor SBOMs (ID.AM-02)
- C-04 — IT/OT vulnerability management with compensating controls for legacy OT (ID.RA-01)
- C-06 — Completion of zone/conduit enforcement with assigned security-level targets (PR.IR-01)

## Medium-term (6–12 months)

- C-07 — Enterprise cryptography policy for grid-topology and control-system data (PR.DS-01)
- C-08 — OT-aware network monitoring integrated into the SOC (DE.CM-01)
- C-10 — Tested IT/OT recovery and crisis-management procedures (RC.RP-01)

# 6. Assumptions & Next Steps

- This is a mini assessment based on the scenario narrative; a full-scope assessment should validate current-state statements with Helios's IT, OT engineering, and procurement teams.
- A dedicated IEC 62443-3-2 zone/conduit and security-level (SL-T) workshop should follow to give C-06 the technical detail regulators and auditors will expect.
- The unified IT/OT risk register and asset inventory (C-02/C-03) should become the single source of truth feeding the NIS2 risk analysis, the vendor risk programme, and BSI/KRITIS audit evidence.
- Recommend re-running this gap assessment on a semi-annual cycle, and immediately after any material change to the OT network architecture or vendor landscape.
