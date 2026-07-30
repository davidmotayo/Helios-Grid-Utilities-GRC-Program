# IT + OT Cybersecurity Risk Register

**Helios Grid Utilities — Frankfurt, Germany | Regional Electricity Distribution Operator**

| | |
|---|---|
| **Document Owner** | GRC Analyst, Helios Grid Utilities |
| **Approved By** | CISO (pending sign-off) |
| **Scope** | Corporate IT + OT/ICS/SCADA |
| **Review Cycle** | Quarterly, or on material change |
| **Frameworks** | NIST CSF 2.0, IEC 62443 |
| **Drivers** | NIS2, KRITIS/BSI, ISO 27001 |
| **Version** | v1.0 — Draft for Audit Prep |
| **Date** | 29 June 2026 |

## 1. Purpose & Scope

This risk register establishes a unified view of cybersecurity risk spanning Helios Grid Utilities' corporate IT environment (email, ERP, billing, customer portal) and its operational technology environment (SCADA, substation control systems, grid-automation sensors, and the smart-meter rollout). It supports the organization's NIS2 and KRITIS/BSI compliance obligations by demonstrating documented risk identification, scoring, ownership, and treatment consistent with NIST CSF 2.0 and IEC 62443 guidance for industrial control environments.

Risks are assessed on an inherent (pre-control) and residual (post-treatment target) basis. Scoring reflects the convergent nature of IT/OT risk at Helios: a compromise originating in IT can pivot into OT, and an OT failure carries physical safety and public-service consequences beyond typical data-confidentiality impact.

## 2. Methodology

Each risk is scored using a 5×5 Likelihood × Impact matrix (1 = low, 5 = high), producing an Inherent Risk Score of 1–25. Impact ratings for OT-related risks weight safety, service continuity, and regulatory exposure alongside financial and reputational loss, reflecting the higher consequence ceiling of control-system events relative to pure IT/data events.

| Score Band | Risk Level / Response |
|---|---|
| **15 – 25** | Critical — immediate executive attention; treat or escalate within days |
| **8 – 14** | High — treatment plan with funded owner and committed timeline |
| **4 – 7** | Moderate — scheduled treatment within the annual planning cycle |
| **1 – 3** | Low — monitor; accept or treat opportunistically |

## 3. IT + OT Risk Register

*Twelve risks spanning corporate IT, OT/ICS, smart-grid/IoT, identity, governance, third-party, and compliance domains. L = Likelihood (1–5), I = Impact (1–5), Score = L × I (Inherent Risk).*

| ID | Domain | Risk Description | Asset(s) | L | I | Score | Owner | Treatment / Controls | Target Residual |
|---|---|---|---|---|---|---|---|---|---|
| **R-01** | OT/ICS | Ransomware or destructive malware reaches OT via a compromised IT/OT bridge (e.g., engineering laptop, jump host), disrupting substation control and causing outages. | SCADA HMI, RTUs | 4 | 5 | **20** | CISO / OT Security Lead | Network segmentation (IEC 62443 zones/conduits); OT-aware monitoring at the IT/OT boundary; offline, tested control-logic backups; tabletop exercises. | Moderate (4–7) |
| **R-02** | OT/ICS | Poorly inventoried vendor remote-access pathways into OT allow unauthorized or excessive access, enabling lateral movement into control systems. | Vendor remote-access links | 5 | 4 | **20** | Third-Party Risk Manager | Complete remote-access inventory; jump-box + MFA + session recording for all vendor access; time-bound, ticket-gated grants; quarterly access review. | Moderate (4–7) |
| **R-03** | OT/ICS | Unsupported, unpatchable legacy OT controllers carry known vulnerabilities that cannot be remediated without compensating controls, given vendor end-of-life and uptime constraints. | Legacy substation controllers | 4 | 5 | **20** | OT Engineering Director | Compensating network controls (firewalls, allow-listing, virtual patching); prioritized lifecycle replacement roadmap; isolate via dedicated VLANs/zones. | High (8–10) — long lead time |
| **R-04** | IT/OT Convergence | No consolidated asset inventory spanning IT and OT means unmanaged devices, including shadow IT and undocumented field devices, evade patching and monitoring. | Enterprise asset inventory | 4 | 4 | **16** | GRC Analyst / IT Asset Mgmt | Unified CMDB with OT-passive discovery tools; reconcile against procurement and vendor records; mandate inventory update on all new deployments. | Low–Moderate (3–6) |
| **R-05** | Smart Grid / IoT | Thousands of multi-vendor, internet-connected smart meters and sensors expand the attack surface with inconsistent firmware security and weak default credentials. | Smart meters, grid sensors | 5 | 3 | **15** | Smart Grid Program Manager | Vendor security baseline in procurement; mandatory credential rotation before deployment; segmented IoT network with anomaly detection; firmware updates. | Moderate (4–6) |
| **R-06** | Identity & Access | Fragmented IAM across old and new IT/OT systems leads to orphaned accounts, excessive privilege, and inconsistent MFA enforcement. | IAM across legacy + modern systems | 4 | 4 | **16** | IAM Lead | Consolidate IAM under a single identity provider where feasible; enforce least privilege and periodic access recertification; mandate MFA for privileged/remote access. | Moderate (4–6) |
| **R-07** | Governance | IT and OT are governed by separate teams with no unified security program, creating gaps in policy, incident response, and accountability across the IT/OT boundary. | IT/OT security program | 4 | 4 | **16** | CISO | Joint IT/OT governance committee; unify policy under NIST CSF with IEC 62443 overlay for OT; single risk register and IR plan spanning both domains. | Low–Moderate (3–5) |
| **R-08** | Third-Party / Supply Chain | Insufficient vendor security due diligence for OT suppliers and integrators introduces supply-chain compromise risk (firmware tampering, insecure components). | OT equipment suppliers, integrators | 3 | 4 | **12** | Procurement / Third-Party Risk Manager | Security requirements in RFPs/contracts; SBOM and firmware-integrity attestation; risk-tiered vendor assessments; right-to-audit clauses for critical suppliers. | Low–Moderate (3–5) |
| **R-09** | Compliance | Inability to demonstrate continuous risk management and timely incident reporting per NIS2 and KRITIS/BSI requirements results in audit findings and penalties. | NIS2 / KRITIS reporting program | 3 | 4 | **12** | GRC Analyst / Compliance Officer | Map controls to NIS2/KRITIS/ISO 27001 requirements; formalize 24/72-hour incident notification procedure; conduct internal pre-audit and remediate gaps. | Low (2–4) |
| **R-10** | IT | Customer billing and consumption data in cloud-connected IT systems is exposed to credential-stuffing, phishing, or web-app attacks, risking large-scale data breach. | Customer portal, billing/ERP | 4 | 3 | **12** | IT Security Manager | WAF and bot-mitigation on the customer portal; mandatory MFA for admin access; DLP on billing/ERP exports; regular penetration testing and patching. | Low–Moderate (3–5) |
| **R-11** | Physical / OT Safety | Inadequate physical security at remote substations allows unauthorized access to control cabinets and network equipment, enabling direct OT tampering. | Substations, field equipment | 2 | 5 | **10** | Physical Security Manager | Tamper-evident enclosures and access logging at substations; CCTV/intrusion alarms tied to the SOC; periodic physical security audits of remote sites. | Low (2–4) |
| **R-12** | OT/ICS | Theft of sensitive grid topology and control-system design data enables targeted attack planning by sophisticated threat actors. | Grid topology & control data | 3 | 5 | **15** | CISO / Data Protection Officer | Classify and encrypt grid topology data at rest/in transit; restrict access on a need-to-know basis; monitor for exfiltration; insider-threat awareness. | Moderate (4–6) |

## 4. SLE / ALE Calculation — Worked Example

To quantify financial exposure for the highest-scoring risk, R-01 (ransomware/destructive malware disrupting OT and causing customer outages), Helios applies a Single Loss Expectancy (SLE) and Annualized Loss Expectancy (ALE) calculation. This translates qualitative risk scoring into a defensible financial figure for budget and treatment-prioritization discussions with the executive team and board.

### 4.1 Inputs and Assumptions

| | |
|---|---|
| **Asset / Scenario** | OT/SCADA outage from a ransomware event disrupting substation control for an average-affected distribution area |
| **Asset Value (AV)** | € 18,000,000 (estimated value of affected grid-segment revenue, restoration cost, and regulatory/penalty exposure for a multi-day outage) |
| **Exposure Factor (EF)** | 25% — a successful intrusion is assumed to disrupt roughly one quarter of asset value via outage duration, restoration labor, regulatory fines, and reputational/customer-compensation costs, based on the peer-utility incident referenced in threat intelligence |
| **Single Loss Expectancy (SLE)** | **SLE = AV × EF = € 18,000,000 × 0.25 = € 4,500,000** |
| **Annualized Rate of Occurrence (ARO)** | 0.20 (estimated 1-in-5-year likelihood, reflecting the rising frequency of nation-state and ransomware activity against European energy operators and partial, but incomplete, OT segmentation) |
| **Annualized Loss Expectancy (ALE)** | **ALE = SLE × ARO = € 4,500,000 × 0.20 = € 900,000 / year** |

### 4.2 Interpretation & Use

An ALE of approximately €900,000 per year represents Helios' expected annual financial exposure from this single OT ransomware scenario before additional treatment. This figure supports a cost-benefit case: if proposed controls (IT/OT segmentation hardening, OT-aware monitoring, and offline backup capability) cost materially less than €900,000 annually to implement and maintain, and meaningfully reduce the Exposure Factor or Annualized Rate of Occurrence, the investment is financially justified independent of the safety and regulatory rationale already established in Section 3 (R-01).

This calculation should be refreshed as incident data, segmentation maturity, and threat intelligence evolve, and repeated for other high-scoring risks (notably R-02 and R-03) to build a portfolio view of annualized cyber-risk exposure for budget planning and board reporting.

## 5. Compliance Alignment Note

This register and its treatments are designed to map directly to NIS2 Directive risk-management and incident-reporting obligations, Germany's KRITIS/BSI critical-infrastructure requirements, IEC 62443 zone-and-conduit principles for the OT environment, and ISO/IEC 27001 control objectives for the IT environment, with NIST CSF 2.0 functions (Govern, Identify, Protect, Detect, Respond, Recover) used as the unifying structure across both domains. A detailed control-mapping matrix is maintained as a companion working paper.
