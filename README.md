# Enterprise Cybersecurity Mega Lab
## Overview
This project is an enterprise-style network security lab designed and implemented in **Cisco Packet Tracer**.
The objective of this project is to demonstrate practical knowledge of network design, segmentation, routing, network security controls, monitoring, security testing, and basic incident response.
The lab simulates a multi-department organization containing IT, HR, Management, Guest, Servers, Security Operations Center (SOC), and Administration networks.
The project was built as a hands-on cybersecurity portfolio project to demonstrate practical networking and defensive security skills.
## Objectives
The main objectives of this project are to:
* Design an enterprise-style segmented network
* Implement VLAN-based network segmentation
* Configure inter-VLAN routing using Router-on-a-Stick
* Configure DHCP for internal networks
* Configure static addressing for servers
* Secure network devices using local authentication and SSH
* Implement switch port security
* Disable unused switch ports
* Implement extended ACLs for network isolation
* Simulate unauthorized network access
* Monitor security events and network activity
* Investigate a simulated security incident
* Document security findings and response procedures
## Network Architecture
The network contains the following departments and VLANs:
| VLAN | Department     | Network         | Gateway      |
| ---: | -------------- | --------------- | ------------ |
|   10 | IT             | 192.168.10.0/24 | 192.168.10.1 |
|   20 | HR             | 192.168.20.0/24 | 192.168.20.1 |
|   30 | Management     | 192.168.30.0/24 | 192.168.30.1 |
|   40 | Guest          | 192.168.40.0/24 | 192.168.40.1 |
|   50 | Servers        | 192.168.50.0/24 | 192.168.50.1 |
|   60 | SOC            | 192.168.60.0/24 | 192.168.60.1 |
|   70 | Administration | 192.168.70.0/24 | 192.168.70.1 |
### Devices
* 1 Router — R1
* 3 Switches — SW1, SW2, SW3
* Multiple department endpoints
* 2 Servers — SRV-01 and SRV-02
## Network Topology
The physical topology consists of:

                         R1
                          |
                       Gi0/1
                          |
                       SW1
                     /     \
                 Gi0/2     Fa0/24
                   /         \
                 SW2         SW3
### SW2
* IT endpoints → VLAN 10
* HR endpoints → VLAN 20
### SW3
* Management endpoints → VLAN 30
* Guest endpoints → VLAN 40
* Servers → VLAN 50
* SOC endpoints → VLAN 60
* Administration endpoints → VLAN 70
## Security Architecture
The lab implements multiple layers of defensive security.
### 1. VLAN Segmentation
Each department is placed into a separate VLAN to logically isolate network traffic.
### 2. Router-on-a-Stick
R1 provides inter-VLAN routing through subinterfaces on `GigabitEthernet0/1`.
### 3. DHCP
R1 provides DHCP services for:
* IT
* HR
* Management
* Guest
* SOC
* Administration
Servers use static IP addressing.
### 4. SSH
Network devices are configured for secure remote administration using:
* Local user authentication
* RSA keys
* SSH version 2
* VTY authentication
* SSH-only remote access
### 5. Port Security
Access ports use:
* Maximum MAC address limit
* Sticky MAC learning
* Restrict violation mode
This helps prevent unauthorized devices from connecting to protected access ports.
### 6. Unused Port Protection
Unused switch ports are administratively shut down to reduce the available attack surface.
### 7. Guest Network Isolation
An extended ACL named `GUEST-RESTRICTION` prevents the Guest VLAN from accessing protected internal networks.
The Guest network is restricted from:
* IT
* HR
* Management
* Servers
* SOC
* Administration
Guest users can still communicate with permitted destinations outside these protected networks.
## Security Testing
The project includes simulated security testing to verify that the implemented controls operate correctly.
### Guest Network Attack Simulation
A simulated unauthorized Guest user attempts to access internal resources.
The following networks are tested:
IT          192.168.10.0/24
HR          192.168.20.0/24
Management  192.168.30.0/24
Servers     192.168.50.0/24
SOC         192.168.60.0/24
Admin       192.168.70.0/24
The ACL should block these unauthorized connections.
ACL counters are then examined to confirm that the security control detected and blocked the traffic.
## Monitoring and Detection
The lab uses Cisco IOS verification and monitoring commands to examine network and security status.
Examples include:
show ip interface brief
show ip route
show ip dhcp pool
show ip dhcp binding
show access-lists
show port-security
show port-security address
show interfaces trunk
show vlan brief
show interfaces status
show ip ssh
show logging
These commands provide visibility into:
* Interface status
* Routing
* DHCP assignments
* ACL activity
* Port-security events
* VLAN configuration
* Trunk status
* SSH configuration
* Device logs
## Incident Response Scenario
A simulated security incident is included in the project.
### Scenario
An unauthorized device connected to the Guest network attempts to access protected internal resources.
### Detection
The activity is identified through:
* Failed connectivity attempts
* ACL match counters
* Network verification commands
### Investigation
The source network and targeted internal networks are identified.
### Containment
The existing Guest network ACL prevents access to protected resources.
### Verification
ACL counters and connectivity tests are used to confirm that the attack traffic was blocked.
### Documentation
The incident and response process are documented in the `Incidents/` directory.
## Project Evidence
The repository contains supporting evidence organized into the following directories:
Documentation/
    Project documentation and technical explanations
Incidents/
    Simulated security incidents and incident-response documentation
Packet Tracer/
    Cisco Packet Tracer project files
Screenshots/
    Verification and testing evidence
Topology/
    Network topology diagrams and related documentation
## Key Technologies
* Cisco Packet Tracer
* Cisco IOS
* VLAN
* 802.1Q Trunking
* Router-on-a-Stick
* DHCP
* SSH
* Extended ACL
* Switch Port Security
* MAC Address Security
* Network Monitoring
* Incident Response
* Network Segmentation
## Skills Demonstrated
This project demonstrates practical experience with:
* Network architecture
* Cisco IOS configuration
* VLAN implementation
* Inter-VLAN routing
* DHCP configuration
* Network segmentation
* Access control
* SSH administration
* Switch hardening
* Port security
* ACL configuration
* Security monitoring
* Attack simulation
* Incident investigation
* Incident containment
* Technical documentation
## Project Status
**Status: Completed**
The network configuration, security controls, security testing, monitoring activities, and simulated incident-response workflow have been implemented and verified.
## Disclaimer
This project was created for educational and portfolio purposes in a controlled Cisco Packet Tracer environment.
All security testing was performed against the simulated network created for this project.
## Author
**Amir Muhammad**
Cybersecurity Student | Network Security | SOC & Defensive Security
This repository represents part of my practical cybersecurity learning journey.
