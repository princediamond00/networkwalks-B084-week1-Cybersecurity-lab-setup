


<div align="center">

#  Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Emeka%20Prince-C00000?style=flat-square" />
</p>
---

##  Project Overview

This project involves building a virtual laboratory for cybersecurity learning and penetration-testing exercises using Oracle VirtualBox and Kali Linux.

The environment provides a dedicated spaceto pratice security-related activities without directly affecting the host comuter or exposing it to certain risks. It is designed to support pratical exercises involving network discovery,reconnaissance, vulnerability testing and the use of cybersecurity tools.

A private virtual network is been configured to connect the laboratory machines, making it possible to intoduce additional virtual machines as testing targets when needed.

## Project Objectives

The key goals of this setup are to:

- Install and configure VirtualBox.
- Install and import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

---

## 3. Purpose of the Laboratory

The laboratory is intended to provide a controlled space for learning and practising cybersecurity techniques.

The environment can support practical activities such as:

- Discovering devices and services on a network.
- Scanning ports.
- Assessing potential vulnerabilities.
- Examining network packets.
- Testing web application security.
- Practising exploitation techniques.
- Exploring and testing security tools.

*Responsible use:* Testing must be restricted to systems that you own or have clear permission to assess. Never use the tools in this laboratory against unauthorized systems.

## 4. Laboratory Architecture

The setup consists of a Windows host computer running VirtualBox, with Kali Linux operating as a virtual machine connected to a dedicated NAT Network.

The network is designed to accommodate more virtual machines in later exercises. These additional machines can serve as targets for authorized testing within the laboratory.

## 5. Hardware and Network Configuration

| Component | Specification |
|---|---|
| Host Operating System | Windows 10 |
| Host Memory | 8 GB RAM |
| Processor | Intel Core i5 |
| Virtualization Software | VirtualBox 7.2 |
| Guest Operating System | Kali Linux 2026.2 |
| Kali VM Memory | 3075 MB |
| Network Mode | NAT Network |
| Network Prefix | 10.0.0.0/24 |
| Kali IPv4 Address | 10.0.0.2/24 |
| Default Gateway | 10.0.0.1 |
| DNS Server | 8.8.8.8 |
| Reserved Range for Future VMs | 10.0.0.3–10.0.0.99 |


![VirtualBox]  
(screenshots/01 Oracle VirtualBox Manager.png)



Note: Confirm that the processor, memory allocation and network values mat#ch your actual setup before publishing.

## 6. Implementation Procedure

### Step 1: Installing 7-Zip

The first requirement was an archive extraction utility. 7-Zip was selected because it supports the .7z format commonly used to distribute compressed virtual-machine packages.

*Software:* [Download 7-Zip](https://7-zip.org/download.html)

### Step 2: Installing VirtualBox

VirtualBox was installed to provide the platform for creating and managing the virtual machines used in the laboratory.

*Software:* [Download VirtualBox](https://virtualbox.org/wiki/Downloads)

### Step 3: Setting Up the NAT Network

A separate NAT Network was configured in VirtualBox to provide a common network for the laboratory's virtual machines.

The network settings were defined as follows:

| Setting | Value |
|---|---|
| Network Name | NatNetwork |
| IPv4 Prefix | 10.0.0.0/24 |
| DHCP | Enabled |
| IPv6 | Disabled |

This networking mode was chosen because it allows multiple virtual machines attached to the same NAT Network to communicate with one another while  also supporting outbound connectivity.

This arrangement provides the networking foundation for future attacker and target machines.

### Step 4: Importing Kali Linux

Kali Linux was obtained from its official distribution website and imported into VirtualBox as a virtual machine.

The virtual machine's first network adapter was assigned to the newly created NAT Network.

*Adapter configuration:*

| Setting | Value |
|---|---|
| Adapter | Adapter 1 |
| Attached To | NAT Network |
| Network | NatNetwork |
| Adapter Type | Intel PRO/1000 MT Desktop |

The virtual machine was allocated *3075 MB of RAM*.

A shared folder was also set up to make it possible to exchange necessary files between Windows and the Kali Linux environment.

*Kali Linux:* [Official download page](https://kali.org/get-kali)

### Step 5: Configuring Kali Linux Networking

After importing the virtual machine, its network settings were inspected and configured to use a consistent IPv4 address.

The intended network parameters were:

| Parameter | Value |
|---|---|
| IPv4 Address | 10.0.0.2 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.0.1 |
| DNS Server | 8.8.8.8 |

Using a consistent address makes it easier to identify the Kali machine during subsequent laboratory exercises and when recording network activity.

### Step 6: Creating a Recovery Snapshot

Once the initial virtual-machine and network configuration had been completed, a snapshot was created in VirtualBox.

*Snapshot label:* Clean Kali - Network Setup

This snapshot serves as a reference point representing the initial configured state of the virtual machine.

It can be restored if later experiments result in unwanted changes or problems with the operating system or network configuration.

## 7. Laboratory Verification

After configuration, a series of checks can be performed to confirm that the virtual machine and its network are functioning as expected.

| Verification | Command / Action | Expected Outcome |
|---|---|---|
| Inspect IP configuration | ip a | Configured Kali IP address is visible |
| Check gateway reachability | ping 10.0.0.1 | Replies received from the gateway |
| Check external connectivity | ping 8.8.8.8 | Successful replies |
| Check DNS resolution | nslookup networkwalks.com | Domain name resolves to an IP address |
| Check Nmap installation | nmap --version | Installed Nmap version is displayed |
| Check snapshot recovery | Restore snapshot, then run ip a | Original network configuration is available |

### Reference Network Values

The expected configuration includes:

- *Kali IP:* 10.0.0.2/24
- *Gateway:* 10.0.0.1
- *DNS:* 8.8.8.8

Actual command output and screenshots should be used as evidence of successful verification.

## 8. Challenges and Resolutions

Recording technical difficulties and the steps taken to address them is part of documenting the laboratory setup.

But unfortunately i didn't encounter any challenges and technical difficulties . All thanks to the well detailed and explained youtube videos from my instructor **WAQAS KARIM CCIE**

## 9. Knowledge and Skills Gained

This exercise provided practical experience with virtual-machine deployment, network configuration and the preparation of a cybersecurity testing environment.

The main concepts covered include:

### 9.1 NAT and NAT Network

The exercise helped demonstrate the difference between the standard NAT mode and NAT Network mode in VirtualBox.

NAT Network allows connected virtual machines to communicate over a shared virtual network while using network address translation for external connectivity.

This makes it suitable for a laboratory that may contain several virtual machines.

### 9.2 Virtual Machine Networking

Configuring the virtual adapter provided an opportunity to understand how virtual machines connect to networks and how adapter settings influence communication.

### 9.3 Static IPv4 Configuration

The network configuration process covered important IPv4 parameters, including IP addresses, subnet masks, gateways and DNS servers.

### 9.4 Virtual Machine Snapshots

Creating a clean snapshot demonstrated the importance of maintaining a recoverable starting point before carrying out experimental or potentially disruptive activities.

### 9.5 Technical Documentation

The project also highlighted the importance of recording setup procedures, commands, configuration details, test results and solutions to encountered problems.

## 10. Security and Ethical Considerations

This environment is designed for educational and authorized cybersecurity activities.

Any assessment, scanning or testing must be limited to systems that belong to the user or for which explicit permission has been granted.

## 11. Software and Reference Resources

| Resource | Official Website |
|---|---|
| 7-Zip | https://7-zip.org/download.html |
| VirtualBox | https://virtualbox.org/wiki/Downloads |
| Kali Linux | https://kali.org/get-kali |

## 12. Author Information

**Name:** Emeka Chukwuemeka Prince  
**Field:** Computer Science  
**Area of Interest:** Cybersecurity and Ethical Hacking  
**LinkedIn:** [https://www.linkedin.com/in/chukwuemeka-emeka-477404447?utm_source=share_via&utm_content=profile&utm_medium=member_android]


## 13. Assignment Information

| Field | Details |
|---|---|
| Program | Cybersecurity at Networkwalks |
| Week | 01 |
| Project Title | Cybersecurity & Pentesting Lab Setup |
| Repository | GitHub |……
