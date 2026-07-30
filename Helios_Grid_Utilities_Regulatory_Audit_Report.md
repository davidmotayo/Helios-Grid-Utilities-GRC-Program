**REGULATORY COMPLIANCE AUDIT REPORT**

IT/OT Cybersecurity Governance, Risk & Compliance Assessment

**HELIOS GRID UTILITIES**

*Frankfurt, Germany · Regional Electricity Distribution Operator*

| | |
|---|---|
| **Report Type** | Regulatory Readiness / Compliance Audit |
| **Regulatory Frameworks** | EU NIS2 Directive · German BSI/KRITIS · IEC 62443 · ISO/IEC 27001:2022 · NIST CSF 2.0 |
| **Scope** | Corporate IT and Operational Technology (OT/ICS/SCADA) environments, including smart-grid field devices and third-party/vendor access |
| **Audit Date** | 13 July 2026 |
| **Report Classification** | Confidential — Internal / Regulator Use Only |
| **Prepared By** | GRC Analyst |
| **Distribution** | Chief Information Security Officer, Chief Risk Officer, OT Engineering Director, Board Risk Committee |

# Executive Summary

Helios Grid Utilities ("Helios") is a regional electricity distribution operator serving approximately 1.4 million households and businesses across Frankfurt and surrounding districts. As a designated critical-infrastructure operator under Germany's KRITIS regime and an entity in scope for the EU NIS2 Directive, Helios is subject to heightened statutory obligations for cybersecurity governance, risk management, and incident reporting, with formal regulatory audits and potential enforcement penalties for non-compliance.

This audit was conducted to assess Helios' readiness against NIS2, BSI/KRITIS, IEC 62443, ISO/IEC 27001:2022, and NIST CSF requirements, with particular focus on the governance boundary between corporate Information Technology (IT) and Operational Technology (OT/ICS/SCADA) environments. The assessment covered governance and organizational structure, asset inventory and risk management practices, identity and access management, third-party/vendor risk management, vulnerability and patch management, and incident detection and reporting capability.

The audit identified four significant findings, summarized below, that collectively indicate Helios does not yet possess a demonstrable, unified cybersecurity governance program spanning both IT and OT as required under NIS2 Article 21 and the German IT-Sicherheitsgesetz (IT-SiG 2.0) / BSI KRITIS-Verordnung. The most significant gaps relate to the absence of a consolidated IT/OT asset inventory, fragmented identity and access management with poorly governed third-party remote access into OT, an OT patch and vulnerability management model that is reactive rather than risk-based, and incident response/reporting arrangements that are unlikely to satisfy NIS2's mandatory 24-hour early-warning and 72-hour reporting timelines.

Left unremediated, these gaps expose Helios to elevated risk of a disruptive OT security incident affecting grid reliability and public safety — consistent with recent attacks against peer European utilities — as well as to regulatory enforcement action, including administrative fines of up to €10 million or 2% of global annual turnover under NIS2, and potential personal liability exposure for management under Article 20. Each finding below is presented using the Five C's methodology (Condition, Criteria, Cause, Consequence, Recommendation) to support root-cause remediation planning and audit-committee reporting.

| **#** | **Finding** | **Domain** | **Risk Rating** |
|---|---|---|---|
| 1 | No consolidated IT/OT asset inventory or risk register | Asset & Risk Mgmt | **Critical** |
| 2 | Fragmented IAM and poorly inventoried third-party/vendor remote access into OT | Access & Vendor Risk | **Critical** |
| 3 | Reactive, non-risk-based OT patch and vulnerability management | Vulnerability Mgmt | **High** |
| 4 | Incident detection and reporting capability insufficient for NIS2 timelines | Incident Response | **High** |

# Audit Scope, Objectives & Methodology

## Objectives

- Assess the design and operating effectiveness of Helios' cybersecurity governance program against NIS2, BSI/KRITIS, IEC 62443, ISO/IEC 27001:2022, and NIST CSF 2.0.
- Evaluate the maturity of asset inventory and risk management practices spanning corporate IT and OT/ICS/SCADA environments.
- Assess identity and access management, with emphasis on third-party vendor and OT-supplier remote access.
- Evaluate vulnerability and patch management practices applied to legacy and unsupported OT assets.
- Assess incident detection, escalation, and regulatory reporting capability against NIS2's mandatory timelines.

## Methodology

The audit was performed using a combination of document review (policies, standards, network diagrams, vendor contracts), interviews with IT security, OT engineering, and procurement personnel, walkthroughs of representative substations and the smart-meter data platform, and control testing against IEC 62443 zone/conduit requirements and ISO/IEC 27001:2022 Annex A controls. Findings were rated using a four-tier scale (Critical / High / Medium / Low) based on likelihood and potential impact to safety, reliability, confidentiality, and regulatory compliance.

## Regulatory Basis

- EU NIS2 Directive (2022/2555) — Articles 20 (governance/management liability) and 21 (risk-management measures, incident reporting).
- German IT-Sicherheitsgesetz 2.0 and BSI KRITIS-Verordnung — critical-infrastructure obligations administered by the Bundesamt für Sicherheit in der Informationstechnik (BSI).
- IEC 62443 series — security for industrial automation and control systems (zones, conduits, security levels).
- ISO/IEC 27001:2022 — information security management system and Annex A controls.
- NIST Cybersecurity Framework 2.0 — used as the organizing framework for governance (Govern, Identify, Protect, Detect, Respond, Recover).

# Detailed Findings

Each finding below is documented using the Five C's audit methodology: Condition (what was observed), Criteria (the standard against which it was assessed), Cause (the underlying root cause), Consequence (the resulting risk or impact), and Recommendation (corrective action proposed).

## Finding 1: No Consolidated IT/OT Asset Inventory or Unified Risk Register

**Domain:** Asset & Risk Management (NIST CSF: Identify) — **Risk Rating: CRITICAL**

| | |
|---|---|
| **Condition** | Helios maintains separate, incomplete asset records for corporate IT (via its ITSM/CMDB tool) and OT/ICS (via informal spreadsheets maintained locally by substation engineering teams). No single, authoritative inventory exists that spans both domains. Newly deployed smart-meter and grid-automation field devices from multiple vendors are not systematically registered at time of deployment, and several legacy SCADA components could not be definitively attributed to an owner or firmware version during walkthroughs. |
| **Criteria** | NIS2 Article 21(2)(a) requires risk-analysis and information-system security policies underpinned by accurate asset visibility. IEC 62443-2-1 requires a documented asset inventory as a foundational element of the Cyber Security Management System (CSMS). ISO/IEC 27001:2022 Annex A.5.9 requires an inventory of information and associated assets with a designated owner. NIST CSF 2.0 ID.AM-1/ID.AM-2 require physical and software assets to be inventoried. |
| **Cause** | IT and OT are governed by separate teams with no unified security program or shared asset-management platform. The smart-grid modernization program was rolled out without a corresponding requirement for devices to be registered in a central inventory prior to network connection, and historical "air-gap" assumptions about OT reduced the perceived urgency of formal inventory discipline. |
| **Consequence** | Without a unified inventory, Helios cannot reliably scope its attack surface, prioritize patching, or demonstrate risk coverage to regulators. Unregistered or unknown devices represent a materially elevated likelihood of undetected compromise, and the gap directly undermines Helios' ability to complete the NIS2-mandated risk assessment and to respond credibly to a BSI KRITIS audit request for asset documentation, exposing the organization to both operational risk and regulatory enforcement. |
| **Recommendation** | Establish a single, cross-domain asset inventory and Configuration Management Database (CMDB) covering IT, OT, and IoT/field devices, with mandatory registration prior to network connection. Assign an executive-level asset-management owner spanning both domains, adopt an IEC 62443-aligned zone/conduit model to classify assets by criticality, and integrate the inventory with the enterprise risk register so that every asset maps to a documented risk owner and treatment plan. Target completion: initial inventory baseline within 90 days; full CMDB integration within two quarters. |

## Finding 2: Fragmented Identity & Access Management with Poorly Inventoried Third-Party OT Remote Access

**Domain:** Access & Vendor Risk (NIST CSF: Protect / Govern) — **Risk Rating: CRITICAL**

| | |
|---|---|
| **Condition** | Identity and access management is fragmented across legacy OT systems (local accounts, shared credentials at several substations) and modern IT/cloud systems (centralized SSO). Multiple OT equipment vendors and integrators maintain remote-access pathways into the control environment — via VPNs, vendor-supplied remote-support tools, and dial-up modems on some legacy RTUs — that are not centrally inventoried, do not universally enforce multi-factor authentication, and in several cases were found to be active despite the associated support contracts having lapsed. |
| **Criteria** | NIS2 Article 21(2)(d)/(j) requires supply-chain security and access-control measures, including secure remote access. IEC 62443-3-3 (SR 1.13 / SR 2.1) requires authentication and authorization controls for all remote access to the control system, including third parties. ISO/IEC 27001:2022 Annex A.5.19–A.5.23 (supplier relationships) and A.8.3/A.8.5 (access restriction, secure authentication) apply directly. NIST CSF 2.0 PR.AA and GV.SC (cybersecurity supply chain risk management) are also relevant. |
| **Cause** | Historical reliance on OT "air-gap" isolation meant remote-access governance was never formalized as OT systems became increasingly networked for remote monitoring. Procurement and OT engineering functions independently onboard vendor remote-access tools without a centralized approval, logging, or offboarding process, and there is no single owner accountable for the third-party access lifecycle across IT and OT. |
| **Consequence** | Unmonitored and lapsed vendor remote-access pathways constitute a high-likelihood initial-access vector consistent with the attack pattern observed at a neighboring peer utility, with potential consequences extending to physical grid disruption and public-safety impact, not merely data loss. This finding also represents a direct compliance gap under NIS2's supply-chain risk-management provisions and would likely be flagged in a formal BSI audit as evidence of inadequate governance over third-party access to critical infrastructure. |
| **Recommendation** | Implement a centralized Privileged Access Management (PAM) solution covering both IT and OT remote access, with mandatory MFA, session recording, and time-bound (just-in-time) access grants for all vendor connections. Conduct an immediate inventory and re-certification of all existing vendor remote-access pathways, disabling any associated with lapsed contracts within 30 days. Establish a formal third-party access lifecycle process (onboarding, periodic access review, mandatory offboarding) owned jointly by IT Security and OT Engineering, and incorporate remote-access security requirements into all OT vendor contracts going forward. |

## Finding 3: Reactive, Non-Risk-Based Patch and Vulnerability Management for OT Systems

**Domain:** Vulnerability Management (NIST CSF: Protect) — **Risk Rating: HIGH**

| | |
|---|---|
| **Condition** | OT engineering teams prioritize uptime and safety over patching, and a significant proportion of SCADA and substation control components are running unsupported or end-of-life firmware and operating systems. There is no documented, risk-based patch-management process for OT; patching decisions are made ad hoc by local engineers, and known vulnerabilities in OT components identified through vendor advisories are not systematically tracked, risk-assessed, or remediated with compensating controls. |
| **Criteria** | IEC 62443-2-3 requires a formal patch-management process for the IACS environment, including risk assessment prior to patch deployment and documented compensating controls where patching is not feasible. NIS2 Article 21(2)(b) requires incident-handling and vulnerability-management measures proportionate to risk. ISO/IEC 27001:2022 Annex A.8.8 requires management of technical vulnerabilities. NIST CSF 2.0 ID.RA (Risk Assessment) and PR.PS (Platform Security) require vulnerabilities to be identified and remediated in a timely, risk-informed manner. |
| **Cause** | The absence of a unified asset inventory (Finding 1) means OT vulnerability exposure cannot be systematically assessed. In addition, OT's operational culture — reasonably prioritizing continuous, safe electricity delivery — has not been paired with a formal risk-acceptance and compensating-control framework, so "cannot patch" defaults to "no action" rather than triggering alternative mitigations such as network segmentation or enhanced monitoring. |
| **Consequence** | Unpatched, unsupported OT components with no compensating controls represent a persistent and exploitable weakness, materially increasing the likelihood of a successful OT-disrupting attack similar to that experienced by the neighboring peer utility, with potential consequences for grid reliability and public safety. The absence of a documented, risk-based process would also likely be assessed as a control deficiency in a BSI/KRITIS technical audit, given the explicit IEC 62443-2-3 expectation of a formal patch-management program. |
| **Recommendation** | Establish a formal, risk-based OT patch- and vulnerability-management program aligned to IEC 62443-2-3, including a documented process for vulnerability triage, patch testing in a non-production environment, and — where patching is not operationally feasible — mandatory compensating controls (network segmentation, enhanced monitoring, access restriction) with formal, time-bound risk acceptance signed off by both OT Engineering and IT Security leadership. Prioritize remediation of unsupported systems identified as highest-criticality in the consolidated asset inventory, and integrate OT vulnerability data into the enterprise risk register. |

## Finding 4: Incident Detection & Regulatory Reporting Capability Insufficient for NIS2 Timelines

**Domain:** Incident Response (NIST CSF: Detect / Respond) — **Risk Rating: HIGH**

| | |
|---|---|
| **Condition** | Helios' security monitoring capability (SOC/SIEM) covers corporate IT comprehensively but has limited to no visibility into the OT/ICS environment; several substations lack any network monitoring or intrusion-detection capability. The current incident-response plan does not include OT-specific escalation procedures, has not been tested via a joint IT/OT tabletop exercise, and does not reference the specific notification timelines and content requirements mandated under NIS2 (24-hour early warning, 72-hour incident notification, and final report within one month). |
| **Criteria** | NIS2 Article 23 mandates a 24-hour early-warning notification to the competent authority/CSIRT following awareness of a significant incident, a detailed 72-hour incident notification, and a final report within one month. IEC 62443-2-1 requires incident response planning specific to the industrial automation and control system environment. ISO/IEC 27001:2022 Annex A.5.24–A.5.26 require incident management planning, assessment, and response. NIST CSF 2.0 DE (Detect) and RS (Respond) functions require timely detection and a tested response capability. |
| **Cause** | Security monitoring investment has historically been concentrated in corporate IT, reflecting the organizational split between IT and OT security teams and the historical assumption that OT's physical isolation reduced monitoring urgency. The incident-response plan has not been updated to reflect NIS2's specific (and comparatively aggressive) regulatory notification timelines, which came into force more recently than the plan's last revision. |
| **Consequence** | Limited OT monitoring visibility increases the likely dwell time of an attacker within the control environment before detection, extending the window in which a safety- or reliability-impacting event could occur. Separately, and irrespective of detection capability, the absence of NIS2-aligned reporting procedures creates a direct compliance risk: Helios may be unable to meet the mandatory 24-hour/72-hour notification windows even where an incident is detected, exposing the organization to regulatory penalties of up to €10 million or 2% of global annual turnover, and potential personal liability for management under Article 20. |
| **Recommendation** | Extend security monitoring (SIEM/OT-aware intrusion detection) to cover priority substations and control-network segments, prioritized using the consolidated asset inventory's criticality ratings. Update the incident-response plan to include OT-specific playbooks and to explicitly incorporate NIS2's 24-hour/72-hour/one-month notification timelines and content requirements, with a pre-drafted notification template and a clearly assigned regulatory-liaison role. Conduct a joint IT/OT tabletop exercise simulating an OT-disrupting incident within the next quarter, and repeat at least annually thereafter to maintain demonstrable readiness for BSI/KRITIS audit. |

# Overall Conclusion & Next Steps

Helios Grid Utilities has made meaningful investments in modernizing its grid infrastructure, but its cybersecurity governance has not kept pace with the resulting expansion of its attack surface or with the regulatory obligations now in force under NIS2 and BSI/KRITIS. The four findings in this report are interrelated: the absence of a unified asset inventory (Finding 1) constrains Helios' ability to manage access (Finding 2), prioritize patching (Finding 3), and scope monitoring coverage (Finding 4). Remediation should therefore begin with the asset inventory as the foundational control, with the remaining findings addressed in parallel where feasible.

It is recommended that Helios establish a single, board-sponsored IT/OT Cybersecurity Governance Committee, chaired jointly by the CISO and the OT Engineering Director, to own the consolidated risk register and to track remediation of these findings against the target dates specified above. Given the compressed regulatory timelines under NIS2 and the demonstrated real-world threat to peer European utilities, it is further recommended that Findings 1 and 2 be treated as immediate priorities, with formal remediation plans presented to the Board Risk Committee within 30 days of this report.
