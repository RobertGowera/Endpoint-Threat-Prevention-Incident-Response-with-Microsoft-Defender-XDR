# 02 - Attack Surface Reduction Policy Configuration

## 1. Objective

The objective of this exercise was to configure an Attack Surface Reduction (ASR) security policy in the Microsoft Defender environment.

The policy was designed to block JavaScript or VBScript from launching downloaded executable content, reducing the risk associated with certain script-based attack techniques.

## 2. Tools and Technologies

- Microsoft Defender security environment
- Endpoint Security Policy
- Attack Surface Reduction (ASR)
- Microsoft Defender Applied Skills lab environment

## 3. Policy Configuration

An Endpoint Security Policy was created and configured to use the ASR rule designed to block JavaScript or VBScript from launching downloaded executable content.

This rule is intended to prevent potentially malicious scripts from launching downloaded executable files, helping reduce opportunities for malware execution through specific script-based techniques.

**Evidence:** Screenshot of the ASR policy settings.

![Attack Surface Reduction policy settings](/screenshots/endpoint-security-policy/New%20Endpoint%20Security%20Policy%20Settings.png)

## 4. Policy Creation

After configuring the policy, the policy creation process completed successfully in the Defender environment.

This demonstrated the configuration and creation of the preventive security control.

**Evidence:** Screenshot showing successful policy creation.

![Successfully created Attack Surface Reduction policy](/screenshots/endpoint-security-policy/New%20Endpoint%20Security%20Policy%20Settings.png)

## 5. Security Significance

Attack Surface Reduction rules help organisations reduce exposure to common attack techniques by restricting specific application and process behaviours.

The configured rule focuses on JavaScript or VBScript launching downloaded executable content. It is a preventive control intended to interrupt this particular execution pattern.

ASR complements other security capabilities, including endpoint monitoring, threat detection and incident response. It should not be treated as a replacement for those capabilities.


## 6. Key Learning Outcomes

This exercise provided practical exposure to:

- Creating an endpoint security policy.
- Configuring an Attack Surface Reduction rule.
- Understanding preventive endpoint security controls.
- Distinguishing policy creation from policy deployment and enforcement verification.
- Understanding how preventive controls complement security monitoring and incident response.

## 7. Conclusion

The ASR policy was configured and created successfully in the lab environment. The policy was intended to reduce the risk of JavaScript or VBScript launching downloaded executable content.

Further deployment or enforcement claims will depend on the additional evidence available from the lab.
