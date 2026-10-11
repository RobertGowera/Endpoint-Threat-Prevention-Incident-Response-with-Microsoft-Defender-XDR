# Endpoint Threat Prevention & Incident Response with Microsoft Defender XDR

## 1. Project Overview

This project documents hands-on security operations performed in a Microsoft Defender Applied Skills lab environment. The objective was to configure endpoint security controls, investigate a security incident and perform incident response actions using Microsoft Defender XDR.

The project covers the endpoint security lifecycle, from onboarding a device and applying preventive security controls to investigating suspicious activity, collecting investigation evidence and isolating a device as a containment measure.

**Project type:** Cybersecurity / Security Operations Centre (SOC) Lab

**Environment:** Microsoft Defender Applied Skills lab environment

**Primary technologies:**
- Microsoft Defender XDR
- Microsoft Defender for Endpoint
- Endpoint security policies
- Attack Surface Reduction (ASR)
- Live Response
- Incident investigation and response

## 2. Project Objectives

The objectives of this project were to:

- Onboard an endpoint into Microsoft Defender XDR to enable endpoint security monitoring.
- Configure an Endpoint Security Policy to block JavaScript or VBScript from launching downloaded executable content.
- Investigate and manage a security incident using Microsoft Defender XDR.
- Initiate a Live Response session to investigate an endpoint.
- Collect an investigation package for further analysis.
- Isolate a device as an incident containment measure.

## 3. Implementation and Investigation

### Phase 1: Endpoint Onboarding

**Objective:** Establish endpoint visibility within the Microsoft Defender security environment.

**Activities performed:**
- Onboarded an endpoint to Microsoft Defender XDR.
- Worked with the endpoint onboarding process in the lab environment.

**Security relevance:**

Endpoint onboarding enables security teams to collect endpoint telemetry and investigate device activity through the Defender security platform.

**Evidence:** `screenshots/endpoint-onboarding.png`

### Phase 2: Attack Surface Reduction Policy

**Objective:** Apply a preventive security control to reduce the risk of malicious scripts launching downloaded executable content.

**Activities performed:**
- Created an Endpoint Security Policy.
- Configured the relevant Attack Surface Reduction (ASR) rule to block JavaScript or VBScript from launching downloaded executable content.

**Security relevance:**

Attack Surface Reduction rules help prevent common attack techniques by restricting potentially risky application behaviours. This control is intended to reduce the opportunity for malicious scripts to launch downloaded executable files.

**Evidence:** `screenshots/asr-policy.png`

### Phase 3: Microsoft Defender XDR Incident Investigation

**Objective:** Investigate and manage a security incident using the Defender XDR portal.

**Activities performed:**
- Accessed and managed a Defender XDR incident.
- Worked through the incident management workflow provided by the lab.

**Security relevance:**

Incident investigation allows analysts to review available alerts and supporting evidence, understand potentially malicious activity, assess the scope of an incident, and determine appropriate response actions.

**Evidence:** `screenshots/incident-investigation.png`

### Phase 4: Live Response and Device Containment

**Objective:** Perform endpoint response actions and collect evidence to support further investigation.

**Activities performed:**
- Initiated a Live Response session.
- Collected an investigation package.
- Isolated a device through the Defender security environment.

**Security relevance:**

Live Response provides remote investigation capabilities for supported endpoints. An investigation package can provide diagnostic and forensic artefacts for further examination, while device isolation helps contain a potential threat by restricting network communication, subject to the platform's isolation behaviour and permitted connections.

**Evidence:**
- `screenshots/live-response.png`
- `screenshots/investigation-package.png`
- `screenshots/device-isolation.png`

## 4. Security Operations Workflow

The activities in this project demonstrate the following security operations workflow:

1. **Establish visibility:** Onboard an endpoint into the security monitoring environment.
2. **Reduce attack surface:** Configure a preventive endpoint security policy.
3. **Investigate:** Review and manage a security incident in Defender XDR.
4. **Collect evidence:** Initiate Live Response and collect an investigation package.
5. **Contain:** Isolate the affected device as part of the incident response process.

## 5. Skills Demonstrated

- Endpoint security configuration and onboarding
- Attack Surface Reduction policy configuration
- Microsoft Defender XDR incident management
- Endpoint investigation and Live Response
- Investigation evidence collection
- Device isolation and incident containment
- Security documentation and technical reporting

## 6. Key Learning Outcomes

This lab provided practical exposure to endpoint security controls and incident response capabilities within the Microsoft Defender ecosystem.

It reinforced the relationship between preventive security controls, endpoint visibility, incident investigation, evidence collection, and containment. It also provided an opportunity to document security operations activities in a format suitable for my technical portfolio.

## 7. Lab Scope and Limitations

- All activities documented in this project were performed as part of a Microsoft Defender Applied Skills lab.
- The project does not represent production security operations experience.
- Findings and conclusions will be limited to the evidence available from the lab.

## 8. Acknowledgement

This project is based on practical exercises completed through Microsoft Defender Applied Skills. Microsoft documentation and other relevant technical references may be added as supporting sources during the documentation process.

---

**Author:** Robert Gowera

**Certification:** Microsoft Certified: Security Operations Analyst Associate (SC-200)


