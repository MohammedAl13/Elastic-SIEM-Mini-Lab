# Elastic-SIEM-Mini-Lab

![image](https://github.com/MohammedAl13/Elastic-SIEM-Mini-Lab/assets/154714127/7465f204-111b-4528-a11d-c3492f163387)

## Introduction

In this project, I used Elastic Stack and Virtualbox to setup a miniature SIEM enviroment. I will be using Virtualbox to host a Kali Linux Virtual Machine and will generate queries that will be collected by Elastic stacks Security Information and Event Management (SIEM). In this lab I will also be seting up an agent to forward data to the SIEM, in order to analyze the logs and create a dashboard. The purpose of this homelab is to simulate a miniature SIEM enviroment in order to gain some understanding of some of the work done within a proffessional SOC.



This miniature SIEM lab consists of the following components:

- Elastic Stack
- Virtualbox
- Kali Linux

***This homelab is not like other homelabs as it will be quite short, consisting of a few basic steps. All parts of this lab can be done for free.***

## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:


Start Time: 2023-12-18 08:20:09


Stop Time:  2023-12-19 08:20:09

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 50656
| Syslog                   | 943
| SecurityAlert            | 5
| SecurityIncident         | 26
| AzureNetworkAnalytics_CL | 129482

## Attack Maps After Hardening / Security Controls

```All map queries returned no results due to no instances of malicious activity for the 24-hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics I measured in my environment for another 24 hours after NIST 800-53 security controls were applied:


Start Time: 2023-12-21 01:57:37


Stop Time:  2023-12-22 01:57:37

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 12541
| Syslog                   | 5
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0


## Percentage of Security Events 


The following table compares the security events from before hardening the environment vs afterward and shows to what percent were security events reduced:


| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | -75.24%
| Syslog                   | -99.47%
| SecurityAlert            | -100%
| SecurityIncident         | -100%
| AzureNetworkAnalytics_CL | -100%



## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure, and log sources were integrated into a Log Analytics workspace. The firewalls and NSGs for the VMS were disabled, leaving them exposed to the public internet. Microsoft Sentinel was then employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. NIST 800-53 security controls were implemented to harden the environment. It is noteworthy that the number of security events and incidents were drastically reduced after the NIST 800-53 security controls were applied, demonstrating their effectiveness.
