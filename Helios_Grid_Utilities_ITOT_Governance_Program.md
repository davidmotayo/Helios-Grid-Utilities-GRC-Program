# HELIOS GRID UTILITIES

## Unified IT/OT Cybersecurity Governance Program

*Aligned to NIST CSF 2.0 · IEC 62443 · ISO/IEC 27001:2022 · NIS2 Directive · Germany BSI/KRITIS*

**Document Classification: INTERNAL — CONFIDENTIAL**

Frankfurt am Main, Germany

Version 1.0 — Effective Date: 29 July 2026

Owner: Governance, Risk & Compliance (GRC) Function — Office of the CISO

### Document Control

| **Field**        | **Detail**                                                                                                                                                                        |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Document Title   | Unified IT/OT Cybersecurity Governance Program                                                                                                                                    |
| Document Owner   | Chief Information Security Officer (CISO), on behalf of the IT/OT Security Governance Council                                                                                     |
| Prepared By      | GRC Analyst — Information Security Compliance                                                                                                                                     |
| Approved By      | Executive Board / Management Board (Vorstand); pending formal sign-off                                                                                                            |
| Version          | 1.0 — Initial Baseline                                                                                                                                                            |
| Effective Date   | 29 July 2026                                                                                                                                                                      |
| Review Cycle     | Annually, and upon material change to threat landscape, regulatory obligations, or organizational structure                                                                       |
| Classification   | Internal — Confidential (Restricted distribution: Executive Board, CISO Office, OT Engineering Leadership, Internal Audit, Regulators upon request)                               |
| Regulatory Basis | EU NIS2 Directive (2022/2555); German IT-Sicherheitsgesetz 2.0 / BSI-KritisV (KRITIS); IEC 62443 series; ISO/IEC 27001:2022; NIST Cybersecurity Framework 2.0 (guiding reference) |

## 1. Executive Summary

Helios Grid Utilities ("Helios") is a regional electricity distribution operator serving approximately 1.4 million households and businesses across Frankfurt and surrounding districts. As a designated operator of essential services under the EU NIS2 Directive and Germany's KRITIS regime, Helios bears a direct legal and societal obligation to protect the confidentiality, integrity, and availability of the systems that keep power flowing.

Helios today operates two cybersecurity realities under one roof: a modern, cloud-connected corporate IT estate (email, ERP, billing, customer portal) and a legacy, safety-critical Operational Technology (OT) estate (SCADA, substation automation, distribution control) that has historically been isolated but is rapidly being networked through the smart-grid, smart-meter, and renewable-integration rollout. These two environments have been governed independently, by separate teams, using separate risk languages, with no unified asset inventory, no shared risk register, and no consolidated view of third-party access. This fragmentation is no longer tenable: it is both a regulatory exposure under NIS2/KRITIS and an operational risk given the precedent of an OT-disrupting attack against a neighboring peer utility.

This document establishes Helios's Unified IT/OT Cybersecurity Governance Program. It defines the governance structure, risk management methodology, asset and risk inventory approach, access control and network segmentation requirements, third-party/vendor risk management program, incident response and regulatory reporting obligations, and audit-readiness posture required to bring Helios into demonstrable compliance with NIS2, BSI/KRITIS, IEC 62443, and ISO/IEC 27001, using the NIST Cybersecurity Framework (CSF) 2.0 as the unifying structure across both IT and OT domains.

This program does not ask OT engineering to adopt IT security practices wholesale, nor does it ask IT to defer to OT on enterprise risk. It establishes a single governance authority, a shared risk language, and domain-appropriate controls — recognizing that in OT, safety and availability are non-negotiable and that security controls must be engineered around that constraint, not against it.

## 2. Purpose, Scope, and Applicability

### 2.1. Purpose

The purpose of this document is to establish a single, board-endorsed cybersecurity governance framework spanning both Information Technology (IT) and Operational Technology (OT) at Helios, ensuring that:

- Cybersecurity risk to corporate systems and to grid operations is identified, assessed, treated, and reported through one coherent governance structure.

- Helios can demonstrate compliance with NIS2, BSI/KRITIS, IEC 62443, and ISO/IEC 27001 to regulators and auditors on demand.

- Accountability for cybersecurity outcomes is clearly assigned, up to and including the Management Board, consistent with NIS2 Article 20 management-body liability provisions.

- IT and OT teams operate from a shared asset inventory, shared risk register, and shared incident response process, while retaining domain-specific technical practices.

### 2.2. Scope

This program applies to:

- All corporate IT systems, networks, applications, and data, including email, ERP, billing and customer relationship systems, the customer self-service portal, and supporting cloud infrastructure.

- All Operational Technology / Industrial Control Systems (OT/ICS), including SCADA master stations, substation automation and protection systems, remote terminal units (RTUs) and programmable logic controllers (PLCs), distribution management systems (DMS), the renewable-integration platform, and grid-automation sensor networks.

- The smart metering infrastructure (AMI), including meter data management systems, head-end systems, and field communication networks.

- All third parties, vendors, systems integrators, and managed service providers with access to Helios IT or OT environments, including remote access pathways.

- All employees, contractors, and temporary staff with logical or physical access to in-scope systems.

### 2.3. Out of Scope

Physical security of substations and generation assets is governed under the separate Physical Security and Site Access Policy, though this program defines the cybersecurity requirements for any networked physical-security systems (e.g., IP cameras, access-control controllers) that connect to IT or OT networks.

## 3. Governance Structure and Accountability

Helios establishes a single governance authority spanning IT and OT: the IT/OT Security Governance Council. This resolves the prior state in which IT and OT security decisions were made independently, with no forum for shared risk visibility or conflict resolution.

### 3.1. Governance Bodies

**Management Board (Vorstand)**

Holds ultimate accountability for cybersecurity risk under NIS2 Article 20, which imposes direct governance duties and potential personal liability on management bodies of essential entities. The Board approves this governance program annually, approves risk appetite, and receives quarterly risk and incident reporting.

**IT/OT Security Governance Council (new)**

A standing cross-functional body chaired by the CISO, meeting monthly (or ad hoc following a significant incident), responsible for: approving the unified risk register, resolving IT–OT control conflicts (e.g., patch timing vs. uptime), overseeing third-party risk exceptions, and reviewing audit and regulatory findings. Permanent members include the CISO, Head of OT Engineering, Head of IT Infrastructure, Data Protection Officer, Head of Internal Audit (observer), and the GRC function.

**Chief Information Security Officer (CISO)**

Owns this governance document, the unified risk register, and the security architecture spanning IT and OT. Reports to the Management Board and holds the NIS2-mandated point of contact role for regulatory liaison with BSI and the competent authority.

**OT Security Lead**

A dedicated role (new, reporting jointly to the CISO and Head of OT Engineering) responsible for translating IT/OT governance requirements into engineering practice on the control-system side — the single accountable owner for IEC 62443 zone/conduit design, OT patch and change management, and OT vendor remote access.

**GRC Function**

Maintains the risk register, asset inventory governance, policy lifecycle, audit calendar, and regulatory reporting evidence across both domains; acts as the neutral coordinating layer between IT and OT teams.

### 3.2. RACI — Key Governance Activities

| **Activity**                                | **Mgmt Board** | **CISO** | **OT Security Lead** | **IT Infra Lead** | **GRC** |
|---------------------------------------------|----------------|----------|----------------------|-------------------|---------|
| Approve governance program & risk appetite  | A              | R        | C                    | C                 | C       |
| Maintain unified asset inventory            | I              | A        | R                    | R                 | C       |
| Maintain unified risk register              | I              | A        | R                    | R                 | R       |
| Approve OT change / patch exceptions        | I              | C        | A/R                  | C                 | C       |
| Third-party / vendor risk assessment        | I              | A        | R                    | C                 | R       |
| Incident declaration & regulatory reporting | I              | A/R      | R                    | R                 | R       |
| Internal & external audit coordination      | I              | A        | C                    | C                 | R       |
| Security awareness & training program       | I              | A        | C                    | C                 | R       |

*R = Responsible, A = Accountable, C = Consulted, I = Informed.*

## 4. Regulatory and Framework Alignment

Helios is subject to overlapping but complementary regulatory and standards obligations. This program uses NIST CSF 2.0 as the organizing structure because its six functions (Govern, Identify, Protect, Detect, Respond, Recover) map cleanly onto both IT and OT domains and provide a single vocabulary for board-level reporting, while IEC 62443 and ISO/IEC 27001 supply the domain-specific control depth, and NIS2/KRITIS define the legal minimum and reporting obligations.

### 4.1. Driver Summary

| **Driver**                                              | **Nature**                                        | **Key Obligation for Helios**                                                                                                                                        |
|---------------------------------------------------------|---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| EU NIS2 Directive (2022/2555)                           | Binding EU law, transposed into German law        | Risk management measures, management-body accountability, supply-chain security, 24-hour early warning / 72-hour incident notification / 1-month final report to BSI |
| Germany IT-Sicherheitsgesetz 2.0 / BSI-KritisV (KRITIS) | National critical-infrastructure regulation       | Registration as critical infrastructure operator, mandatory attack-detection systems, 2-yearly proof of compliance (§8a BSIG audits), incident reporting to BSI      |
| IEC 62443 series                                        | International OT/ICS security standard            | Zone and conduit segmentation, Security Levels (SL) for OT components, secure product/system lifecycle for control systems and vendors                               |
| ISO/IEC 27001:2022                                      | International ISMS standard                       | Certifiable Information Security Management System, Annex A controls, Statement of Applicability covering IT and, where scoped, OT                                   |
| NIST CSF 2.0                                            | Voluntary US framework, used as guiding structure | Common language across Govern / Identify / Protect / Detect / Respond / Recover for board and cross-functional reporting                                             |

### 4.2. NIST CSF 2.0 Function Mapping

The table below shows how each CSF function is operationalized across IT and OT, and which control standard governs the detail.

| **CSF Function** | **IT Implementation**                                     | **OT Implementation**                                                                                                                | **Primary Standard**                           |
|------------------|-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| Govern (GV)      | ISMS policy suite, IT risk committee reporting            | OT Security Lead role, IEC 62443 policy & procedure (SP) requirements                                                                | ISO 27001 Cl. 5–6 / IEC 62443-2-1              |
| Identify (ID)    | CMDB, IT risk register                                    | OT asset inventory, Purdue-model network diagrams, HAZOP-informed risk register                                                      | ISO 27001 A.5.9 / IEC 62443-3-2                |
| Protect (PR)     | IAM/SSO, endpoint protection, DLP, cloud security posture | Zone/conduit segmentation, unidirectional gateways, engineering workstation hardening, compensating controls for unpatchable devices | IEC 62443-3-3 (SL targets) / ISO 27001 Annex A |
| Detect (DE)      | SIEM, EDR, cloud detection                                | OT-aware network monitoring (passive/non-intrusive), anomaly detection on control-system traffic                                     | IEC 62443-3-3 SR requirements                  |
| Respond (RS)     | IT incident response plan, SOC                            | OT incident response runbooks coordinated with safety/engineering, joint IT-OT incident bridge                                       | NIS2 Art. 23 reporting timelines               |
| Recover (RC)     | Backup/DR, business continuity                            | Manual fallback / islanding procedures, control-system restoration from validated gold images                                        | BSI KRITIS resilience requirements             |

## 5. Unified IT/OT Risk Management Methodology

Helios adopts a single risk management methodology, informed by NIST SP 800-30 (risk assessment) and ISO 31000 (risk management principles), applied consistently to IT and OT — but scored against domain-appropriate impact criteria, because a compromised billing server and a compromised substation RTU are not comparable on a purely financial scale.

### 5.1. Risk Appetite Statement

Helios has zero tolerance for risks that could plausibly cause loss of grid control, unsafe conditions for field personnel or the public, or sustained multi-district outage. Helios has low tolerance for risks to customer data confidentiality and regulatory compliance, and moderate tolerance for risks affecting non-critical corporate IT availability, provided compensating controls and recovery plans exist. Risk appetite is reviewed and re-approved by the Management Board annually.

### 5.2. Impact Criteria (Unified Scale, 1–5)

| **Level**      | **IT / Data Impact**                                                 | **OT / Grid Impact**                                              | **Safety & Public Impact**                             |
|----------------|----------------------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------|
| 5 – Critical   | Large-scale breach of customer PII/billing data; regulatory sanction | Loss of control over substation(s); multi-district outage \>4 hrs | Credible risk to life or public safety                 |
| 4 – Major      | Significant service disruption to billing/CRM \>24 hrs               | Loss of view (monitoring) over grid segment; localized outage     | Elevated risk requiring emergency response             |
| 3 – Moderate   | Departmental IT outage; contained data exposure                      | Degraded OT system performance; manual workaround required        | No immediate safety impact; precautionary action taken |
| 2 – Minor      | Isolated system issue, single user/team affected                     | Non-critical sensor/device failure with redundancy in place       | None                                                   |
| 1 – Negligible | Minimal, no service impact                                           | No operational effect                                             | None                                                   |

### 5.3. Risk Register Structure

A single, consolidated risk register spans both domains, with a domain tag (IT / OT / Shared) on every entry so that reporting can be sliced by domain while governance remains unified. Each entry records: Risk ID, Domain, Asset/Process affected, Threat, Vulnerability, Likelihood (1–5), Impact (1–5, per the scale above), Inherent Risk Score, Existing Controls, Residual Risk Score, Risk Owner, Treatment Plan, Target Date, and Status. Representative entries below illustrate the format; the full register is maintained as a living document outside this policy.

| **Risk ID** | **Domain** | **Risk Description**                                                                    | **Likelihood** | **Impact** | **Residual** | **Owner**        |
|-------------|------------|-----------------------------------------------------------------------------------------|----------------|------------|--------------|------------------|
| R-OT-014    | OT         | Unpatched legacy RTU firmware exploitable via newly networked remote monitoring link    | 4              | 5          | High         | OT Security Lead |
| R-OT-021    | OT         | Poorly inventoried vendor remote-access pathway into substation network                 | 4              | 5          | High         | OT Security Lead |
| R-IT-007    | IT         | Fragmented IAM allows orphaned accounts to persist across legacy and cloud systems      | 3              | 4          | Medium       | CISO             |
| R-SH-003    | Shared     | No consolidated IT/OT asset inventory delays incident scoping and regulatory reporting  | 4              | 4          | High         | GRC              |
| R-OT-030    | OT         | Smart meter fleet (multi-vendor) introduces heterogeneous, hard-to-patch attack surface | 4              | 4          | High         | OT Security Lead |
| R-IT-012    | IT         | Customer portal vulnerable to credential-stuffing due to absent MFA enforcement         | 3              | 3          | Medium       | CISO             |

### 5.4. Cadence

- OT risk register review: monthly, jointly by OT Security Lead and GRC.

- IT risk register review: monthly, jointly by CISO delegate and GRC.

- Consolidated risk report to IT/OT Security Governance Council: monthly.

- Consolidated risk report to Management Board: quarterly, or immediately upon a new critical/high risk.

## 6. Unified Asset Inventory and Classification

The absence of a consolidated asset inventory spanning IT and OT is treated as a foundational gap and a standalone priority workstream, because NIST CSF's Identify function, IEC 62443 zone design, and NIS2 risk-management obligations are all unachievable without it. Helios cannot report incident scope to BSI within the mandated 24-hour early-warning window if it does not know what asset was affected and what it connects to.

### 6.1. Inventory Architecture

- A single logical asset repository with two federated sources: the existing IT CMDB (extended to capture OT-adjacent IT, e.g., historian servers, engineering workstations) and a new OT Asset Repository purpose-built for ICS (capturing vendor, firmware version, protocol, safety criticality, and network zone).

- Both sources reconcile into a single Helios Asset Register maintained by GRC, queryable by domain, criticality, and location — this is the authoritative source for the risk register, incident response scoping, and regulatory reporting.

- Discovery method for OT assets uses passive network monitoring and engineering walk-downs rather than active scanning, in line with IEC 62443 guidance, to avoid destabilizing live control systems.

### 6.2. Classification Scheme

| **Tier**                               | **Description**                                                                       | **Examples**                                                   | **Minimum Control Baseline**                                                                     |
|----------------------------------------|---------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| Tier 0 — Safety & Grid-Critical OT     | Direct control over substation/distribution operations; safety-instrumented functions | SCADA master stations, substation RTUs/IEDs, protection relays | IEC 62443 SL2+ target, strict zone isolation, no direct internet exposure, 4-eyes change control |
| Tier 1 — Supporting OT / Grid-Adjacent | Monitoring, automation support, does not directly actuate the grid                    | Historians, engineering workstations, DMS, AMI head-end        | Segmented zone, hardened baseline, monitored remote access only                                  |
| Tier 2 — Critical IT                   | Regulatory, financial, or customer-data bearing                                       | Billing/ERP, customer portal, meter data management            | ISO 27001 Annex A full baseline, MFA, encryption at rest/in transit                              |
| Tier 3 — General IT                    | Standard corporate systems                                                            | Email, collaboration tools, internal websites                  | Standard corporate security baseline                                                             |

### 6.3. Required Attributes per Asset

Asset ID · Domain (IT/OT) · Tier · Owner (business and technical) · Physical/logical location · Network zone · Vendor & support status (including end-of-life/end-of-support date) · Firmware/software version · Connectivity (including any remote-access pathway) · Data classification handled · Safety criticality flag · Last verified date.

### 6.4. Milestones

1.  Complete OT engineering walk-down and passive discovery across all substations — target: rolling completion within 2 quarters, prioritized by district criticality.

2.  Reconcile IT CMDB against actual estate (address shadow IT) — target: 1 quarter.

3.  Stand up federated Helios Asset Register with GRC as data steward — target: concurrent with above.

4.  Establish quarterly re-verification cycle for Tier 0/1 assets; annual for Tier 2/3.

## 7. Identity, Access Management, and Network Segmentation

### 7.1. Unified Identity Governance

Helios's fragmented IAM landscape — separate identity stores for legacy OT systems, corporate Active Directory, and newer cloud applications — is consolidated under a single identity governance policy, without forcing every legacy OT system onto a common technical platform where doing so would be unsafe or unsupported by the vendor.

- A single authoritative source of truth for human identity (HR-driven joiner/mover/leaver process) feeds provisioning into both IT and OT identity stores, closing the gap where terminated employees or contractors retain OT system access.

- Role-based access control (RBAC) is mandatory for all Tier 0–2 systems; access is granted on least-privilege and need-to-operate basis, reviewed quarterly by asset owners.

- Privileged access to OT systems (engineering, configuration, firmware changes) requires named individual accounts (no shared/generic operator logins for auditable actions), multi-factor authentication where technically supportable, and session logging.

- Where legacy OT devices cannot support MFA or individual accounts, this is documented as a formal risk exception with compensating controls (e.g., physical access restriction, enhanced monitoring, jump-host logging) and reviewed by the IT/OT Security Governance Council.

### 7.2. Third-Party and Vendor Remote Access

Poorly inventoried vendor remote-access pathways into OT are treated as one of the highest-priority risks in this program (see R-OT-021). The following controls are mandatory:

5.  Every remote-access pathway into OT — VPN, vendor cloud portal, cellular modem, dial-up, or otherwise — must be registered in the Vendor Remote Access Inventory, with owner, business justification, and technical description.

6.  All vendor OT remote access routes through a centrally managed, brokered jump-host/PAM (privileged access management) solution — no direct vendor-to-device connections.

7.  Access is time-bound ("break-glass" or scheduled maintenance-window access only) and requires Helios-side approval and supervision for each session; standing/always-on vendor access is prohibited for Tier 0 assets.

8.  All vendor remote sessions are logged and retained per the incident response evidentiary requirements in Section 9.

9.  An immediate inventory sweep and decommissioning of any undocumented or legacy remote-access pathway is treated as a priority remediation item under this program.

### 7.3. Network Segmentation (IEC 62443 Zones and Conduits)

The IT/OT network boundary is redesigned around IEC 62443's zone and conduit model rather than the historical, informal "air gap" assumption, which the smart-grid rollout has already eroded.

- Enterprise Zone (corporate IT) and Industrial Zone (OT) are separated by a demilitarized zone (DMZ) with strictly defined, unidirectional-where-possible data flows for historian replication, reporting, and monitoring.

- Within the Industrial Zone, further segmentation into cell/area zones by substation grouping and function (control, safety, monitoring), each with defined conduits and access control at the boundary.

- All new smart-grid, smart-meter, and renewable-integration field devices connect through a dedicated, monitored IoT/field-device zone — never directly into the core SCADA network — with network access control and anomaly detection at the aggregation point.

- No direct internet exposure is permitted for Tier 0 assets under any circumstance, including vendor convenience access.

## 8. Third-Party and OT Supplier Risk Management

The multi-vendor smart-grid rollout materially expands Helios's third-party attack surface. This program establishes a formal Third-Party Risk Management (TPRM) lifecycle applied to all vendors, systems integrators, and OT equipment suppliers, scaled by the criticality of the access or product involved.

### 8.1. Vendor Risk Tiering

| **Tier**                             | **Criteria**                                                                                 | **Required Due Diligence**                                                                                                                                             |
|--------------------------------------|----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tier A — OT-Critical                 | Direct access to Tier 0 OT assets, or supplies components embedded in grid-control functions | Pre-contract security assessment, IEC 62443-4-1/4-2 evidence for products, on-site or remote audit rights, mandatory incident notification clause, annual reassessment |
| Tier B — OT-Supporting / IT-Critical | Access to Tier 1 OT or Tier 2 IT systems; handles regulated data                             | Security questionnaire (ISO 27001-aligned), evidence of certification or equivalent controls, contractual right-to-audit, biennial reassessment                        |
| Tier C — General                     | No access to sensitive systems or data                                                       | Standard procurement security clause, baseline questionnaire at onboarding                                                                                             |

### 8.2. Lifecycle Requirements

10. Pre-engagement: security and privacy risk assessment scaled to tier; results feed the vendor's entry in the Vendor Risk Register (a domain-tagged extension of the unified risk register).

11. Contracting: mandatory security clauses — right to audit, incident notification within a contractually defined window aligned to Helios's own NIS2 reporting clock, minimum patching/support commitments, and data handling requirements.

12. Onboarding: remote access provisioned per Section 7.2; no access granted before the vendor's risk assessment and access registration are complete.

13. Ongoing monitoring: Tier A vendors reassessed annually, Tier B biennially, or immediately following a relevant security incident at the vendor or a disclosed vulnerability in their product.

14. Offboarding: access revocation is a mandatory, tracked step in contract termination or project close-out; verified by GRC, not assumed complete by default.

### 8.3. OT Equipment Supply Chain

For smart meters, grid-automation sensors, and renewable-integration platform components, Helios requires suppliers to provide a software/firmware bill of materials (SBOM) where feasible, evidence of secure development practices consistent with IEC 62443-4-1, and a defined vulnerability disclosure and patch-notification process. Multi-vendor heterogeneity is managed by requiring all field devices to conform to a common Helios security baseline specification prior to procurement approval, regardless of vendor.

## 9. Incident Response and Regulatory Reporting

Helios operates a single, joint IT/OT incident response process. A cyber incident affecting OT is treated as both a safety event and a security event from the first moment of detection — the OT Security Lead and site safety/engineering leadership are on every OT-related incident bridge alongside the CISO's incident commander.

### 9.1. Incident Classification

| **Severity**     | **Definition**                                                                           | **Example**                                                                            |
|------------------|------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| SEV-1 — Critical | Confirmed or suspected loss of control/view over grid systems, or any safety implication | Malware confirmed on SCADA network; unauthorized command issued to a substation device |
| SEV-2 — High     | Significant IT or OT disruption without confirmed grid-control impact                    | Ransomware in corporate IT segment; anomalous traffic at IT/OT boundary                |
| SEV-3 — Moderate | Contained incident, limited scope                                                        | Phishing compromise of a single non-privileged account                                 |
| SEV-4 — Low      | Minor policy violation or false positive requiring documentation only                    | Isolated failed login anomaly, resolved                                                |

### 9.2. NIS2 / BSI Regulatory Reporting Timeline

For incidents meeting the NIS2 significant-incident threshold, Helios follows the mandatory reporting timeline to BSI as the competent authority:

| **Deadline**                         | **Report**                                                                                                            | **Owner**                                 |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| Within 24 hours of awareness         | Early warning — initial notification, indicating suspected unlawful/malicious cause and potential cross-border effect | CISO (regulatory point of contact)        |
| Within 72 hours of awareness         | Incident notification — updated assessment, initial severity/impact, indicators of compromise where available         | CISO with GRC support                     |
| Within 1 month of the 72-hour report | Final report — detailed description, root cause, mitigation measures, cross-border impact assessment                  | GRC, with CISO and OT Security Lead input |

KRITIS/BSIG §8b obligations run in parallel and are satisfied by the same reporting process; Helios maintains a single incident evidence package per event, sufficient to satisfy both NIS2 and KRITIS documentation expectations, avoiding duplicated or inconsistent reporting.

### 9.3. Joint IT/OT Response Principles

- Safety takes precedence over evidence preservation and forensic ideals — OT engineering has authority to take a system to a safe state even if this affects forensic artifacts, per documented playbooks agreed in advance with the CISO's office.

- Isolation actions on OT networks require joint sign-off from the incident commander and OT Security Lead to avoid unintended cascading grid effects.

- A pre-approved communication plan covers regulator (BSI), customer, and public communications, coordinated through the CISO and corporate communications, avoiding uncoordinated disclosure that could trigger secondary risk (e.g., signaling grid vulnerability publicly during an active incident).

- Post-incident reviews are mandatory for SEV-1 and SEV-2 events and feed corrective actions directly into the unified risk register with tracked remediation owners and dates.

## 10. Patch, Change, and Vulnerability Management

Helios recognizes that standard IT patch cadences cannot be applied uniformly to OT, where uptime and safety are paramount and many control systems cannot be patched without vendor-qualified testing, or cannot be patched at all due to end-of-support status. This program formalizes a risk-based, compensating-control approach rather than treating OT non-patching as an unmanaged exception.

### 10.1. IT Patch Management

Standard patch SLAs apply: critical vulnerabilities on internet-facing or Tier 2 systems remediated within 14 days; high within 30 days; routine patching on a monthly cycle, tested in a staging environment before production deployment.

### 10.2. OT Patch and Change Management

15. All OT patches and firmware updates are evaluated first for safety and operational impact by OT engineering before any security-driven timeline is applied; no patch is deployed to Tier 0 systems without vendor validation and a scheduled maintenance window.

16. Where a vulnerability cannot be patched (unsupported/legacy device, vendor has not released a fix, or patching would void safety certification), a formal compensating-control record is created: e.g., network isolation/segmentation, enhanced monitoring, restricted physical/logical access, or virtual patching at a network boundary.

17. Every unpatched Tier 0/1 vulnerability with a compensating control is logged in the unified risk register with an owner, compensating-control description, and scheduled reassessment date — it is never simply closed or ignored.

18. Emergency changes to OT systems in direct response to an active threat follow an expedited but still dual-authorized (security + engineering) approval path, documented after the fact if immediate action was required for safety.

### 10.3. Vulnerability Management

- IT vulnerability scanning is continuous/automated across corporate networks and cloud infrastructure.

- OT vulnerability identification relies primarily on passive network monitoring, vendor security bulletins, and ICS-specific threat intelligence (e.g., BSI CERT advisories, ICS-CERT equivalents) rather than active scanning, which is only performed on Tier 0/1 systems with documented engineering approval and during scheduled windows.

## 11. Security Awareness and Workforce Training

A single awareness program with domain-specific tracks ensures both corporate staff and OT engineers understand their role in the governance program.

- All staff: annual security awareness training, phishing simulation, and data protection refreshers, aligned to ISO 27001 Annex A competence requirements.

- OT engineers and technicians: dedicated ICS security awareness track covering safe remote-access practice, recognizing anomalous HMI/SCADA behavior, and the escalation path to the OT Security Lead — delivered without requiring OT staff to become general IT security practitioners.

- Vendor and third-party personnel with OT access: mandatory security briefing prior to first access, refreshed annually for standing engagements.

- Executive and Management Board: tabletop exercises simulating a NIS2-reportable OT incident, at least annually, to exercise governance decision-making and regulatory reporting timelines under realistic pressure.

## 12. Audit, Assurance, and Regulatory Readiness

### 12.1. Internal Audit Program

- GRC maintains a rolling internal audit calendar covering ISO 27001 Annex A controls, IEC 62443 zone/conduit conformance, IAM/access reviews, and vendor remote-access inventory accuracy.

- Internal Audit function performs independent testing at least annually, with findings tracked to closure in the same governance forum (IT/OT Security Governance Council) as risk register items — audit findings are risk register entries, not a separate parallel process.

### 12.2. External / Regulatory Audit Readiness

Helios prepares continuously, not reactively, for BSIG §8a KRITIS audits (required at least every two years) and NIS2 supervisory examinations. Readiness activities include:

19. Maintaining an always-current evidence repository mapped to each applicable control (ISO 27001 Statement of Applicability, IEC 62443 SL assessments, NIS2 Article 21 risk-measures documentation) so evidence can be produced on request rather than assembled under audit pressure.

20. Conducting an annual internal "mock audit" against the BSIG §8a criteria, led by GRC with Internal Audit oversight, at least two quarters ahead of any known external audit window.

21. Ensuring the asset inventory (Section 6) and risk register (Section 5) — the two artifacts regulators most consistently request — are demonstrably current, owned, and versioned at all times.

22. Designating the CISO as the single point of contact for BSI and other regulators, with GRC providing evidence coordination, to ensure consistent, accurate regulatory communication.

### 12.3. Certification Roadmap

Helios targets ISO/IEC 27001:2022 certification for the corporate IT ISMS as the near-term milestone, followed by extension of the management system's risk methodology (though not necessarily certification scope) to cover OT governance processes, with IEC 62443 conformance assessments applied directly to OT zones as the technical control standard. This sequencing reflects that ISO 27001 certification demonstrates governance maturity to regulators and customers while IEC 62443 provides the engineering-level assurance appropriate to control systems.

## 13. Metrics, KPIs, and Board Reporting

The following metrics are reported to the IT/OT Security Governance Council monthly and to the Management Board quarterly, giving early warning of governance program health rather than relying solely on lagging incident counts.

| **Metric**                                                                            | **Target**                          | **Domain** |
|---------------------------------------------------------------------------------------|-------------------------------------|------------|
| % of IT/OT assets in the unified inventory with verified attributes (\<12 months old) | ≥95%                                | Shared     |
| % of vendor remote-access pathways formally registered and brokered through PAM       | 100%                                | Shared     |
| Number of open Tier 0/1 vulnerabilities without a documented compensating control     | 0                                   | OT         |
| Mean time to detect (MTTD) for OT network anomalies                                   | Trending down, quarter over quarter | OT         |
| % of SEV-1/SEV-2 incidents meeting NIS2 24-hour early-warning deadline                | 100%                                | Shared     |
| % of privileged OT accounts using named individual credentials (vs. shared/generic)   | ≥95%, all exceptions documented     | OT         |
| Overdue risk register remediation items (past target date)                            | 0 for High/Critical                 | Shared     |
| Third-party (Tier A/B) vendors with current risk assessment                           | 100%                                | Shared     |

## 14. Policy Governance, Review, and Change Management

- This document is reviewed at least annually by the CISO and GRC function, and immediately following: a material regulatory change (e.g., updated NIS2 implementing acts or BSI guidance), a significant incident, or a material change to Helios's IT or OT architecture.

- All changes are version-controlled, with a summary changelog maintained as an appendix, and re-approved by the Management Board before taking effect.

- Subordinate policies and standards (e.g., the OT Remote Access Standard, the Vendor Risk Management Procedure, the Incident Response Plan) are maintained as separate operational documents beneath this governance program and must remain consistent with it; conflicts are escalated to the IT/OT Security Governance Council for resolution.

### 14.1. Document Approval

| **Role**    | **Name / Title**                             | **Signature** | **Date** |
|-------------|----------------------------------------------|---------------|----------|
| Prepared by | GRC Analyst, Information Security Compliance |               |          |
| Reviewed by | Chief Information Security Officer           |               |          |
| Reviewed by | Head of OT Engineering                       |               |          |
| Approved by | Management Board (Vorstand)                  |               |          |

## Appendix A — Glossary of Terms

| **Term**            | **Definition**                                                                                                                               |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| AMI                 | Advanced Metering Infrastructure — the smart meter ecosystem, including meter data management and head-end systems                           |
| BSI                 | Bundesamt für Sicherheit in der Informationstechnik — Germany's Federal Office for Information Security, the NIS2/KRITIS competent authority |
| CSF                 | NIST Cybersecurity Framework — six-function structure (Govern, Identify, Protect, Detect, Respond, Recover)                                  |
| DMS                 | Distribution Management System                                                                                                               |
| IEC 62443           | International standard series for security of Industrial Automation and Control Systems                                                      |
| KRITIS              | Kritische Infrastrukturen — Germany's critical infrastructure regulatory regime under the BSI-KritisV                                        |
| NIS2                | EU Directive (2022/2555) on measures for a high common level of cybersecurity across the Union                                               |
| OT / ICS            | Operational Technology / Industrial Control Systems                                                                                          |
| PAM                 | Privileged Access Management                                                                                                                 |
| RTU / IED           | Remote Terminal Unit / Intelligent Electronic Device — field devices controlling or monitoring substation equipment                          |
| SCADA               | Supervisory Control and Data Acquisition — the system(s) used to monitor and control grid operations                                         |
| SL (Security Level) | IEC 62443 rating (SL0–SL4) describing the resistance of a zone or component to a defined threat capability                                   |
| Zone / Conduit      | IEC 62443 concept: a zone groups assets with common security requirements; a conduit is a controlled communication path between zones        |
