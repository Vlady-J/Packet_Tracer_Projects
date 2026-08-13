# Corporate Network

> Enterprise Network Design & Implementation using Cisco Technologies

![Cisco](https://img.shields.io/badge/Cisco-Enterprise%20Networking-blue)
![OSPF](https://img.shields.io/badge/Routing-OSPF-orange)
![HSRP](https://img.shields.io/badge/Redundancy-HSRP-green)
![EtherChannel](https://img.shields.io/badge/Link%20Aggregation-LACP-purple)
![Rapid PVST+](https://img.shields.io/badge/STP-Rapid%20PVST%2B-blue)
![Security](https://img.shields.io/badge/Security-ASA%20%7C%20ACL-red)
![Platform](https://img.shields.io/badge/Platform-Cisco%20Packet%20Tracer-lightgrey)


---

### Network Topology

<img width="1537" height="1024" alt="Corporate_Network_Topology_Layers" src="https://github.com/user-attachments/assets/9e85b9a7-2f4b-43c9-adee-7f66512d1d29" />

<img width="1250" height="775" alt="Corporate_Network_Topology" src="https://github.com/user-attachments/assets/daea1252-d40c-4cac-9420-7599643d6f0b" />







---

## 📌 Project Overview

**Corporate Network** is an enterprise network design and implementation project built with Cisco technologies.

The network uses a hierarchical architecture with redundant Edge, Core, Distribution and Access layers. The design focuses on **high availability, network segmentation, dynamic routing, security and centralized network services**.

The project was developed in **Cisco Packet Tracer** as a practical networking portfolio project.

---

## 🏗️ Network Architecture

The infrastructure is organized into the following layers:

* **Edge Layer** – redundant Internet connectivity and edge routing
* **Firewall Layer** – Cisco ASA security perimeter
* **Core Layer** – redundant Layer 3 switching and high-speed routing
* **Distribution Layer** – Layer 3 aggregation and gateway redundancy
* **Access Layer** – endpoint, voice and wireless connectivity
* **Server Farm** – centralized infrastructure and network services

---

## 🔄 High Availability

Redundancy is implemented across multiple layers of the network to reduce single points of failure.

| Area            | Implementation                  |
| --------------- | ------------------------------- |
| Internet Edge   | Dual Edge Routers               |
| Firewall        | Redundant ASA Firewalls         |
| Core            | Dual Layer 3 Core Switches      |
| Distribution    | Redundant Distribution Switches |
| Default Gateway | HSRP                            |
| Routing         | OSPF                            |
| Uplinks         | EtherChannel / LACP             |
| Layer 2         | Rapid PVST+                     |

---

## 🌐 Routing

The network uses **OSPF Area 0** as the primary interior gateway protocol.

The design uses dedicated loopback interfaces as stable OSPF router IDs and routed point-to-point links between the Layer 3 infrastructure.

### Routing Features

* OSPF Area 0
* Loopback-based Router IDs
* Routed point-to-point links
* Passive interfaces where appropriate
* Dynamic route propagation
* Default route advertisement from the edge

---

## 🔀 Switching & Layer 2

The switching infrastructure uses VLAN segmentation and redundant Layer 2 paths.

### Implemented Technologies

* VLANs
* 802.1Q trunking
* Native VLAN 777
* Explicit trunk VLAN allow-lists
* Rapid PVST+
* EtherChannel
* LACP
* PortFast
* BPDU Guard
* DHCP Snooping
* Dynamic ARP Inspection

The configuration uses explicit VLAN allow-lists on trunks rather than permitting every VLAN, reducing unnecessary Layer 2 exposure.

---

## 🧩 VLAN Architecture

| VLAN | Name            | Subnet       | Purpose                   |
| ---: | --------------- | ------------ | ------------------------- |
|   10 | Management_A    | 10.1.0.0/28  | Network Management        |
|   11 | Management_B    | 10.1.0.16/26 | Infrastructure Management |
|   12 | MGT-Data_Farm   | 10.0.1.0/24  | Server Management         |
|   20 | Data_Farm       | 10.2.0.0/24  | Server Infrastructure     |
|   30 | Department_A    | 10.3.0.0/24  | Department A              |
|   40 | Department_B    | 10.4.0.0/24  | Department B              |
|   50 | Voice_A         | 10.5.0.0/24  | Department A Voice        |
|   60 | Voice_B         | 10.6.0.0/24  | Department B Voice        |
|   70 | Corporate_Wi-Fi | 10.7.0.0/24  | Corporate Wireless        |
|   80 | Guest_Wi-Fi     | 10.8.0.0/24  | Guest Wireless            |
|  777 | Native_Vlan     | N/A          | Native VLAN / Trunks      |

---

## 🔐 Security

The network incorporates security mechanisms at both the infrastructure and perimeter levels.

### Firewall

Cisco ASA firewalls provide the security boundary between the internal network and external networks.

### Access Control

* ACL-based traffic filtering
* Management access restrictions
* Dedicated management networks
* Segmented server infrastructure

### Secure Management

Network devices use:

* SSH Version 2
* Local authentication
* Restricted VTY access
* Telnet disabled

### Layer 2 Security

Access switches implement:

* Port Security
* PortFast
* BPDU Guard
* DHCP Snooping
* Dynamic ARP Inspection

---

## 🖥️ Server Infrastructure

The dedicated Server Farm provides centralized network services.

### Services

* Active Directory
* DNS
* DHCP
* Syslog
* SNMP
* NTP
* AAA / RADIUS
* File Server
* Wireless LAN Controller

The Server Farm is separated from the user access networks using dedicated VLANs and Layer 3 connectivity.

---

## 📡 Wireless

The network supports separate wireless environments:

### Corporate Wi-Fi

**VLAN 70 – 10.7.0.0/24**

Used for internal corporate wireless access.

### Guest Wi-Fi

**VLAN 80 – 10.8.0.0/24**

Dedicated network segment for guest wireless clients.

Wireless infrastructure is centrally managed through a **Wireless LAN Controller (WLC)**.

---

## 📊 Network Management & Monitoring

Centralized management services are provided through the Server Farm.

| Service      | Purpose                      |
| ------------ | ---------------------------- |
| SSH          | Secure device administration |
| SNMP         | Network monitoring           |
| Syslog       | Centralized event logging    |
| NTP          | Time synchronization         |
| DNS          | Name resolution              |
| DHCP         | Dynamic IP addressing        |
| AAA / RADIUS | Centralized authentication   |

---

## 🗂️ Repository Structure

```text
Corporate_Network/
│
├── README.md
│
├── configurations/
│   ├── EDGE/
│   ├── FIREWALL/
│   ├── CORE/
│   ├── DISTRIBUTION/
│   ├── ACCESS/
│   └── SERVER_FARM/
│
├── documentation/
│   ├── 01_Network_Overview.md
│   ├── diagrams/
│       ├── 02_Logical_Network_Diagram.md
│       ├── 03_IP_Addressing_Diagram.md
│
└── screenshots/
```

---

## 🧪 Validation

The network design can be validated through the following tests:

### Routing

* OSPF neighbor relationships
* OSPF route propagation
* Default route propagation
* Routing table verification

### High Availability

* HSRP gateway failover
* EtherChannel operation
* Redundant path verification
* STP convergence

### Network Services

* DHCP address assignment
* DNS resolution
* NTP synchronization
* Syslog delivery
* SNMP connectivity

### Security

* ACL verification
* SSH access
* VLAN isolation
* Guest network segmentation
* Layer 2 security verification

---

## 📁 Configuration Documentation

The repository contains the device configurations used to implement the network.

Configuration files are organized by network layer to make the project easier to understand, troubleshoot and maintain.

---

## 🎯 Design Goals

The project was designed around five main principles:

**Availability**
Redundant devices and paths reduce the impact of individual failures.

**Segmentation**
VLANs separate users, voice, wireless, management and server traffic.

**Scalability**
The hierarchical architecture allows additional departments, users and services to be added without redesigning the entire network.

**Security**
Firewall policies, ACLs, secure management and Layer 2 security controls provide multiple levels of protection.

**Manageability**
Centralized DHCP, DNS, Syslog, SNMP, NTP and AAA services simplify network administration.

---

## 🛠️ Skills Demonstrated

* Enterprise Network Architecture
* Cisco IOS
* Cisco ASA
* Layer 2 Switching
* Layer 3 Switching
* OSPF
* HSRP
* EtherChannel / LACP
* Rapid PVST+
* VLAN Design
* Inter-VLAN Routing
* ACLs
* Network Security
* DHCP Relay
* SSH
* SNMP
* Syslog
* NTP
* Network Documentation
* Network Troubleshooting

---

## 🚀 Future Improvements

Potential future enhancements include:

* Cisco ISE integration
* Network automation with Ansible
* Centralized monitoring with Zabbix
* NetFlow / traffic analysis
* Infrastructure-as-Code
* Automated configuration backup
* Network configuration compliance

---

## 📚 Documentation

Additional technical documentation is available in the `documentation/` directory.

* [Network Overview](documentation/01_Network_Overview.md)
* [Logical Diagram](documentation/02_Logical_Network_Diagram.md)
* [IP Addressing](documentation/03_IP_Addresing_Diagram.md)

---

## 👤 Author

**Vlady-J**

Cisco Networking Portfolio Project


