# Windows Domain Controller Configuration/ Active Directory configuration
This is an overview of my experience configuring a Domain Controller to provide a client internet access through the DC(Domain Controller) as well as Configure Active Directory. A step by step guide for the lab will also be included in a link below (:

## Objective
The objective of the lab is to configure and manage network infrastructure through a Windows domain controller. The primary goal was to enable client connectivity to the internet via the domain controller, while also implementing Active Directory to be able to enforce user policies within the domain in a future Lab. This setup aimed to simulate a real-world corporate network. 

### Skills Learned

- Understanding of IP addresses and network configuration
- A more advanced understanding of windows server operating system and configuration.
- Enchanced knowledge of dorporate domain setup with active directory


### Tools Used

- VMware to host the server alongside the client computer
- Server Manager
- Server Configuration Tools
- Active Directory Users and Computers
  

## Diagram
This network diagram outlines the setup for our upcoming lab environment. In this scenario, the client computer is configured to route all internet traffic through the internal network, ultimately passing through the domain controller for internet access. This design utilizes a domain controller (DC) that serves dual purposes: managing domain resources and handling network routing with RAS/NAT functionalities. 
![Screenshot (149)](https://github.com/user-attachments/assets/5dadffeb-147c-433e-9fca-5804f720ba44)

## Summary of Lab
In this lab, I configured a Domain Controller, including setting up and enabling Active Directory, DNS, and DHCP services. I defined a DHCP scope to manage IP address distribution within the network. A domain named githubdomain.com was created during the configuration. Additionally, I set up two Organizational Units within Active Directory Users and Computers, one for Admin accounts and one for Users where I added three user accounts and one admin account.

This setup ensures centralized management of the network, user authentication, IP address assignment, and domain services while granting us the ability to impliment Group Policies. While also forcing a internet connection through our Domain Controller for a connected client. 

## Challenges and Solutions
### DHCP Configuration Errors
Challenge: Initially there was an issue with the DHCP scope not assigning IP's correctly to the client machinces.

Solution: The issue was related to an incorrect subnet mask once correcting that ensuring the scope was correctly defined, the client recieved an IP address. 

## Step by Step For Lab
<a href="https://github.com/karamkamal1/Domain_Controller-Active-Directory_Configuration_Lab.md/blob/b877a1ccfceb92ad4a78eb88b346e8d98b5f9a47/Step_by_step_Domain_Controller_%26_Active_Directory_Lab.md">Step By Step</a>
