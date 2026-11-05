# Greenbone Vulnerability Assessment & IT Security Risk Assessment

## Project Overview

This project demonstrates an end-to-end cybersecurity assessment workflow using Greenbone Community Edition, Proxmox VE, and an intentionally vulnerable Metasploitable Linux virtual machine.

The objective was to identify technical vulnerabilities, analyze supporting evidence, evaluate potential business risks, and develop risk treatment recommendations using established cybersecurity governance and risk management concepts.

The project combines technical vulnerability assessment with:

* IT security risk identification and analysis
* Likelihood and impact scoring
* Risk register development
* COSO internal control considerations
* NIST SP 800-53 control mapping
* Risk treatment planning
* Executive-level security reporting

**Assessment Date:** November 3, 2026

**Project Type:** Home Lab / Cybersecurity GRC Portfolio Project

**Important:** This project was conducted in a controlled laboratory environment against an intentionally vulnerable system. Business risk ratings and management recommendations are simulated and do not represent an assessment of a production organization.

---
## Project Deliverables

| Deliverable | Description |
|---|---|
| [Assessment Reports](reports/) | Seven-section IT Security Risk Assessment covering methodology, findings, COSO/NIST control mapping, treatment recommendations, and limitations |
| [Risk Management Workbook](risk-management/IT_Security_Risk_Register_Metasploitable_2026.xlsx) | Four-tab workbook containing the Risk Register, Risk Scoring Methodology, Risk Treatment Plan, and Executive Dashboard |

**Assessment Results:** 66 Greenbone findings identified; 13 Critical findings reviewed in detail and consolidated into 12 distinct risks (9 Critical, 3 High).

**Assessment Scope:** Intentionally vulnerable Metasploitable laboratory system with simulated business risk analysis.

## Laboratory Environment

| Component                | Technology                      |
| ------------------------ | ------------------------------- |
| Virtualization Platform  | Proxmox VE 9.0.3                |
| Vulnerability Scanner    | Greenbone Community Edition     |
| Scanner Operating System | Ubuntu 24.04                    |
| Assessment Target        | Metasploitable Linux            |
| Deployment Method        | Docker Compose                  |
| Risk Management          | Spreadsheet-based Risk Register |
| Control Frameworks       | COSO and NIST SP 800-53         |

The laboratory used a dedicated virtual network for vulnerability assessment traffic.

The Greenbone scanner had separate interfaces for management connectivity and communication with the vulnerable target.

Network safeguards included a laboratory bridge without a physical uplink, disabled IP forwarding, and firewall forwarding restrictions.

These safeguards supported the intended separation of the vulnerable target from the home network. Complete isolation was not established through exhaustive testing of every possible network path.

---

## Assessment Methodology

The assessment followed six phases:

| Phase | Activity                             |
| ----- | ------------------------------------ |
| 1     | Laboratory Preparation               |
| 2     | Vulnerability Scanning               |
| 3     | Finding Review and Evidence Analysis |
| 4     | Business Risk Assessment             |
| 5     | COSO and NIST Control Mapping        |
| 6     | Risk Treatment and Reporting         |

Greenbone Community Edition was used to identify vulnerabilities affecting the Metasploitable target.

The most significant findings were reviewed to understand the affected services, technical severity, detection evidence, and potential consequences.

Technical findings were then translated into documented IT security risks using a simulated production scenario.

---

## Vulnerability Assessment Results

The completed Greenbone scan identified **66 findings**.

| Severity  | Findings |
| --------- | -------: |
| Critical  |       13 |
| High      |        8 |
| Medium    |       39 |
| Low       |        6 |
| **Total** |   **66** |

The 13 Critical findings were selected for detailed analysis.

Two results associated with the same vsftpd backdoor vulnerability were consolidated into one risk.

This resulted in **12 distinct risks** documented in the IT Security Risk Register.

The remaining High, Medium, and Low findings were included in the overall scan summary but were not individually assessed in the risk register.

---

## Key Security Findings

### 1. Unauthorized Remote Command Execution

The assessment identified vulnerabilities and backdoor functionality associated with remote command execution.

Examples included:

* Ingreslock backdoor
* DistCC remote command execution
* Distributed Ruby remote execution exposure
* vsftpd backdoor

Greenbone demonstrated root-level command execution through the Ingreslock backdoor and command execution under a daemon account through DistCC.

Not every remote execution finding was independently demonstrated to permit arbitrary command execution.

### 2. Weak Authentication

The assessment identified authentication weaknesses involving:

* Passwordless rlogin access
* Empty MySQL administrator password
* Default PostgreSQL credentials
* Weak VNC authentication

These findings illustrate the risks associated with insecure authentication and privileged access configurations.

### 3. Unsupported and Vulnerable Software

The target contained outdated software, including Ubuntu 8.04 and a vulnerable TWiki application version.

These findings demonstrate the importance of software lifecycle management, patching, and secure configuration practices.

### 4. Insecure Network Services

The assessment identified insecure or unnecessarily exposed services.

Examples included rexec and the Apache Tomcat AJP connector.

The Tomcat Ghostcat finding included evidence of unauthorized retrieval of an application configuration file.

Remote code execution through Ghostcat was not demonstrated.

---

## Business Risk Assessment

To demonstrate enterprise risk management practices, the vulnerabilities were evaluated using a hypothetical production scenario.

The target was assumed to support business applications and be accessible from an internal corporate network.

A five-point likelihood and impact methodology was applied.

**Inherent Risk Score = Likelihood × Impact**

| Risk Score | Classification |
| ---------- | -------------- |
| 1–4        | Low            |
| 5–9        | Medium         |
| 10–16      | High           |
| 17–25      | Critical       |

### Risk Assessment Results

| Risk Rating | Number of Risks |
| ----------- | --------------: |
| Critical    |               9 |
| High        |               3 |
| Medium      |               0 |
| Low         |               0 |
| **Total**   |          **12** |

Nine risks were assigned Priority 1 (P1), and three were assigned Priority 2 (P2).

These ratings are illustrative business-risk assessments rather than measurements of actual organizational risk.

---

## Internal Control Mapping

The documented risks were mapped to relevant concepts from the COSO Internal Control Framework and NIST SP 800-53.

### COSO

The assessment primarily focused on the **Control Activities** component.

Relevant areas included:

* Authentication and privileged access
* Secure system configuration
* Vulnerability and patch management
* Network access restrictions
* Software lifecycle management

### NIST SP 800-53

Relevant control considerations included:

| Control | Description                                |
| ------- | ------------------------------------------ |
| AC-3    | Access Enforcement                         |
| AC-6    | Least Privilege                            |
| AC-17   | Remote Access                              |
| IA-5    | Authenticator Management                   |
| CM-6    | Configuration Settings                     |
| CM-7    | Least Functionality                        |
| CM-8    | System Component Inventory                 |
| SI-2    | Flaw Remediation                           |
| SC-7    | Boundary Protection                        |
| SC-8    | Transmission Confidentiality and Integrity |

The mappings identify potential safeguards relevant to the vulnerabilities.

No formal organizational control design or operating effectiveness testing was performed.

---

## Risk Treatment Recommendations

The assessment developed proposed treatment actions for all 12 registered risks.

Recommended activities included:

1. Remove backdoors and restrict unauthorized remote execution.
2. Eliminate empty, default, and weak passwords.
3. Disable insecure legacy administration services.
4. Upgrade or retire unsupported software.
5. Restrict unnecessary network exposure.
6. Validate corrective actions through targeted testing and rescanning.

All 12 risks were assigned a proposed mitigation strategy.

**Assessment status:**

| Metric                         | Result |
| ------------------------------ | ------ |
| Registered Risks               | 12     |
| Open Risks                     | 12     |
| Proposed Mitigation Strategies | 12     |
| Verified Remediations          | 0      |
| Residual Risk Assessments      | 0      |

No remediation activities were performed during the assessment.

---


### IT Security Risk Assessment Report

A seven-section report documenting:

1. Executive Summary
2. Assessment Objectives and Scope
3. Assessment Methodology
4. Key Findings and Risk Analysis
5. COSO and NIST Control Assessment
6. Risk Treatment Recommendations
7. Assessment Limitations and Conclusion

### Risk Management Workbook

A four-tab workbook containing:

* Risk Register
* Risk Scoring Methodology
* Risk Treatment Plan
* Executive Dashboard

### Technical Evidence

The assessment was supported by an exported Greenbone vulnerability scan report and technical detection evidence.

Selected, sanitized evidence may be included in this repository to demonstrate the basis for the documented findings.

---

## Skills Demonstrated

**Technical Security**

* Virtualized cybersecurity laboratory configuration
* Greenbone vulnerability scanning
* Vulnerability evidence interpretation
* Network service and configuration analysis
* Technical severity assessment

**Governance, Risk, and Compliance**

* IT security risk identification
* Likelihood and impact analysis
* Inherent risk scoring
* Risk register development
* COSO internal control concepts
* NIST SP 800-53 control mapping
* Risk treatment planning
* Management reporting

**Professional Communication**

* Translating technical vulnerabilities into business risks
* Distinguishing demonstrated evidence from detection-based findings
* Documenting assessment limitations
* Developing management-oriented recommendations

---

## Assessment Limitations

This project was conducted against a single intentionally vulnerable laboratory system.

The assessment did not include:

* Production infrastructure testing
* Comprehensive penetration testing
* Detailed analysis of all 66 scanner findings
* Formal organizational control effectiveness testing
* Remediation implementation or validation
* Residual risk assessment
* Management risk acceptance

The business risk ratings, ownership assignments, and treatment priorities were developed for educational purposes.

This project does not provide assurance regarding the cybersecurity posture of any production organization.

---

## Key Takeaways

This project demonstrated that vulnerability management involves more than identifying technical weaknesses.

Effective cybersecurity risk management also requires understanding the available evidence, evaluating potential business consequences, identifying relevant security controls, prioritizing treatment, and communicating results clearly.

The project illustrates how technical vulnerability assessment can support IT audit, cybersecurity governance, and enterprise risk management activities.

---

## Disclaimer

All vulnerability testing was performed against an intentionally vulnerable system within a personally controlled laboratory environment.

No third-party or production systems were assessed.

The documented findings and simulated risk ratings are provided for educational and professional portfolio purposes.
