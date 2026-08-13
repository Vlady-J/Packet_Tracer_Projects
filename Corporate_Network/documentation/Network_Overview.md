

<img width="1250" height="775" alt="Corporate_Network_Topology" src="https://github.com/user-attachments/assets/1f991a00-9218-4c36-859d-4531d0b47f28" />

<img width="1536" height="1024" alt="Corporate_Network_Topology_1" src="https://github.com/user-attachments/assets/848d79bd-ee32-49bd-a981-54a646ded6a9" />
1. Project Overview
Introduction

This project demonstrates the design and implementation of a modern enterprise corporate network based on Cisco technologies. The infrastructure follows a hierarchical architecture and incorporates redundancy, network segmentation, dynamic routing, and centralized network services.

The primary objective is to provide a secure, scalable, and highly available network capable of supporting business operations while following Cisco enterprise design recommendations.

2. Project Objectives
Design a scalable enterprise network
Implement a hierarchical network architecture
Provide high availability using redundant devices and links
Segment network traffic using VLANs
Deploy dynamic routing with OSPF
Implement secure remote management
Centralize network services
Demonstrate Cisco enterprise best practices
3. Network Architecture

The network follows the Cisco three-tier hierarchical model.

Edge Layer
Dual ISP connectivity
Two edge routers
Internet connectivity
WAN redundancy
Security Layer
Cisco ASA Firewalls
Network Address Translation (NAT)
Access Control Lists (ACL)
Security zone separation
Core Layer
Redundant Layer 3 Core Switches
High-speed interconnection
Dynamic routing
High-speed forwarding
Distribution Layer
Layer 3 Distribution Switches
Inter-VLAN routing
HSRP default gateways
Policy enforcement
Access Layer
User connectivity
Voice devices
Wireless Access Points
End-user devices
4. Key Technologies
Technology	Purpose
OSPF	Dynamic Routing
HSRP	Gateway Redundancy
EtherChannel (LACP)	Link Aggregation
Rapid PVST+	Layer 2 Loop Prevention
VLANs	Network Segmentation
ACLs	Traffic Filtering
DHCP Relay	Centralized IP Assignment
SSH	Secure Remote Management
SNMP	Network Monitoring
Syslog	Centralized Logging
NTP	Time Synchronization
5. High Availability

The network incorporates redundancy at multiple layers.

WAN
Dual Edge Routers
Multiple WAN paths
Core
Dual Core Switches
Dynamic routing using OSPF
Distribution
Dual Distribution Switches
HSRP virtual gateways
Layer 2
EtherChannel uplinks
Rapid PVST+

This design minimizes single points of failure and improves service availability.

6. Routing Design

The routing infrastructure is based on OSPF Area 0.

Features
Dynamic route advertisement
Loopback Router IDs
Fast convergence
Scalable routing architecture

The configurations indicate that OSPF uses explicit router IDs, passive loopback interfaces, and multiple routed links participating in Area 0.

7. Layer 2 Design

The switching infrastructure provides:

VLAN segmentation
802.1Q trunk links
Native VLAN 777
Restricted allowed VLAN lists
Rapid PVST+
EtherChannel uplinks

Example configuration snippets show Rapid PVST enabled, tuned STP priorities, trunk ports using native VLAN 777, and explicitly allowed VLANs rather than permitting all VLANs.

8. Security Design

The network implements multiple security mechanisms.

Management Security
SSH Version 2
Local user authentication
VTY access control
Secure management access
Monitoring
SNMP
Syslog
NTP authentication

The available configurations include SSH v2, local login for console and VTY access, SNMP, Syslog to a centralized server, and authenticated NTP.

9. Network Services

Centralized services include:

DNS
DHCP
Syslog
SNMP
NTP
SSH Management

These services simplify administration while providing centralized management and monitoring.

10. Enterprise Features

The project demonstrates practical implementation of:

Enterprise network hierarchy
Dynamic routing
High availability
VLAN segmentation
Secure device management
Centralized monitoring
Redundant uplinks
Routed infrastructure
Layer 2 optimization
11. Skills Demonstrated

This project demonstrates practical knowledge of:

Cisco IOS configuration
Enterprise network design
OSPF deployment
VLAN implementation
Inter-VLAN routing
HSRP
EtherChannel (LACP)
Rapid PVST+
Network security
Cisco ASA firewall integration
Enterprise documentation
12. Conclusion

The Corporate Network project showcases the design and implementation of a scalable enterprise network using Cisco technologies. The architecture emphasizes redundancy, modularity, security, and operational simplicity through the use of dynamic routing, VLAN segmentation, centralized management services, and resilient network design.

The resulting infrastructure provides a solid foundation that can be extended with technologies such as IPv6, 802.1X, Cisco ISE, SD-WAN, or network automation as future enhancements.
