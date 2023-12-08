# Securing-Azure-Resources-in-accordance-with-NIST-SC-7

![Securing the network](https://github.com/TherealvictorIT/Securing-Azure-Resources-in-accordance-with-NIST-SC-7/assets/125538763/0b0ad44e-fcb1-4454-a528-ad18923c0c33)

## Introduction
After allowing the VMs to be exposed to the internet for over 24 hours, the next step is to implement security measures and observe the outcomes for an additional 24 hours. The objective is to ensure alignment with NIST SC-7 recommendations, emphasizing restricted access within a secure network environment. Tasks include securing Azure Key Vault and a Storage Account by disabling public access, establishing private endpoints, and configuring Network Security Groups for the VMs.

## Configuring Azure Private Link and Firewall for Azure Key Vault instance and Storage account 
The first thing that will be done is to enable the Key Vault Firewall. This is done by disabling public access to the firewalls and virtual networks of the key vault. 

<img width="1140" alt="Enabling Firewall for Key Vault" src="https://github.com/TherealvictorIT/Securing-Azure-Resources-in-accordance-with-NIST-SC-7/assets/125538763/c683912f-207c-4f2b-8716-1f25d316b872">

Next, a Private Endpoint will be created to ensure that the Key Vault is accessible exclusively through the Virtual Network and subnet, eliminating public internet access.

<img width="600" alt="Creating Private endpoint" src="https://github.com/TherealvictorIT/Securing-Azure-Resources-in-accordance-with-NIST-SC-7/assets/125538763/02503884-7316-4782-b286-591d5d19a60e">
 

The same thing will be done with the Storage account. You will first make sure that you disable Allow Blob anonymous access by going to the configuration settings.
[Insert image here] 
Disable public access from the Internet. Create a private endpoint
	[Insert image here]
Once the private endpoints are setup we can test them by doing an nslookup and observing if they resolve to a private IP address using a VM that is part of the subnet. In this case both storage and key vault resolve to a private IP address.
	[Insert image here]
Configure VM NSG inbound port rule 

In order to limit access to the virtual machine the VM’s NSG will be configure so that only My IP address is able to establish a connection with the VM. This is done for both the Windows VM and the Linux VM. 
[Insert image here] 

Create Network Security Rule and attach it to the subnet
In order to satisfy the Microsoft Cloud Defender recommendation of attaching an NSG to a subnet an NSG is created and attached to the subnet but no rules will be added to it. In a production environment the NSG should be configured but in this lab we will not do that.  
	[Insert Image here]
Show SC.7 Boundary protection results with image and description 
Explain how everything is setup now

Include the results you get from having the nsg setup and secured 
