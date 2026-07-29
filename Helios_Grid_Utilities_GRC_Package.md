**HELIOS GRID UTILITIES**

Frankfurt, Germany

**Unified IT/OT Cybersecurity Governance Program**

*Security Awareness Program · Data Loss Prevention Policy · Incident Response Runbook · Third-Party / OT Vendor Risk Assessment*

Prepared by: GRC Analyst, Information Security Compliance

**Classification: Internal --- Confidential**

# 

# 

# 

# 

# 

# 

# 

# 

# 

# 

# **1. Security Awareness Program Outline**

Purpose: Establish a role-based, continuous security awareness program that closes the human-risk gap across Helios Grid Utilities\' corporate IT workforce, OT/engineering personnel, field technicians, and third-party contractors --- supporting NIS2 Article 20 (management accountability and training) and BSI/KRITIS awareness obligations.

## **1.1 Program Objectives**

-   Reduce human-factor incidents (phishing, credential misuse, unsafe remote-access practices) across both IT and OT populations.

-   Build OT-specific risk literacy among engineers who have not traditionally been security stakeholders.

-   Demonstrate auditable, evidence-backed training completion for NIS2/KRITIS and ISO 27001 Annex A 6.3 audits.

-   Establish a measurable security culture baseline and year-over-year improvement trend.

## **1.2 Audience Segmentation & Role-Based Tracks**

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Audience**                        **Population**                                                         **Focus Areas**
  ----------------------------------- ---------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  All Staff (Baseline)                \~3,200 employees, all departments                                     Phishing/social engineering, password & MFA hygiene, data classification, acceptable use, incident reporting (\'see something, say something\').

  Corporate IT & Office Staff         Billing, ERP, customer portal, back-office                             Business email compromise, invoice fraud, customer PII/GDPR handling, cloud app usage, safe remote work.

  OT Engineers & SCADA Operators      Substation control, grid-automation, SCADA/ICS teams                   IEC 62443 security-vs-safety concepts, secure remote access, USB/removable-media discipline, engineering workstation hygiene, recognizing ICS-targeted social engineering, change-control tie-in.

  Field Technicians                   Smart-meter installers, sensor/field-device crews                      Device provisioning security, credential handling on mobile tooling, physical tampering/theft reporting, secure field-laptop use.

  Executives & Board                  Leadership, NIS2-accountable management body                           NIS2 personal-liability obligations, targeted/whaling attacks, incident-reporting decision authority, tabletop participation.

  Third-Party Vendors & Contractors   OT suppliers, smart-meter vendors, IT contractors with remote access   Remote-access rules of engagement, NDA/data-handling obligations, incident-notification duty, on/off-boarding of access.
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## **1.3 Curriculum & Delivery Cadence**

  -------------------------------------------------------------------------------------------------------------------------------------------------
  **Module**                                          **Audience**                        **Frequency**          **Delivery**
  --------------------------------------------------- ----------------------------------- ---------------------- ----------------------------------
  Security Fundamentals & Acceptable Use              All staff                           Annual + on-hire       E-learning module

  Phishing Simulation Program                         All staff                           Monthly simulation     Simulated email platform

  Data Protection & GDPR Handling                     IT, billing, customer service       Annual                 E-learning + quiz

  ICS/OT Security Awareness (IEC 62443-2-1 aligned)   OT engineers, SCADA operators       Annual + on-hire       Instructor-led workshop

  Secure Remote Access for OT Vendors                 OT engineers, vendor coordinators   Semi-annual            Instructor-led + policy sign-off

  Executive Threat Briefing & Tabletop                Executives, board                   Semi-annual            Facilitated tabletop exercise

  Incident Reporting & NIS2 Obligations               All staff, management body          Annual                 E-learning + townhall

  Vendor Security Onboarding Briefing                 New third parties                   Pre-access, one-time   Live briefing + attestation
  -------------------------------------------------------------------------------------------------------------------------------------------------

## **1.4 Reinforcement & Culture Mechanisms**

-   Monthly phishing simulations with escalating difficulty; repeat-clickers routed to targeted coaching.

-   Quarterly \"OT Security Moment\" --- 10-minute toolbox-talk style briefings delivered by OT team leads at shift handover, co-developed with GRC.

-   Internal awareness campaign around KRITIS/NIS2 audit windows to reinforce reporting duties.

-   Recognition program for near-miss/incident reporting to counter OT culture\'s historical reluctance to \"raise flags.\"

-   Annual simulated OT-themed tabletop exercise combining IT and OT responders (see Section 3).

## **1.5 Metrics & Reporting**

-   Training completion rate by role and business unit (target: ≥95% within 30 days of assignment).

-   Phishing simulation click-rate and report-rate trend, segmented IT vs. OT vs. field.

-   Percentage of third-party personnel with current security attestation prior to OT access provisioning.

-   Time-to-report for simulated and real incidents.

-   Quarterly awareness scorecard to the CISO/Security Steering Committee; annual summary to the NIS2-accountable management body.

## **1.6 Governance**

-   Program owner: GRC/Security Awareness Lead, reporting to the CISO.

-   OT content co-developed and reviewed with OT Engineering leadership to preserve safety-first framing and technical accuracy.

-   Content and completion records retained for a minimum of 3 years to support NIS2/KRITIS audit evidence requests.

# **2. Data Loss Prevention (DLP) Policy**

**Document Owner:** CISO / GRC Function **Effective Date:** 01 August 2026 **Review Cycle:** Annual, or upon material change

**2.1 Purpose & Scope**

This policy establishes controls to prevent unauthorized disclosure, exfiltration, or loss of Helios Grid Utilities\' sensitive data, including customer billing and consumption data (personal data under GDPR), grid topology and control-system data, and corporate confidential information. It applies to all employees, contractors, and third parties with access to Helios IT systems, OT/ICS environments, or company data, across all locations and devices, including cloud services and remote access.

**2.2 Data Classification (basis for control application)**

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Tier**           **Examples**                                                                                    **Baseline Controls**
  ------------------ ----------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------
  **Restricted**     Grid topology, SCADA configs, substation control logic, OT network diagrams, credentials/keys   Encryption at rest/in transit, no cloud sync, no removable media, OT network segmentation enforced, access logged and reviewed monthly

  **Confidential**   Customer billing & consumption data (PII), contracts, internal financials                       Encryption at rest/in transit, DLP scanning on email/web/endpoint, access on least-privilege basis, approved cloud apps only

  **Internal**       Internal memos, non-sensitive operational reports                                               Standard access control; no external sharing without approval

  **Public**         Marketing, published tariffs, press releases                                                    No restriction
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**2.3 Core Controls**

-   Endpoint, email, and web DLP tooling inspects outbound traffic for Confidential/Restricted data patterns (IBAN/payment data, national ID formats, grid asset identifiers) and blocks or quarantines policy violations.

-   Restricted-tier data (OT/grid data) is prohibited from personal devices, personal cloud storage, and consumer messaging apps; transfer occurs only via approved, logged, encrypted channels.

-   Removable media on OT/engineering workstations is disabled by default; exceptions require written approval and are scanned on a dedicated transfer station.

-   Customer/billing data exports are logged, size-limited, and subject to approval for bulk extraction (\>1,000 records).

-   Third-party and vendor access to Confidential/Restricted data requires a signed data-handling agreement and is provisioned on least-privilege, time-bound access.

-   Email DLP applies automatic encryption to outbound messages containing Confidential/Restricted markers and flags mismatched recipient domains.

**2.4 Roles & Responsibilities**

-   CISO: policy ownership and exception approval authority.

-   GRC/Security Operations: DLP rule tuning, alert triage, quarterly effectiveness review.

-   OT Engineering Leadership: enforcement of media-control and workstation rules within control-system environments.

-   All personnel: correct classification and handling of data they create or process; mandatory reporting of suspected data loss within 1 hour of discovery.

**2.5 Incident Handling & Regulatory Reporting**

Any suspected loss, exfiltration, or unauthorized disclosure of Confidential or Restricted data is treated as a security incident under the Incident Response Runbook (Section 3). Personal-data breaches meeting GDPR Article 33 thresholds are reported to the competent supervisory authority within 72 hours; incidents affecting OT/grid operations are additionally assessed against NIS2/BSI significant-incident reporting timelines (24-hour early warning, 72-hour incident notification, final report within one month).

**2.6 Exceptions & Enforcement**

Exceptions require documented business justification, risk acceptance by the data/asset owner, and CISO sign-off, and are time-bound with mandatory review. Violations are addressed under the Acceptable Use Policy and HR disciplinary process; willful or grossly negligent data loss may result in termination and, where applicable, referral to authorities.

# **3. Incident Response Runbook**

## **Scenario: Compromised Third-Party Remote Access Leading to Suspected OT/SCADA Intrusion**

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Incident Type**        Third-party remote-access compromise with suspected pivot into OT/SCADA network segment
  ------------------------ --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Severity Tier**        SEV-1 (Critical) --- potential impact to grid operations and public safety

  **Trigger**              SOC alert: anomalous authentication from an OT-vendor VPN account followed by unexpected connection attempts from the vendor remote-access jump host toward substation HMI/engineering workstations, outside scheduled maintenance windows

  **Regulatory Context**   NIS2 Art. 23 / BSI-KRITIS significant-incident reporting; IEC 62443 zone/conduit breach; potential GDPR exposure if customer systems are also affected
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## **3.1 Roles (RACI Summary)**

  ---------------------------------------------------------------------------------------------------------------------------------------------
  **Role**                         **Responsibility**
  -------------------------------- ------------------------------------------------------------------------------------------------------------
  Incident Commander (IR Lead)     Overall coordination, severity declaration, escalation authority

  SOC / IT Security Analyst        IT-side detection, log analysis, containment of corporate network path

  OT/ICS Security Engineer         OT network assessment, safe isolation of affected control assets, coordination with control-room operators

  Control Room / Grid Operations   Operational safety decisions, manual-control fallback, confirms no unsafe state changes

  GRC / Compliance Lead            Regulatory notification timeline (BSI/NIS2), evidence log, audit trail

  Legal & DPO                      GDPR breach assessment, law-enforcement liaison, vendor contract obligations

  Communications/PR                Internal updates, regulator-facing statements, public messaging if outage risk

  Affected Vendor                  Access suspension cooperation, forensic support per contract, root-cause disclosure
  ---------------------------------------------------------------------------------------------------------------------------------------------

## **3.2 Response Phases**

**Phase 1 --- Detection & Triage (0--30 minutes)**

1.  SOC validates the alert: confirm vendor VPN account identity, source geolocation/IP reputation, and destination assets contacted.

2.  IR Lead is paged; SEV-1 declared given OT-directed traffic; incident bridge opened (IT Security, OT Security, Control Room Operations, GRC).

3.  OT/ICS Security Engineer checks whether any control commands, configuration changes, or logic uploads occurred on targeted HMI/engineering workstations.

4.  Initial timeline and indicators (account, source IP, destination assets, timestamps) logged in the incident record.

**Phase 2 --- Containment (30--120 minutes)**

5.  Suspend the compromised third-party VPN/remote-access account and any associated shared credentials immediately.

6.  IT Security isolates the vendor jump host from the corporate network; OT Security confirms the OT/IT segmentation firewall (conduit) is blocking further lateral movement, tightening rules if needed.

7.  Control Room Operations, in coordination with OT Security, evaluates whether affected substation systems should be placed into manual/local control as a precaution --- safety and continuity of supply take priority over forensic preservation of live systems.

8.  Preserve forensic evidence (firewall logs, VPN logs, EDR data, HMI session logs) before any remediation that would overwrite it, consistent with safe-operation constraints.

9.  Identify and inventory all other active remote-access sessions/vendors as a precaution; suspend any with unclear ownership pending validation.

**Phase 3 --- Eradication & Recovery (Hours 2--24+)**

10. Forensic review (internal + vendor, and external IR retainer if warranted) determines root cause --- e.g., compromised vendor credential, unpatched jump host, absence of MFA.

11. Rotate all credentials associated with the affected vendor and any shared/service accounts on the path; enforce MFA on remote-access accounts if not already present.

12. Validate integrity of OT assets that were contacted: confirm no unauthorized configuration or logic changes via checksum/config comparison against known-good baseline before returning systems to remote/automated control.

13. Phased restoration of vendor access only after remediation is verified and re-approved by OT Security and IR Lead, under enhanced monitoring.

**Phase 4 --- Notification & Reporting**

14. GRC/Compliance assesses significance against BSI/KRITIS and NIS2 thresholds; if met, submit the early warning to BSI within 24 hours of awareness and formal incident notification within 72 hours, with a final report within one month.

15. DPO assesses whether any personal data (customer systems) was implicated; if so, GDPR Art. 33 72-hour supervisory-authority notification runs in parallel.

16. Executive leadership and the NIS2-accountable management body are briefed per the internal severity-escalation matrix; customer/public communications activated only if service impact occurs.

**Phase 5 --- Post-Incident Review**

17. Formal after-action review within 10 business days: root cause, timeline, control gaps (e.g., vendor remote-access inventory, MFA coverage, conduit rule effectiveness).

18. Update the IT/OT asset and remote-access inventory, the third-party risk register, and this runbook with lessons learned.

19. Feed findings into the annual OT tabletop exercise and vendor risk re-assessment cycle (Section 4).

## **3.3 Key Decision Point**

**Escalation to manual/local substation control is a Control Room Operations decision, made jointly with OT Security, and is never delayed for forensic convenience. Safety and supply continuity take precedence over evidence preservation at every phase of this runbook.**

# **4. Third-Party / Operational Technology Vendor Risk Assessment**

Applies to all vendors, integrators, and suppliers with remote or on-site access to Helios OT/ICS environments, smart-grid field devices, or Confidential/Restricted data, including smart-meter manufacturers, SCADA/HMI integrators, and grid-sensor suppliers. Assessment is required pre-onboarding and at minimum annually thereafter, or upon material change in access/scope.

## **4.1 Vendor Risk Questionnaire**

***Section A --- Corporate & Governance***

20. Does your organization maintain an information security management system (e.g., ISO/IEC 27001 certified or equivalent)? Provide certificate/evidence.

21. Do you have a named accountable security/compliance contact for the Helios engagement?

22. Have you experienced a security incident or data breach in the past 24 months? Describe scope and remediation.

23. Do you carry cyber liability insurance? Provide coverage level.

***Section B --- Access & Remote Connectivity***

24. Describe all methods used to remotely access Helios systems (VPN, jump host, vendor cloud portal, dial-up/modem, etc.).

25. Is multi-factor authentication enforced on all remote-access accounts used to reach Helios systems?

26. Are remote sessions time-bound, logged, and subject to Helios approval prior to each connection (vs. standing/always-on access)?

27. Do you use shared or generic accounts for access to Helios environments? If yes, describe compensating controls.

28. Can session recording/screen-logging be enabled for privileged remote sessions on request?

***Section C --- OT/ICS-Specific Practices (IEC 62443 alignment)***

29. Does your organization follow IEC 62443 (or equivalent) secure-development and system-integration practices for delivered OT products/services?

30. What is your patch/vulnerability disclosure process for deployed devices, and average time-to-patch for critical vulnerabilities?

31. Do delivered field devices/sensors support secure boot, signed firmware, and encrypted communications?

32. What is the end-of-support/end-of-life roadmap for the proposed OT products, and legacy-support commitments?

33. Do you test firmware/software updates in a representative environment before release to customers?

***Section D --- Data Handling***

34. What categories of Helios data (grid topology, telemetry, customer data) will you access, process, or store?

35. Where is data processed/stored (region), and does this comply with GDPR data-residency/transfer requirements?

36. Is data encrypted at rest and in transit? Specify standards.

37. What is your data deletion/return process at contract termination?

***Section E --- Incident Response & Resilience***

38. Do you have a documented incident response plan, and will you notify Helios of any incident affecting delivered systems within 24 hours of detection?

39. Do you participate in coordinated vulnerability disclosure or threat-intelligence sharing relevant to the energy sector?

40. Do you have business continuity/disaster recovery plans covering services delivered to Helios?

***Section F --- Compliance & Audit***

41. Will you accept periodic Helios (or Helios-appointed third-party) security audits/assessments of the delivered solution?

42. Can you provide evidence of compliance with NIS2 supply-chain security expectations as a supplier to critical infrastructure?

43. Do subcontractors have access to Helios systems/data? If yes, list and describe flow-down security obligations.

## **4.2 Scoring Methodology**

Each of the six sections is scored 0--4 by the assessor based on evidence quality (0 = no evidence/non-compliant, 4 = fully evidenced and mature). Sections are weighted to reflect OT/critical-infrastructure risk exposure, producing a composite score of 0--100.

  -----------------------------------------------------------------------------------------------------------------
  **Section**                         **Weight**       **Rationale**
  ----------------------------------- ---------------- ------------------------------------------------------------
  A. Corporate & Governance           10%              Baseline maturity indicator

  B. Access & Remote Connectivity     25%              Primary OT intrusion pathway per scenario risk profile

  C. OT/ICS-Specific Practices        25%              Direct control-system safety/reliability impact

  D. Data Handling                    15%              GDPR and grid-data confidentiality exposure

  E. Incident Response & Resilience   15%              Determines containment speed for supplier-origin incidents

  F. Compliance & Audit               10%              NIS2 supply-chain assurance requirement
  -----------------------------------------------------------------------------------------------------------------

## **4.3 Risk Rating Bands**

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Composite Score**   **Rating**          **Treatment**
  --------------------- ------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------
  85--100               **Low Risk**        Approve standard access; annual reassessment.

  65--84                **Moderate Risk**   Approve with compensating controls (e.g., enhanced monitoring, restricted access windows); reassess every 6 months.

  40--64                **High Risk**       Conditional approval requiring a documented remediation plan with deadlines, executive risk acceptance, and quarterly reassessment; no standing OT access.

  Below 40              **Unacceptable**    Access denied/suspended until material remediation is demonstrated and re-assessed.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## **4.4 Additional Onboarding Requirements (all ratings)**

-   Signed data-handling and confidentiality agreement referencing this policy and the DLP Policy (Section 2).

-   Entry into the consolidated IT/OT remote-access inventory with named contacts, access scope, and expiry date.

-   Least-privilege, time-bound access provisioning --- no standing/always-on OT connectivity by default.

-   Inclusion in the incident-notification distribution list per the Incident Response Runbook (Section 3).

-   High-risk and OT-critical vendors are subject to on-site or evidence-based audit prior to go-live, and annually thereafter.
