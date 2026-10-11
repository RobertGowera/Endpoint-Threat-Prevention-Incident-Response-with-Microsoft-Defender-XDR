# 03 - Incident Investigation and Custom Detection

## 1. Overview

This phase focused on investigating a security incident in Microsoft Defender XDR following a controlled attack simulation using the `attackscript.ps1` script.

The investigation involved reviewing the incident, examining endpoint telemetry, analysing process relationships, investigating network activity, writing an Advanced Hunting query and creating a custom detection rule.

The objective was to demonstrate a structured incident investigation process and understand how endpoint telemetry can support threat detection and response.

## 2. Objectives

The objectives of this phase were to:

- Execute the provided attack simulation in the lab environment.
- Identify and review the resulting security incident in Microsoft Defender XDR.
- Investigate the affected endpoint using the device timeline and process tree.
- Examine network activity associated with the investigated process.
- Use Advanced Hunting and KQL to identify relevant process execution activity.
- Create and validate a custom detection rule.
- Configure an IP indicator and understand the implications of blocking network destinations.
- Distinguish between observed evidence, suspicious behaviour and confirmed malicious activity.

## 3. Tools and Environment

- **Microsoft Defender XDR:** Incident investigation, endpoint telemetry and security response capabilities.
- **Microsoft Defender Advanced Hunting:** Querying endpoint telemetry using Kusto Query Language (KQL).
- **`attackscript.ps1`:** Microsoft-provided script containing process injection used for the controlled lab simulation.
- **VirusTotal:** External reputation lookup used to investigate the destination IP address.

## 4. Attack Simulation

### Objective

Generate activity for investigation in Microsoft Defender XDR using the attack simulation provided as part of the lab.

### Procedure

1. Ran the provided `attackscript.ps1` script in the lab environment.
2. Reviewed the resulting security telemetry and incident information in Microsoft Defender XDR.
3. Identified the process activity requiring further investigation.
4. Used the incident and endpoint investigation tools to examine the observed behaviour.

### Evidence

![Attack Script Execution](/screenshots/defender-xdr-incident/Attack%20Script%20ran.png)

## 5. Incident Identification and Review

### Objective

Review the incident generated during the exercise and identify the activity requiring further investigation.

### Procedure

1. Opened the relevant incident in Microsoft Defender XDR.
2. Reviewed the available alert information.
3. Examined the incident's associated activity and related alerts.
4. Used the incident details to guide the endpoint investigation.

### Evidence

![Multi-Stage Incident](/screenshots/defender-xdr-incident/Multi-Stage%20Incident.png)
![Process Injection Alert](/screenshots/defender-xdr-incident/Process%20Injection%20Alert.png)


### Findings

The incident investigation focused on suspected process injection or process hollowing behaviour involving PowerShell and Notepad.

The observed process relationship was significant enough to investigate further. However, process names and parent-child relationships alone are not sufficient to confirm process injection or process hollowing. Additional telemetry and contextual evidence are required to establish what occurred.

## 6. Endpoint Timeline and Process Tree Analysis

### Objective

Investigate the sequence of endpoint activity and understand the relationship between the processes involved.

### Procedure

1. Opened the affected device's timeline in Microsoft Defender XDR.
2. Reviewed the sequence of recorded events associated with the investigation.
3. Examined the process tree to understand the relationship between PowerShell and Notepad.
4. Correlated the process information with the incident details and other available telemetry.

### Evidence

![Client 2 Device Timeline](/screenshots/defender-xdr-incident/Client%202%20Device%20Timeline.png)

![Client 2 Process Tree](/screenshots/defender-xdr-incident/Client%202%20Process%20Tree.png)

### Findings and Security Significance

The process tree and device timeline provided complementary views of endpoint activity.

- **Process tree:** Helped establish the observed process relationships.
- **Device timeline:** Helped place events in sequence and correlate activity during the investigation.
- **Incident details:** Provided additional context for prioritising relevant events.

PowerShell launching Notepad is a behaviour worth examining when it occurs in an unexpected context, but it is not conclusive evidence of malicious activity..

The purpose of correlating these sources is to establish a defensible conclusion based on multiple pieces of evidence rather than a single alert or process name.

## 7. Network Connection Investigation

### Objective

Investigate the destination IP address contacted by Notepad and assess whether the connection provided evidence of suspicious activity.

### Procedure

1. Reviewed the network activity associated with the process under investigation.
2. Recorded the destination IP address and observed connection port.
3. Used VirusTotal to look up information about the destination.
4. Compared the reputation findings with the process and incident context.
5. Considered whether the evidence justified treating the destination as malicious.

### Evidence

![Suspicious IP Address Contacted](/screenshots/defender-xdr-incident/Suspicious%20IP%20Address%20contacted.png)
![VirusTotal Screenshot](/screenshots/defender-xdr-incident/Virus-Total-Scan.png)

### Findings

The investigation identified an HTTP connection associated with `notepad.exe`. The VirusTotal lookup suggested that the destination IP address was associated with Microsoft and no malicious detections however it had a community score of -261.

This created an important distinction between suspicious-looking process behaviour and the reputation of the network destination.

A process making an unexpected HTTP connection can justify further investigation, particularly when the process is involved in a security incident. However, the connection alone does not prove that the destination is malicious or that data was exfiltrated.

IP ownership and reputation should be verified using reliable sources and considered alongside the hostname, URL, timing, process command line, DNS information, TLS or HTTP details where available and the surrounding incident evidence.

**Investigation conclusion:** The connection warranted  investigation because of the process and incident involved. The available evidence described here is not sufficient, by itself, to conclude that the Microsoft-associated destination was malicious.

## 8. Advanced Hunting with KQL

### Objective

Use Advanced Hunting to identify process-execution activity matching the behaviour observed during the investigation.

### Detection Query

```kusto
DeviceProcessEvents
| where InitiatingProcessFileName =~ "powershell.exe"
    and FileName =~ "notepad.exe"
```

### Query Explanation

- `DeviceProcessEvents` accesses process creation telemetry available in Microsoft Defender XDR.
- `where` filters the results to records matching the specified conditions.
- `InitiatingProcessFileName =~ "powershell.exe"` filters for events where the initiating process is PowerShell, using a case-insensitive equality comparison.
- `FileName =~ "notepad.exe"` filters for events where the created process is Notepad.
- The `=~` operator performs case-insensitive string equality comparisons.

The query identifies process-creation events in which PowerShell initiated Notepad, provided that the relevant telemetry contains those filenames and fields.

### Evidence

![Advanced Hunting KQL Detection Query](/screenshots/defender-xdr-incident/Advanced%20Hunting%20KQL%20Detection%20Query.png)

### Validation and Findings

The query was executed against the available telemetry and the resulting match evidence showed activity associated with the incident being investigated.

This demonstrated how an observed process relationship can be translated into a repeatable query for identifying similar activity in endpoint telemetry.

The query is intentionally narrow. It can miss other process names, alternate execution methods or different telemetry patterns.


## 9. Custom Detection Rule and Automated Response

### Objective

Create a custom detection rule in Microsoft Defender XDR to identify the process activity observed during the investigation and configure automated response actions to support incident containment and evidence collection.

### Detection Query

```kusto
DeviceProcessEvents
| where InitiatingProcessFileName =~ "powershell.exe"
    and FileName =~ "notepad.exe"
```

### Detection Rule Configuration

The custom detection rule was configured with the following response actions:

- **Collect investigation package:** Collect an investigation package from the affected device to support further analysis and evidence gathering.
- **Isolate device:** Isolate the affected endpoint to help contain potential malicious activity and limit its communication with other systems, subject to the platform's isolation behaviour and permitted connections.

### Procedure

1. Created a custom detection rule using the Advanced Hunting KQL query.
2. Reviewed the rule configuration and summary.
3. Examined the query match evidence and confirmed that it corresponded to activity associated with the incident investigated during the lab.
4. Configured the rule to collect an investigation package and isolate the affected device when the detection triggers.

### Evidence

![Advanced Hunting KQL Detection Query](/screenshots/defender-xdr-incident/Advanced%20Hunting%20KQL%20Detection%20Query.png)

![New Custom Detection Rule](/screenshots/defender-xdr-incident/New%20Custom%20Detection%20Rule.png)

![Detection Rule Summary](/screenshots/defender-xdr-incident/Detection%20Rule%20Summary.png)

### Security Significance

This configuration demonstrates how detection engineering can be connected to incident response. Rather than relying only on an analyst to begin containment and evidence collection manually, a detection rule can be configured to initiate supported response actions when its conditions are met.

Device isolation can help contain a potentially compromised endpoint, while an investigation package can provide additional artefacts for analysis. These actions serve different purposes: isolation focuses on containment, whereas evidence collection supports investigation.


### Validation and Limitations

The available match evidence showed that the query matched activity associated with the investigated lab incident. The rule was also configured to collect an investigation package and isolate the device.

A query match, however, does not simply prove that both response actions executed successfully. Successful execution should be confirmed through the relevant device action status, action history or other available Defender XDR evidence.

The detection query identifies a specific process relationship; it does not, by itself, prove process injection or process hollowing. The response actions are therefore documented as configured capabilities rather than confirmed outcomes unless execution evidence is available.
## 10. IP Indicator Configuration

### Objective

Configure an IP address indicator in Microsoft Defender XDR and examine the security implications of assigning a blocking action.

### Configuration

The indicator was configured with the following settings:

- **Indicator type:** IP address
- **Action:** Block
- **MITRE ATT&CK category:** Execution

### Evidence

![Creating an IP Indicator](/screenshots/defender-xdr-incident/Creating%20an%20IP%20Indicator.png)

![IP Indicator Settings](/screenshots/defender-xdr-incident/IP%20Indicator%20Settings.png)

### Security Significance

Indicators can help security teams apply controls to known or suspected malicious infrastructure.

Blocking a legitimate service address may disrupt normal business activity. An analyst should verify the destination, determine whether the observed connection is genuinely related to malicious behaviour, check the scope of the control and assess possible service impact before implementing a production block.

The configured indicator demonstrates the configuration workflow.

**MITRE ATT&CK note:** The configured category was Execution.

## 11. Key Findings

The investigation demonstrated several practical security operations skills:

- Reviewed a Defender XDR incident and related alert information.
- Investigated endpoint activity using a device timeline and process tree.
- Examined a network connection associated with a process under investigation.
- Used an external reputation source to gather context about an IP address.
- Wrote and executed an Advanced Hunting KQL query.
- Created a custom detection rule and reviewed evidence that it matched relevant incident activity.
- Configured an IP indicator with a blocking action.
- Considered the limitations of individual indicators and the potential impact of blocking legitimate infrastructure.

## 12. Lessons Learned

### Investigation requires correlation

An alert or unusual process relationship is a starting point, not a complete verdict. Analysts should correlate the process tree, timeline, commandline information, network activity and other available telemetry.

### Detection engineering begins with observable behaviour

A useful detection query can be developed from a pattern identified during an investigation. The query must then be tested against available telemetry and assessed for coverage, false positives and false negatives.

### Reputation information requires context

An IP address's reputation or apparent ownership should inform the investigation, but neither reputation nor ownership alone establishes whether a particular connection is benign or malicious.

### Response actions should be evidence-based

Blocking indicators can affect legitimate services. Analysts should verify the evidence and consider operational impact before applying disruptive controls.

## 13. Scope and Limitations

This was a controlled learning exercise using a Microsoft-provided attack simulation and lab telemetry. The findings are limited to the activity and evidence available during the exercise.

The process execution query identifies a specific parent-child process pattern. The IP reputation lookup suggested a Microsoft association, which requires contextual verification rather than an automatic malicious classification.

The indicator configuration demonstrates how a block action can be configured. The custom detection rule's match evidence validates a match against the observed lab activity.

## 14. Conclusion

This phase demonstrated an end-to-end investigation workflow in Microsoft Defender XDR, from reviewing an incident and analysing endpoint telemetry to developing a KQL query, validating a custom detection rule and configuring an IP indicator.

The main lesson was the importance of evidence based analysis. Effective SOC investigation involves identifying relevant patterns, validating them against telemetry, understanding the limits of detection logic and applying response controls only when justified by the available evidence.

