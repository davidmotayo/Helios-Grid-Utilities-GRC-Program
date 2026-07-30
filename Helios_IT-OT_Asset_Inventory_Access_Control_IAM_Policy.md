**HELIOS GRID UTILITIES**

Regional Electricity Distribution Operator — Frankfurt, Germany

**IT/OT ASSET INVENTORY, ACCESS CONTROL &**

**IDENTITY AND ACCESS MANAGEMENT POLICY**

**Document Classification: CONFIDENTIAL — Internal Use Only**

# **Document Control**

| **Field**      | **Detail**                                                                                                   |
|----------------|--------------------------------------------------------------------------------------------------------------|
| Document Title | IT/OT Asset Inventory, Access Control & IAM Policy                                                           |
| Owner          | Chief Information Security Officer (CISO), Helios Grid Utilities                                             |
| Prepared By    | GRC Analyst — Cybersecurity Governance Team                                                                  |
| Approved By    | CISO; OT Security Lead; Head of IT Operations                                                                |
| Classification | Confidential — Internal Use Only                                                                             |
| Version        | 1.0                                                                                                          |
| Effective Date | 22 July 2026                                                                                                 |
| Review Cycle   | Annual, or upon material change to IT/OT architecture, regulatory scope, or following a significant incident |

# **1. Executive Summary**

Helios Grid Utilities operates a regional electricity distribution network serving approximately 1.4 million households and businesses across Frankfurt and surrounding districts. The organization is midway through a major modernization programme — smart meters, grid-automation sensors, distributed energy resource (DER) integration — while continuing to operate a legacy SCADA/ICS estate that controls physical grid infrastructure. This creates a converged IT/OT risk surface that current governance does not yet address as a single programme.

This document establishes the foundational control set required to close that gap: (1) a unified asset inventory spanning corporate IT, OT/ICS, and internet-connected field devices; (2) an access control model appropriate to each environment's risk profile, including third-party and vendor remote access into OT; and (3) an Identity and Access Management (IAM) policy that governs identity lifecycle, authentication, authorization, and access assurance across both domains.

The deliverable is structured to serve as direct audit evidence for NIS2 Article 21 risk-management measures and German BSI/KRITIS governance obligations, and maps every control domain to IEC 62443, ISO/IEC 27001:2022, and NIST CSF 2.0 for cross-framework traceability.

# **2. Purpose and Scope**

## **2.1 Purpose**

To provide Helios Grid Utilities with a documented, auditable baseline of (a) all IT, OT, and field-device assets material to grid operations and customer service, and (b) the access control and identity governance model that protects those assets, in support of the organization's obligations under NIS2, BSI/KRITIS, and applicable ISO/IEC 27001 and IEC 62443 requirements.

## **2.2 Scope**

This policy applies to:

- All corporate IT systems, applications, and infrastructure (email, ERP, billing, customer portal, data centre, endpoints).

- All OT/ICS systems supporting substation and distribution grid control (SCADA, DMS, RTUs, protection relays, HMIs, engineering workstations, OT network infrastructure).

- All internet-connected smart-grid field devices (smart meters, AMI head-end, grid-automation sensors, DER gateways, remote monitoring sensors), regardless of vendor.

- All employees, contractors, and third-party vendors who access any of the above, whether on-site or remote.

- Excludes: physical construction/civil infrastructure with no digital control interface; assets of independent power producers not under Helios operational control.

# **3. Regulatory and Framework Alignment**

Helios Grid Utilities is designated critical infrastructure under German KRITIS regulation and falls within scope of the EU NIS2 Directive as an essential entity in the energy sector. The organization is therefore subject to:

- NIS2 Directive (EU 2022/2555) — risk-management measures (Art. 21) and incident reporting obligations (Art. 23), transposed into German law via the NIS2 Umsetzungsgesetz (NIS2UmsuCG).

- BSI Act (BSIG) and KRITIS-Verordnung — sector-specific critical-infrastructure obligations enforced by the Bundesamt für Sicherheit in der Informationstechnik (BSI).

- IEC 62443 series — the international standard for security of industrial automation and control systems (IACS), applied to the OT/ICS estate.

- ISO/IEC 27001:2022 — enterprise information security management system (ISMS), applied primarily to corporate IT and as the umbrella framework for the security programme.

- NIST Cybersecurity Framework 2.0 — used internally as the guiding framework to structure governance, identify, protect, detect, respond, and recover functions across both IT and OT.

Section 8 provides a full control-domain mapping across these five frameworks.

# **4. IT/OT Asset Inventory**

## **4.1 Methodology**

The inventory consolidates assets previously tracked separately (or not at all) by corporate IT and OT engineering into a single register, using a common schema: Asset ID, Asset/System name, Category, Function, Criticality Tier, Network Zone, and either Data Sensitivity (IT) or Patch/Support Status (OT) — reflecting that IT risk is data-centric while OT risk is availability- and safety-centric. Field devices are tracked separately given their volume, multi-vendor nature, and distinct connectivity model.

Asset owners (named role, not individual) are assigned for every entry in the full working register; this document presents the consolidated view. The full register is maintained in the GRC platform / CMDB and reconciled quarterly against network discovery scans (IT) and OT engineering change logs (OT).

## **4.2 Asset Criticality Tiering**

| **Tier**                    | **Definition**                                                                                   | **Example Assets**                                                                 | **Availability Target**             |
|-----------------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|-------------------------------------|
| Critical (Safety-Impacting) | Loss or compromise could cause physical grid disruption, safety hazard, or multi-district outage | SCADA, DMS, RTUs, protection relays, OT firewalls, vendor jump boxes               | Near-continuous; failover mandatory |
| High                        | Loss would materially disrupt operations, regulatory standing, or expose sensitive data at scale | Historian, HMI, engineering workstations, ERP, billing, AMI head-end, DER gateways | High availability; defined RTO/RPO  |
| Medium                      | Disruption causes operational inconvenience without safety or large-scale service impact         | Corporate endpoints, individual smart meters, HR system                            | Standard business continuity        |
| Low                         | Limited business or operational consequence                                                      | General office IT peripherals, non-production test systems                         | Best-effort                         |

## **4.3 Corporate IT Asset Inventory**

| **Asset ID** | **Asset / System**                      | **Category**            | **Function**                                 | **Criticality** | **Network Zone**              | **Data Sensitivity**       |
|--------------|-----------------------------------------|-------------------------|----------------------------------------------|-----------------|-------------------------------|----------------------------|
| IT-AST-001   | Corporate Email (M365)                  | Productivity/Cloud      | Enterprise email & collaboration             | Medium          | Corporate IT / Cloud          | Internal / PII             |
| IT-AST-002   | ERP Platform (SAP)                      | Business Application    | Finance, HR, procurement, asset accounting   | High            | Corporate IT / Data Centre    | Confidential               |
| IT-AST-003   | Customer Billing System                 | Business Application    | Billing, metering-to-cash, invoicing         | High            | Corporate IT / Data Centre    | Restricted (PII + billing) |
| IT-AST-004   | Customer Web/Mobile Portal              | Customer-Facing App     | Self-service account & usage portal          | High            | DMZ / Cloud                   | Restricted (PII)           |
| IT-AST-005   | Active Directory / Identity Store       | Identity Infrastructure | Corporate IT authentication & directory      | Critical        | Corporate IT Core             | Confidential               |
| IT-AST-006   | Corporate Data Centre Servers           | Infrastructure          | Virtualization hosts, file/print, DB servers | High            | Corporate IT / Data Centre    | Confidential               |
| IT-AST-007   | Corporate Endpoints (laptops/desktops)  | End-user Compute        | Staff productivity devices                   | Medium          | Corporate IT                  | Internal                   |
| IT-AST-008   | Corporate Firewalls / VPN Concentrators | Network Security        | Perimeter defence, remote access             | High            | Corporate IT Perimeter        | Confidential (config)      |
| IT-AST-009   | SIEM / Security Monitoring Platform     | Security Infrastructure | Log aggregation, detection, alerting         | High            | Corporate IT / SOC            | Confidential               |
| IT-AST-010   | Renewable-Integration Platform (Cloud)  | Business Application    | Forecasting & DER/renewables integration     | High            | Cloud / DMZ to OT Historian   | Confidential (grid data)   |
| IT-AST-011   | Backup & DR Infrastructure              | Infrastructure          | Enterprise backup, replication               | High            | Corporate IT / Secondary Site | Confidential               |
| IT-AST-012   | HR / Payroll System                     | Business Application    | Employee records, payroll                    | Medium          | Corporate IT                  | Restricted (PII)           |

## **4.4 OT/ICS Asset Inventory**

Note: several OT assets are flagged as unsupported, end-of-life (EOL), or with incomplete vendor patching — these are formally logged in the enterprise risk register with compensating controls (network segmentation, monitoring, restricted access) pending remediation or replacement.

| **Asset ID** | **Asset / System**                          | **Category**                 | **Function**                                          | **Criticality**   | **Purdue Zone / Network**      | **Patch/Support Status**                  |
|--------------|---------------------------------------------|------------------------------|-------------------------------------------------------|-------------------|--------------------------------|-------------------------------------------|
| OT-AST-001   | SCADA Master Station                        | Control System               | Centralized monitoring & control of distribution grid | Critical (Safety) | Level 2 – Control Centre LAN   | Vendor-supported; quarterly patch window  |
| OT-AST-002   | Substation RTUs (fleet)                     | Field Controller             | Remote terminal units at distribution substations     | Critical (Safety) | Level 1 – Substation LAN       | Mixed: partly EOL, vendor-dependent       |
| OT-AST-003   | Protection Relays (IEDs)                    | Field Controller             | Fault detection & protective switching                | Critical (Safety) | Level 0/1 – Substation Bay     | Legacy; firmware updates rare/unsupported |
| OT-AST-004   | Distribution Management System (DMS)        | Control System               | Network topology, switching, outage management        | Critical          | Level 2 – Control Centre LAN   | Vendor-supported                          |
| OT-AST-005   | Historian Server                            | Data System                  | Time-series operational data archive                  | High              | Level 3 – OT DMZ               | Vendor-supported                          |
| OT-AST-006   | HMI Workstations                            | Operator Interface           | Operator monitoring & control screens                 | Critical          | Level 2 – Control Centre LAN   | Legacy OS versions in use                 |
| OT-AST-007   | Engineering Workstations                    | Engineering Tooling          | RTU/PLC configuration and firmware loading            | High              | Level 2/3 – OT Engineering LAN | Vendor-supported; irregular patching      |
| OT-AST-008   | OT Firewalls / Data Diodes                  | Network Security             | IT/OT segmentation, unidirectional data flow          | Critical          | Level 3.5 – IT/OT DMZ          | Vendor-supported                          |
| OT-AST-009   | Legacy Serial-to-IP Gateways                | Network Infrastructure       | Bridges legacy serial RTUs onto IP network            | High              | Level 1/2                      | Unsupported / EOL — high risk             |
| OT-AST-010   | Vendor Remote-Access Jump Boxes             | Remote Access Infrastructure | Third-party maintenance access to OT                  | Critical          | Level 3.5 – OT DMZ             | Inventory incomplete — priority gap       |
| OT-AST-011   | Building/Substation Physical Access Control | Physical Security System     | Badge access & CCTV at substations                    | High              | Corporate/OT shared            | Vendor-supported                          |

## **4.5 Smart Grid / Field Device Inventory**

The smart-meter and grid-automation rollout introduces a high-volume, multi-vendor device population. These are inventoried at the platform/fleet level (not per-serial-number) with device-class risk ratings; individual device provisioning is tracked in the AMI/DER management platforms and reconciled monthly.

| **Asset ID** | **Device / Platform**                           | **Vendor Model**               | **Function**                                         | **Connectivity**                   | **Criticality**                         | **Key Risk**                                              |
|--------------|-------------------------------------------------|--------------------------------|------------------------------------------------------|------------------------------------|-----------------------------------------|-----------------------------------------------------------|
| FD-AST-001   | Smart Meters (AMI)                              | Multi-vendor (3 approved OEMs) | Consumption metering, remote read, outage signalling | Cellular / RF mesh to AMI head-end | Medium (individually); High (aggregate) | Fleet-wide firmware vulnerability; billing data integrity |
| FD-AST-002   | AMI Head-End System                             | Vendor-managed platform        | Aggregates meter data, sends to billing & DMS        | Cloud / MPLS to Corporate & OT DMZ | High                                    | Bridges customer & OT data domains                        |
| FD-AST-003   | Grid-Automation Sensors (FLISR)                 | Multi-vendor IIoT sensors      | Fault location, isolation, service restoration       | Cellular/LPWAN to DMS              | High                                    | Unmanaged device sprawl; weak inventory                   |
| FD-AST-004   | Distributed Energy Resource (DER) Gateways      | Multi-vendor                   | Interfaces solar/storage assets to grid platform     | Internet-facing APIs               | High                                    | Internet exposure; inconsistent vendor security posture   |
| FD-AST-005   | Remote Monitoring Sensors (transformers, lines) | Multi-vendor IIoT              | Condition monitoring, predictive maintenance         | Cellular/LPWAN to Cloud Historian  | Medium                                  | Weak default credentials; unmanaged onboarding            |

## **4.6 Network Zone Architecture**

Helios adopts the IEC 62443 / Purdue Model reference architecture to define network zones and conduits between IT and OT:

- Level 4/5 — Enterprise IT: corporate applications, email, ERP, billing, customer portal, internet connectivity.

- Level 3.5 — IT/OT DMZ: historian replication, patch/AV relay, vendor remote-access jump boxes, data diodes; the sole permitted conduit between Enterprise IT and the OT environment.

- Level 3 — OT Operations Management: engineering workstations, OT historian, DMS.

- Level 2 — Control Centre / Substation LAN: SCADA master station, HMIs.

- Level 1 — Basic Control: RTUs, protection relays (IEDs).

- Level 0 — Process/Field: physical switchgear, sensors, actuators.

Field devices (smart meters, grid-automation sensors, DER gateways) connect via dedicated cellular/LPWAN networks into AMI/DER head-end platforms hosted in the IT/OT DMZ or cloud — they do not have direct network paths into Level 0–2 control systems. This segmentation is the primary compensating control for field-device and vendor-related risk pending full lifecycle remediation of legacy OT assets.

# **5. Access Control Policy**

## **5.1 Purpose**

This policy defines the rules by which access to IT and OT systems is granted, restricted, and reviewed, ensuring that access is limited to what each role requires to perform its function (least privilege), that no individual can unilaterally execute a complete high-risk transaction or control action (segregation of duties), and that OT safety and availability are never subordinated to IT-style convenience access.

## **5.2 Core Principles**

- Least privilege — access is granted at the minimum level required for the role, by default deny.

- Need-to-know — access to sensitive data (customer PII, grid topology, control logic) is limited to roles with an operational requirement.

- Segregation of duties (SoD) — access request, approval, provisioning, and audit functions are performed by different parties; OT operational control and OT engineering/configuration roles are held by different individuals.

- OT-specific: safety and availability primacy — no access change may be implemented in the OT environment without OT engineering sign-off confirming it will not compromise system stability or safety interlocks, regardless of urgency.

- Time-bound and supervised access for all third parties — no standing/persistent vendor access into OT is permitted.

## **5.3 IT Access Control Matrix (Illustrative)**

| **Role**              | **Email/Collab**      | **ERP/Finance**          | **Billing System**    | **Customer Portal Admin**      | **Corporate Servers/AD** | **SIEM** |
|-----------------------|-----------------------|--------------------------|-----------------------|--------------------------------|--------------------------|----------|
| General Staff         | Read/Write            | None                     | None                  | None                           | None                     | None     |
| Finance/HR Staff      | Read/Write            | Read/Write (role-scoped) | Read (reporting only) | None                           | None                     | None     |
| Billing Operations    | Read/Write            | Read                     | Read/Write            | None                           | None                     | None     |
| Customer Ops/Support  | Read/Write            | None                     | Read                  | Read/Write (support functions) | None                     | None     |
| IT Administrators     | Admin                 | None (segregated)        | None (segregated)     | Admin (infra only)             | Admin                    | Read     |
| Security/SOC Analysts | Read (investigations) | None                     | None                  | Read (logs)                    | Read                     | Admin    |
| Executives            | Read/Write            | Read (dashboards)        | Read (dashboards)     | None                           | None                     | None     |

## **5.4 OT Access Control Matrix (Illustrative)**

| **Role**                         | **HMI (View)**                                       | **HMI (Control/Switching)**             | **Engineering Workstation**              | **RTU/IED Firmware**                           | **OT Historian** | **OT Firewall/Diode Config**           |
|----------------------------------|------------------------------------------------------|-----------------------------------------|------------------------------------------|------------------------------------------------|------------------|----------------------------------------|
| Control Room Operator            | Read/Write (monitor + switching per authority level) | Yes, within authorized switching limits | None                                     | None                                           | Read             | None                                   |
| Shift Supervisor                 | Read/Write                                           | Yes, full switching authority           | None                                     | None                                           | Read             | None                                   |
| OT/ICS Engineer                  | Read                                                 | No (segregated from operations)         | Read/Write                               | Read/Write (change-controlled)                 | Read/Write       | Request only (approved by OT Security) |
| OT Security Engineer             | Read (monitoring)                                    | No                                      | Read                                     | Read (audit)                                   | Read             | Admin                                  |
| Third-Party Vendor (maintenance) | None (unless supervised session)                     | No                                      | Supervised, time-boxed, session-recorded | Supervised, time-boxed, change-ticket required | None             | None                                   |
| IT Administrators                | None                                                 | No                                      | None                                     | None                                           | None             | None (OT-segregated identities)        |

## **5.5 Remote Access and Third-Party/Vendor Access Controls**

Vendor remote access into OT is currently the most significant identified control gap: pathways are poorly inventoried, several are believed to bypass the OT DMZ, and access is not consistently time-bound. The following controls are mandated:

- All vendor/OT-supplier remote access routes must be inventoried in the vendor remote-access register (owner: OT Security Lead), including vendor name, system(s) accessed, access method, and business justification.

- All vendor remote access terminates at the OT DMZ jump box (OT-AST-010) — no vendor connection may bridge directly from the internet or corporate IT into Level 0–2 OT networks.

- Access is granted per-engagement, time-boxed to the maintenance window, and automatically expires; no standing vendor credentials are permitted.

- All vendor sessions are supervised by an authorized OT engineer and session-recorded; recordings are retained per the organization's log retention standard.

- Multi-factor authentication (MFA) is mandatory for all remote access, including vendor access, with no exceptions.

- A named internal sponsor is accountable for each vendor's access and must re-approve it at each engagement and at each quarterly review.

## **5.6 Privileged Access Management**

- Privileged (administrative) accounts on IT and OT systems are separate from standard user accounts — no shared credentials, no use of privileged accounts for routine tasks (e.g., email).

- Privileged access to SCADA, DMS, RTU/IED configuration, and OT firewalls is restricted to named OT Security Engineers and OT/ICS Engineers, and requires dual-authorization for firmware or configuration changes affecting Critical-tier assets.

- Privileged sessions on Critical-tier IT and OT assets are logged and, where technically supported, recorded via a privileged access management (PAM) solution.

- Break-glass (emergency access) procedures exist for OT control-room continuity but require post-use justification and review within 24 hours.

# **6. Identity and Access Management (IAM) Policy**

## **6.1 Purpose and Scope**

This policy establishes how digital identities are created, authenticated, authorized, reviewed, and retired across Helios's fragmented identity landscape — separate directories for corporate IT, OT domains, and vendor/AMI platforms — with the objective of consolidating governance (not necessarily infrastructure) under a single set of enforceable rules ahead of full IAM platform convergence.

## **6.2 Roles and Responsibilities**

- CISO — policy owner; accountable for overall IAM and access control governance across IT and OT.

- OT Security Lead — accountable for identity and access governance within the OT/ICS environment; co-owns any control affecting Level 0–3 systems.

- IT Operations — executes provisioning/deprovisioning for corporate IT identities; maintains Active Directory and related identity infrastructure.

- OT/ICS Engineering — executes provisioning/deprovisioning within OT systems; validates that access changes do not affect control-system stability.

- Line Managers — initiate and approve access requests for their direct reports; accountable for timely notification of role changes and departures.

- GRC/Compliance — maintains the policy, coordinates access recertification campaigns, and prepares audit evidence.

- Vendor Management — maintains the vendor register and coordinates third-party access sponsorship and offboarding.

## **6.3 Identity Lifecycle — Joiners, Movers, Leavers**

### **Joiners**

- Access is provisioned only after HR confirms start date and line-manager-approved role/system requirements; provisioning follows the applicable access control matrix (Section 5) by default.

- OT system access for new employees or transferred staff requires OT Security Lead approval in addition to line-manager approval, regardless of prior IT access levels.

### **Movers**

- Role changes trigger a mandatory access review within 5 business days; access rights tied to the prior role are removed, not merely supplemented — access must not accumulate across role changes.

### **Leavers**

- IT access is disabled on last working day, coordinated by HR notification to IT Operations, with a maximum permitted delay of 24 hours.

- OT system access and physical substation access are disabled on last working day with no exception, given safety implications of standing OT credentials; disablement is confirmed jointly by OT Security Lead and IT Operations.

- Vendor personnel changes are the vendor's contractual obligation to report within 24 hours; Helios additionally enforces expiry via time-boxed access per Section 5.5.

## **6.4 Authentication Standards**

- Multi-factor authentication (MFA) is mandatory for: all remote access (IT and OT), all privileged/administrative accounts, all vendor access, and all access to systems handling customer PII or grid-control functions.

- Password policy (where MFA cannot be layered on legacy OT systems due to technical constraints): minimum 14 characters, complexity enforced, no reuse of last 12 passwords, mandatory change on suspected compromise. Fixed-interval forced rotation is not required where MFA and monitoring are in place, consistent with current NIST guidance; legacy OT systems without MFA retain periodic rotation as a compensating control.

- Shared/generic accounts are prohibited on IT systems without exception. Where legacy OT equipment technically requires a shared local account, compensating controls (physical/network access restriction, session logging, restricted scope) must be documented and approved by the OT Security Lead.

- Single sign-on (SSO) is the target state for corporate IT; OT systems remain on isolated authentication domains by design, consistent with IEC 62443 zone segregation.

## **6.5 Authorization and Role-Based Access Control**

Access is granted through role-based access control (RBAC) aligned to the matrices in Section 5. Direct-to-individual entitlement grants outside an approved role profile require documented business justification and CISO (IT) or OT Security Lead (OT) approval, and are logged as exceptions (Section 6.10).

## **6.6 Segregation of Duties (SoD)**

- Access requestors cannot approve their own requests; approvers cannot provision their own approvals.

- OT operational control (switching authority) and OT engineering/configuration access are held by mutually exclusive roles.

- Billing system write access and financial reconciliation/audit access are held by mutually exclusive roles.

- IAM administrators (who provision access) are distinct from SIEM/security monitoring administrators (who audit access) to prevent self-concealment.

## **6.7 Third-Party and Vendor Identity Management**

- Every vendor identity is linked to a named internal sponsor and a specific, time-bound business justification (per Section 5.5).

- Vendor identities are provisioned in a segregated identity namespace, never granted membership in internal privileged groups.

- Multi-vendor smart-grid field-device platforms (AMI, DER gateways) are governed by vendor-specific service accounts with scope limited to their platform only; no cross-platform credential reuse.

- Annual (minimum) third-party security assessment is required for any vendor holding standing access to OT-adjacent systems (e.g., AMI head-end, historian replication).

## **6.8 Access Review and Recertification**

- Quarterly access recertification for all Critical- and High-tier IT and OT systems, performed by system/business owners and evidenced for audit.

- Semi-annual recertification for Medium/Low-tier systems.

- Vendor access is recertified at every engagement renewal and, at minimum, quarterly regardless of engagement status.

- Recertification findings (orphaned accounts, excess entitlements, unapproved standing access) are logged in the risk register with named remediation owners and dates.

## **6.9 Logging, Monitoring, and Audit**

- All authentication events, privileged actions, and access changes on Critical- and High-tier assets are logged and forwarded to the SIEM (IT-AST-009) where technically feasible.

- Legacy OT assets unable to forward logs natively are monitored via compensating network-level detection at the OT DMZ boundary.

- Logs are retained for a minimum of 12 months (or longer where required by BSI/KRITIS reporting obligations) and protected from tampering.

- Anomalous access patterns (off-hours OT engineering access, vendor access outside approved windows, repeated failed privileged logins) trigger a SOC alert and OT Security Lead notification.

## **6.10 Exception Handling**

Any deviation from this policy (e.g., a legacy OT system that cannot support MFA, a temporary shared account during an emergency) must be documented in the exception register with: business/technical justification, compensating control, risk owner, and review date. Exceptions affecting Critical-tier OT assets require CISO and OT Security Lead joint sign-off and are reviewed at minimum quarterly.

## **6.11 Enforcement and Non-Compliance**

Violation of this policy — including unauthorized access, credential sharing, or bypassing OT segregation controls — is subject to Helios's disciplinary process and, for vendors, contractual remedy up to termination of the engagement. Confirmed violations affecting OT safety systems are treated as reportable security incidents under the organization's incident response procedure and, where thresholds are met, reported to BSI under NIS2/KRITIS obligations.

# **7. Roles and Responsibilities (RACI)**

| **Activity**                                   | **CISO** | **OT Security Lead** | **IT Ops** | **OT/ICS Engineering** | **GRC/Compliance** | **Vendor Mgmt** |
|------------------------------------------------|----------|----------------------|------------|------------------------|--------------------|-----------------|
| Maintain unified IT/OT asset inventory         | A        | R                    | C          | R                      | C                  | I               |
| Approve new user/system access requests        | A        | C                    | R          | C                      | I                  | I               |
| Quarterly access recertification               | A        | C                    | R          | C                      | R                  | I               |
| Vendor remote-access provisioning & revocation | A        | R                    | C          | C                      | I                  | R               |
| OT change control / patch approval             | C        | A                    | I          | R                      | I                  | C               |
| IAM policy exception approval                  | A        | C                    | I          | I                      | R                  | I               |
| NIS2/KRITIS audit evidence preparation         | A        | C                    | C          | C                      | R                  | I               |
| Incident reporting to BSI/regulator            | R        | C                    | I          | I                      | A                  | I               |

*R = Responsible, A = Accountable, C = Consulted, I = Informed.*

# **8. Compliance Framework Mapping**

The table below maps each control domain in this document to its corresponding regulatory or standards reference, providing direct audit traceability for NIS2/KRITIS regulatory engagement.

| **Control Domain**               | **NIS2 Directive**                              | **BSI/KRITIS**                                            | **IEC 62443**                                                   | **ISO/IEC 27001:2022**     | **NIST CSF 2.0**                       |
|----------------------------------|-------------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------------------|----------------------------|----------------------------------------|
| Asset Management                 | Art. 21(2)(a) risk mgmt measures                | IT-Grundschutz asset baseline; KRITIS asset registry duty | 62443-2-1 Asset Inventory; 62443-3-2 Zone/Conduit ID            | A.5.9, A.8.1               | ID.AM-01, ID.AM-02, ID.AM-04, ID.AM-05 |
| Identity & Access Management     | Art. 21(2)(d)(j) access control                 | BSI IT-Grundschutz ORP.4                                  | 62443-2-1 SR/Requirements on account mgmt; 62443-3-3 SR 1.x/2.x | A.5.15–A.5.18, A.8.2–A.8.5 | PR.AA-01 to PR.AA-05                   |
| Network Segmentation (IT/OT)     | Art. 21(2)(a),(i)                               | KRITIS-specific segmentation expectations                 | 62443-3-2/3-3 Zones & Conduits                                  | A.8.20, A.8.22             | PR.IR-01                               |
| Third-Party / Supply Chain Risk  | Art. 21(2)(d) supply chain security             | BSI supply-chain guidance for KRITIS operators            | 62443-2-4 Service provider requirements                         | A.5.19–A.5.22              | GV.SC-01 to GV.SC-10                   |
| Vulnerability & Patch Management | Art. 21(2)(e)                                   | BSI vulnerability handling guidance                       | 62443-2-3 Patch management for IACS                             | A.8.8                      | ID.RA-01, PR.PS-02                     |
| Incident Detection & Reporting   | Art. 23 reporting obligations (24h/72h/1-month) | BSI incident reporting to national authority              | 62443-2-1 Incident response                                     | A.5.24–A.5.28              | DE.AE, RS.CO, RS.MA                    |
| Governance & Risk Management     | Art. 20, 21(1) management accountability        | KRITIS governance & audit expectations                    | 62443-2-1 Security Management System                            | Clause 5, 6, 9             | GV.OC, GV.RM, GV.OV                    |

# **9. Review and Maintenance**

- This document is reviewed annually by the CISO and OT Security Lead, and on an ad hoc basis following: material IT/OT architecture change, a new smart-grid vendor onboarding, a significant security incident, or a change in NIS2/BSI/KRITIS regulatory requirements.

- The underlying asset inventory (Section 4) is reconciled quarterly against network discovery (IT) and OT engineering change logs (OT), with full physical audit of substation OT assets performed annually.

- Version history and change rationale are maintained in the document control record (cover section) for audit continuity.

# **Appendix A: Definitions and Acronyms**

| **Term** | **Definition**                                                               |
|----------|------------------------------------------------------------------------------|
| AMI      | Advanced Metering Infrastructure — smart meter data collection system        |
| DER      | Distributed Energy Resource (e.g., rooftop solar, battery storage)           |
| DMS      | Distribution Management System                                               |
| FLISR    | Fault Location, Isolation, and Service Restoration                           |
| HMI      | Human-Machine Interface                                                      |
| IACS     | Industrial Automation and Control Systems                                    |
| IED      | Intelligent Electronic Device (protection relay)                             |
| KRITIS   | Kritische Infrastrukturen — German critical infrastructure regulatory regime |
| OT/ICS   | Operational Technology / Industrial Control Systems                          |
| RTU      | Remote Terminal Unit                                                         |
| SCADA    | Supervisory Control and Data Acquisition                                     |
| SoD      | Segregation of Duties                                                        |
