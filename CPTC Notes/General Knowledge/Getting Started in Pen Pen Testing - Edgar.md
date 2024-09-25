
# Info-sec Overview

Cyber Security, or **Information Security** (infosec) has multiple domains, some but not all include:
- Network and infrastructure security 
- Application security 
- Security testing 
- Systems auditing 
- Business continuity planning 
- Digital forensics 
- Incident detection and response 

**Info-sec**: The practice of protecting data from unauthorized access, changes, unlawful use, disruption, and more. 
- Info-sec professionals may also try to reduce impact of these incidents

**Data**: Physical or electronic knowledge. 

**CIA Triad**: Protecting the *"confidentiality, integrity, and availability of data"*

---
## Risk Management Process
Data must be protected in a efficient way, this is done using the *risk management process*

| Step                 | Explanation                                                                                                                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Identifying the Risk | Identifying risks the business is exposed to, such as legal, environmental, market, regulatory, etc...                                                                                       |
| Analyze the Risk     | Analyzing the risks to determine their impact and probability. The risks should be mapped to the organization's various policies, procedures, and business processes                         |
| Evaluate the Risk    | Evaluating, ranking, and prioritizing risks. Then, the organization must decide to **accept** (unavoidable), **avoid** (change plans), **control** (mitigate), or **transfer** risk (insure) |
| Dealing with Risk    | Eliminating or containing the risks as best as possible. This is handled by interfacing directly with the stakeholders for the system or process that the risk is associated with            |
| Monitoring Risk      | All risks must be constantly monitored. Risks should be constantly monitored for any situational changes that could change their impact score. (low, medium, high)                           |

---
## Red Team vs. Blue Team

Red is offensive and blue is defensive

Red
- Pen testing 
- Pretends to be a adversary 
- find weaknesses in a business
- social engineering 

Blue 
- defense 
- most jobs
- sys admin
- coming up with policies 
- responding to threats 
- updating machines
---
## Role of Penetration Testers 
**Possible roles** 
- Security Assessor 
- Network penetration tester 
- web application penetration tester 
- red teamer
**What do they do**
- Helps an organization identify risks in ts external and internal networks. May include:
	- network 
	- web
	- sensitive data exposure
	- configs
	- issues that could lead to the companies reputation being harmed
**What pentesters identify**
- Risks to a organization
- Provide information on how to reproduce these risks 
- Give advice on either mitigating or remediating the issues identified

# Getting Started with a Pen-test Distro
As a pen tester, you will attempting to break into many types of machines, you must try to be as prepared as possible. One of the best ways to practice is by using VMs. This gives you the ability to open up a virtual machine on your actual machine, on Linux, windows, or more.
## Choosing a Distro
Many types of Linux distributions (distros) for pen testing. 
- Specialize in specific areas 
- Can customize 
- Debian is known for pen testing 
- Ubuntu is another good option
- HTB will be using **Parrot OS**
- Suggested to do pen tests on fresh VMs to avoid conflicts from previous events 

## Setting Up a Pen-test Distro
### Ways of setting up local pen-testing distros
- install as base OS (not recommended)
- dual boot (takes long time)
- Install using virtualization (**Recommended**)

### Virtualization Options
- Hyper-V on Windows 
- Proxmox or VMware 
- Virtual Box 
- VMware Workstation layer
- VMware Workstation (paid)

### What is a Hypervisor
**Hypervisor**: A software that allows us to create and run virtual machines (VMs).
- enable us to use our host computer to run multiple VMs by virtually sharing memory and processing resource
- Runs isolated from the primary Operating System (OS)
- The more RAM, the more VMs you can run

## ISO
**ISO**: An ISO file is a CD-ROM that can be mounted within our hypervisor of choice to build the VM by installing the operating system ourselves.

## OVA 
**OVA**: The OVA file is a pre-built virtual appliance that contains an **OVF** XML file that specifies the VM hardware settings and a **VMDK**, which is the virtual disk that the operating system is install on. and **OVA** is pre-built and therefore can be rapidly deployed to get up and running quicker.

## Practicing with Parrot 
Parrot OS is the linux distro that will be used for HTB. You should be able to use other distros for non-specific projects.

# Staying Organized 
It important to organize your notes, files, and any other documentation you have for future use.

## Folder Structure 
When attacking a single box, lab, or client environment, we should have a **clear folder structure on our attack machine**, such as:
- scoping information
- enumeration data 
- evidence of exploitation attempts
- sensitive data such as credentials
- other data obtained during recon, exploitation, and post-exploitation.
*Example Folder Structure*
![[Pasted image 20240925131040.png]]**Client**: Acme Company 
They have two different assessments going on:
- **IPT**: Internal Penetration Test 
- **EPT**: External Penetration Test
Under each folder, there are folders for saving different types of data:
- scan data 
- any relevant tools
- logging output
- scoping information 
	- list of IPs
	- networks to feed to our scanning tools
- Evidence: containing any proof of them finding sensitive information 

**Other options**:
- creating a folder for each target host and saving screenshots within
- Organize their notes by host or network and save screenshots directly into the note taking tool
- Experiment with folder structures and see what work best for you to stay organized and work most efficiently


## Note Taking Tools
Be sure to find a note taking app you like. You need something that keeps things organized like:
- Cherry tree
- Obsidian 
- Google docs 
- Gitbook
- Visual Studio
- Evernote 
- Notion
- Sublime Text
- Notepad++

## Other Tools and Tips
- Take notes on everything you learn, it may be useful in future use.
- Make cheat sheets 
- Make checklists 
- Report templates for different assessment types 
- build a findings/vulnerability database
	- Spreadsheet 
	- Can be more complex

## Moving On
Try out different things and pick one you like


# Connecting Using VPN
**Virtual Private Network (VPN)**: Allows you to connect to a private (internal) network and access hosts and resources as if you were directly to the target private network
- Secured communications over shared public networks 
- Private network

### How VPN Works
Routes our connecting devices internet connection through the targets VPN's private server instead of our internet service provider (ISP)
- Data originates from the VPN server
- Your IP address changes 

### Types of VPNs
Two main types of remote access VPNs:
1. **Client-based VPN**
	- Requires use of client-based software to establish the VPN connection
	- Once connected it works as if the computer is connected directly to the target VPN
1. **SSL VPN**
	- Uses the web browser as the VPN client
	- Connection established between browser and SSL VPN
	- Only configured to access web-based applications without needing to install it

## Why Use A VPN?
Can be used for many reasons, some include:
- Connect to a VPN server in another country to obscure your browsing traffic or disguise your public IP address
- Increase level of security and privacy 
- Usage of a VPN **does not** guarantee anonymity, but can be useful to bypass certain network/firewall restrictions 

## Connecting to HTB VPN
HTB created weak machines for people to test. It requires them to connect to the target network via VPN in order to access it. You cannot connect from outside the internet. 
**Important Notes to Keep in Mind**
- Always consider the network to be "hostile"
- Only connect from a virtual machine 
- Disallow password authentication if SSH is enabled on our attacking VM

### Connecting to a VPN
`sudo openvpn user.ovpn` 
- `sudo`: elevated privileges, must have password
- `openvpn`: The vpn service we are trying to connect to
- `user.ovpn`: The vpn "profile" file that is used to connect to vpn
![[Pasted image 20240925140615.png]]

`ifconfig`: Check your ip address
![[Pasted image 20240925140655.png]]
IP: 10.10.x.2

`netstat -rn`: shows the networks accessible via the VPN
![[Pasted image 20240925140711.png]]

# Common Terms 
Pen Testing is complex and will have a lot of vocabulary all over the place. Here are the most common

## What is a Shell?
