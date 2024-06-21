# Elastic-SIEM-Mini-Lab

![image](https://github.com/MohammedAl13/Elastic-SIEM-Mini-Lab/assets/154714127/7465f204-111b-4528-a11d-c3492f163387)

## Introduction

In this project, I used Elastic Stack and Virtualbox to setup a miniature SIEM enviroment. I will be using Virtualbox to host a Kali Linux Virtual Machine and will generate queries that will be collected by Elastic stacks Security Information and Event Management (SIEM). In this lab I will also be seting up an agent to forward data to the SIEM, in order to analyze the logs and create a dashboard. The purpose of this homelab is to simulate a miniature SIEM enviroment in order to gain some understanding of some of the work done within a proffessional SOC.



This miniature SIEM lab consists of the following components:

- Elastic Stack
- Virtualbox
- Kali Linux

***This homelab is not like other homelabs as it will be quite short, consisting of a few basic steps. All parts of this lab can be done for free.***

Before we can start, a free account must be made on Elastic Stack as this will host our SIEM, Logs, and dashboard
- Go to https://cloud.elastic.co/registration and create and account to start your free trial
- Next, choose “Create Deployment” button and select “Elasticsearch” as the deployment type.
- Next, choose the parameters that fit your needs and hit “Create Deployment”
- Once all the configurations are completed, hit continue

Next, we can now build our Virtual Machines. Any Virtualization software and OS can be used for this Homelab, but for the purposes of this lab, I will be using Virtualbox and a Kali Linux Distribution.
- To download a Kali Linux VM, go to https://www.kali.org/get-kali/#kali-virtual-machines and choose which one suits your need.
- Next, create a Kali Linux VM in your preffered virtualization software using the Kali linux file
- Once the Kali VM is installed, click to start the virtual machine and you will go through a series of screens and prompts which you may need to fill some information
- Once everything is complete, you will be asked to login, both the username and password is "kali"

**Note, if you face difficulty with installing the Kali Linux VM or setting up the virtualization software, either VMware or Virtualbox, there are a plethora of resources and tutorials on youtube which can easily be followed**

In order to collect Logs from our Kali Linux VM, we will need to utilise an Elastic agent. An agent simply put is a tool that collects data from hosts and sends it to the Elastic Stack for monitoring and analysis. Thsi data will be security events collected by the agent and forwarded to the Elastic SIEM. To do this, you must do the following steps:
- Go to the Elastic Home page and at the left top corner, select the menu bar and at the bottom, select "+ Add Integration" button in blue
  
  ![image](https://github.com/MohammedAl13/Elastic-SIEM-Mini-Lab/assets/154714127/4a2ea9b5-0e64-4a56-9f52-6c33dc9317cf)

- Next, you must click Elastic Defend and at the bottom, select "Install Elastic Defend"

You should eventually reach this page

![Install Elastic agent on host](https://github.com/MohammedAl13/Elastic-SIEM-Mini-Lab/assets/154714127/9cceecd0-0759-47f1-a264-375f77aca669)

- Depending on which VM you chose, select which one suits you, for this lab, I used Kali Linux so I will copy the command in the above image.
- Once copied, head over to you Kali VM and open up the terminal which is at the top of the screen.
- In terminal, paste your command and hit enter.
- It may ask you the password so type "kali"
- Once installed, you should be at this screen

![Elastic agent successfully installed onto kali linux](https://github.com/MohammedAl13/Elastic-SIEM-Mini-Lab/assets/154714127/5c27bcd1-666d-4070-ad1c-39191afac0ad)

If you would like to verify whether the agent was successfully installed, you can paste the following command into the terminal: 
sudo systemctl status elastic-agent.service


![check if elastic agent is installed on to kali linux](https://github.com/MohammedAl13/Elastic-SIEM-Mini-Lab/assets/154714127/59f673bf-104e-478a-b892-ac952b1ca5df)

Now that everything is up and running, to verify the agent is working as intended, we can now generate some security events on the Kali Linux VM. If it works, we should be able to see these events as Logs within the Elastic stack SIEM. There are a number of ways to do this, but for the sake of this lab, we will be utilising nmap. 

Nmap is an open-source tool that facilitates network exploration, management, and security assessments. It identifies devices and services within a network, effectively mapping the network structure. Nmap performs scans to detect open ports, ascertain the operating systems and applications in use on target systems, and gather various network-related details.

















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
