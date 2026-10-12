# 04 - Incident Response and Endpoint Containment

## 1. Overview

This phase focused on performing incident response actions in Microsoft Defender XDR after investigating suspicious endpoint activity.

The practical work involved enabling and initiating Live Response, examining the endpoint's current network connections, collecting an investigation package and isolating the affected device.

These activities demonstrate how a security analyst can move from identifying and investigating suspicious behaviour to collecting additional evidence and taking containment measures.

## 2. Objectives

The objectives of this phase were to:

- Enable and initiate Live Response on the affected endpoint.
- Establish a remote investigation session through Microsoft Defender XDR.
- Inspect the endpoint's current network connections.
- Collect an investigation package for further analysis.
- Isolate the affected device to help contain potential malicious activity.
- Understand the difference between investigation, evidence collection and containment.
- Verify the outcome of response actions using the available platform evidence.

## 3. Tools and Environment

- **Microsoft Defender XDR:** Used to access endpoint response capabilities and manage device actions.
- **Live Response:** Used to establish a remote command-line investigation session on the endpoint.
- **Investigation package collection:** Used to gather diagnostic and investigation artefacts from the device.
- **Device isolation:** Used to restrict the affected endpoint's network communications in support of containment.

The activities were conducted in a controlled learning environment as part of the Microsoft Defender Applied Skills exercise.

## 4. Enable Live Response

### Objective

Enable the Live Response Settings required to investigate the affected endpoint remotely through Microsoft Defender XDR.

### Procedure

1. Accessed Defender XDR endpoint tenant settings.
2. Enabled Live Response for the environment.
3. Confirmed the configuration needed to initiate a Live Response session.

### Evidence

![Enable Live Response](/screenshots/live-response/Enable%20Live%20Response.png)

### Security Significance

Live Response provides security analysts with remote investigation capabilities that can help them examine a device without relying solely on information already available in an incident alert.

Access should be restricted to authorised personnel and managed according to organisational permissions and security procedures.

Enabling the capability is a prerequisite for using it.

## 5. Initiate Live Response

### Objective

Start a Live Response session with the affected endpoint to perform further investigation.

### Procedure

1. Selected the affected device in Microsoft Defender XDR.
2. Initiated a Live Response session.
3. Used the available session interface to access the endpoint's investigation capabilities.

### Evidence

![Initiate Live Response](/screenshots/live-response/Initiate%20Live%20Response.png)

### Security Significance

Live Response can provide analysts with additional visibility into endpoint state and support targeted investigation activities.

A remote session can be useful when an analyst needs to examine evidence that is not immediately apparent from an alert or device timeline.

## 6. Investigate Current Network Connections

### Objective

Inspect the endpoint's current network connections to gather additional context about its activity.

### Procedure

1. Established the Live Response session.
2. Accessed the available network connection information.
3. Reviewed the connection details returned by the endpoint.
4. Used the available information as an additional source of investigation evidence.

### Evidence

![Live Response Network Connections](/screenshots/live-response/Live%20Response%20Network%20Connections.png)

### Security Significance

Network connection information can help an analyst identify active or recently observed communications, depending on the command used and the information available at the time of collection.

When investigating a potentially suspicious process, useful context can include:

- The local and remote IP addresses.
- The destination port and protocol.
- The process associated with the connection, where that information is available.
- The connection's timing relative to the incident.
- Whether the destination is expected for the endpoint and its installed applications.

## 7. Collect an Investigation Package

### Objective

Collect an investigation package from the affected endpoint to support further analysis.

### Procedure

1. Selected the relevant endpoint in Microsoft Defender XDR.
2. Initiated the investigation package collection action.
3. Reviewed the available status or output associated with the collection.
4. Captured evidence of the collection workflow and the resulting package information.

### Evidence

![Collect Investigation Package](/screenshots/live-response/Collect%20Investigation%20Package.png)

![Investigation Package](/screenshots/live-response/Investigation%20Package.png)

### Security Significance

An investigation package can provide additional diagnostic and forensic artefacts that support an analyst's assessment of endpoint activity.

It can complement alerts, process trees, device timelines and network connection information. This allows the analyst to examine evidence beyond the initial detection and helps support a more complete incident investigation.

The package should be handled securely because endpoint investigation artefacts may contain sensitive information. Access, storage, transfer and retention should follow the applicable organisational procedures.

The screenshots provide evidence of the investigation package workflow. Where the platform shows a successful collection status, that status should be used to support the claim that collection completed. Initiating the action alone is not proof that the package was successfully collected.

## 8. Isolate the Affected Device

### Objective

Apply device isolation as a containment measure during the incident response exercise.

### Procedure

1. Selected the affected endpoint in Microsoft Defender XDR.
2. Initiated the device isolation action.
3. Reviewed the isolation status in the platform.
4. Captured evidence of the isolation action and resulting device state.

### Evidence

![Device Isolation](/screenshots/incident-response/Device%20Isolation.png)

![Device Isolated](/screenshots/incident-response/Device%20Isolated.png)

### Security Significance

Device isolation is a containment measure used to limit an endpoint's ability to communicate with other devices or services while an investigation is underway.

It can reduce the risk of a potentially compromised device communicating with malicious infrastructure or affecting other systems. The precise communication permitted during isolation depends on the platform's isolation behaviour and supported exceptions.

Isolation should be proportionate to the suspected threat and the operational importance of the device.

## 9. Response Workflow and Evidence Correlation

This phase demonstrates how endpoint investigation and response actions can work together.

The workflow was:

1. **Investigate:** Use Defender XDR incident information, the device timeline and process tree to understand the observed activity.
2. **Gather additional context:** Use Live Response to examine available endpoint information, including network connections.
3. **Collect evidence:** Request an investigation package to support further analysis.
4. **Contain:** Isolate the affected endpoint to limit potential risk.
5. **Verify:** Review the status and results of each action rather than assuming that an initiated action completed successfully.

These activities have different purposes. Live Response supports investigation, package collection supports evidence gathering, and isolation supports containment. None should be treated as a substitute for the others.

## 10. Key Findings and Skills Demonstrated

The practical exercise provided experience with the following Microsoft Defender XDR capabilities:

- Enabling Live Response.
- Initiating a remote endpoint investigation session.
- Inspecting network connection information.
- Initiating investigation package collection.
- Reviewing evidence associated with investigation package collection.
- Initiating device isolation and reviewing the resulting status.
- Connecting endpoint investigation findings with incident response actions.
- Recognising the importance of validating action outcomes.

The exercise reinforced the importance of gathering evidence and taking containment actions while maintaining a clear distinction between suspected activity and confirmed malicious behaviour.

## 11. Lessons Learned

### Investigation and response are complementary

Identifying suspicious activity is only one part of incident handling. Analysts must also gather supporting evidence, assess the risk and determine whether containment or other response actions are justified.

### Evidence collection supports further analysis

An investigation package can provide useful artefacts beyond the information visible in an alert.

### Isolation is a containment action

Isolating an endpoint can help limit potential harm while the incident is investigated. It does not automatically remove the cause of the incident or prove that the device is clean.

### Response actions must be verified

An action being initiated is not equivalent to successful completion. Analysts should check the platform's status or returned results to confirm what occurred.

### Documentation should reflect the available evidence

A reliable incident report distinguishes observed events, investigative hypotheses, configured actions and confirmed outcomes. This prevents conclusions from going beyond the available evidence.

## 12. Scope and Limitations

This phase was completed in a controlled learning environment using Microsoft Defender XDR capabilities.

The results reflect the endpoint state and telemetry available during the exercise. Network connection information represents the information returned at the time of inspection and may not show every historical connection.

The investigation package's usefulness depends on the artefacts collected and their relevance to the incident. Device isolation is a containment measure, not proof of remediation or complete eradication of a threat.

## 13. Conclusion

This phase demonstrated practical incident response capabilities in Microsoft Defender XDR, including Live Response, network connection investigation, investigation package collection and device isolation.

It extended the earlier detection and investigation work by demonstrating how an analyst can gather additional endpoint evidence and apply containment measures. Together, these skills form an important part of the incident handling workflow expected of a security operations analyst.

The exercise also reinforced a core SOC principle: response actions should be selected based on the available evidence, executed through the appropriate controls and verified before their outcomes are reported.
