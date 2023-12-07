# Securing-Azure-Resources-in-accordance-with-NIST-SC-7
Introduction
[Talk about what you will be doing in this lab]

Make sure to secure VM NSG
Configure Azure Private Link and Firewall for your Azure Key Vault instance and storage account 
The first thing that will be done is to enable the Key Vault Firewall. This is done by disabling public access to the firewalls and virtual networks of the key vault. 
[Insert image here] 

The next thing to do is to create a Private endpoint. This is done to make the key vault accessible through the Virtual Network and subnet rather than being accessible to the internet.
	[Insert image here] 

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
