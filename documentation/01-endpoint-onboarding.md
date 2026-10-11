# 01 - Endpoint Onboarding to Microsoft Defender XDR

## 1. Objective

The objective of this exercise was to prepare and onboard a Windows endpoint into Microsoft Defender for Endpoint and verify that the device became visible in the Defender security environment.

The exercise covered device group creation, configuration of device group settings, retrieval and execution of the onboarding script and verification of the endpoint in the device inventory.

## 2. Tools and Technologies

- Microsoft Defender XDR
- Microsoft Defender for Endpoint
- Windows 10/11 endpoint environment
- Device groups
- Endpoint onboarding script
- Microsoft Defender Applied Skills lab environment

## 3. Implementation Procedure

### Step 1: Create a Device Group

A device group for Windows 10 and Windows 11 devices was created in the Microsoft Defender environment.

Device groups help security teams organise endpoints and manage applicable access and security operations settings. Their behaviour depends on the configured group settings and the Defender environment.

**Evidence:** Screenshot showing the creation of the Windows 10/11 device group.

- ![Creating the Windows 10 and Windows 11 device group](/screenshots/endpoint-onboarding/Device%20Group%20Settings.png)
- ![Device Group Created](/screenshots/endpoint-onboarding/Device%20Group%20Created.png)



### Step 2: Download the Onboarding Script

The endpoint onboarding script was downloaded from the Defender environment for use on the target Windows device.

The onboarding script provides a way to configure the endpoint for onboarding into Microsoft Defender for Endpoint. The exact actions performed depend on the script and onboarding package supplied by the platform.

**Evidence:** Screenshot showing the onboarding script download.

- ![Downloading the endpoint onboarding script](/screenshots/endpoint-onboarding/Onboarding%20Script.png)

### Step 3: Execute the Onboarding Script

The downloaded onboarding script was executed on the target Windows endpoint as part of the onboarding procedure.

This step applied the onboarding configuration required for the device to connect to the Defender for Endpoint environment.

**Evidence:** Screenshot showing execution of the onboarding script.

![Running the endpoint onboarding script](/screenshots/endpoint-onboarding/Successfully%20Onboarded%20Endpoint.png)

### Step 4: Verify Endpoint Visibility

Following the onboarding procedure, the endpoint was located in the Assets or device inventory section of the Defender portal.

The device's appearance in the inventory shows evidence that it was visible within the Defender environment.

**Evidence:** Screenshot showing the endpoint in the Assets tab.

![Successfully onboarded endpoint visible in the Defender inventory](/screenshots/endpoint-onboarding/Endpoint%20visible%20in%20XDR.png)

## 4. Security Significance

Endpoint onboarding is an important part of endpoint detection and response. It enables supported security capabilities and provides visibility into endpoint activity for investigation and response.

The device group supports endpoint organisation and administration, while the onboarding script establishes the endpoint's onboarding configuration.

Once onboarded, an endpoint can provide telemetry that helps security analysts investigate suspicious processes, examine device activity and respond to potential threats, subject to the device's health, configuration, licensing and enabled capabilities.

## 5. Key Learning Outcomes

This exercise provided practical experience with:

- Creating and configuring endpoint device groups.
- Retrieving an onboarding script from the Defender environment.
- Executing the onboarding script on a Windows endpoint.
- Verifying endpoint visibility through the Defender device inventory.
- Understanding the role of endpoint onboarding in security monitoring and incident response.

## 6. Conclusion

The onboarding exercise covered the preparation, deployment and verification stages for a Windows endpoint in the Microsoft Defender environment.

This established the foundation for the following endpoint protection, incident investigation and response activities documented in this project.
