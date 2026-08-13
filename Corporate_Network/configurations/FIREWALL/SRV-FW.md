hostname SRV-FW
domain-name Vladi-J.com
enable password GqovsYuMF1C7A3Hx encrypted
names
!
interface GigabitEthernet1/1
 description Inside Link to SF_SW
 nameif inside-0/1
 security-level 100
 ip address 10.0.3.9 255.255.255.252
!
interface GigabitEthernet1/2
 description Link to CORE_SW01
 nameif outside-0/2
 security-level 50
 ip address 10.0.3.6 255.255.255.252
!
interface GigabitEthernet1/3
 description Unused Interface (    shutdown    )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/4
 description Unused Interface (    shutdown    )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/5
 description Unused Interface (    shutdown    )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/6
 description Link to CORE_SW01
 nameif outside-0/1
 security-level 50
 ip address 10.0.3.2 255.255.255.252
!
interface GigabitEthernet1/7
 description Unused Interface (    shutdown    )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/8
 description Unused Interface (    shutdown    )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface Management1/1
 description Management Interface (    shutdown    )
 management-only
 no nameif
 no security-level
 no ip address
 shutdown
!
!
route inside-0/1 10.2.0.0 255.255.255.240 10.0.3.10 1
!
access-list FW_IN_PERMIT extended permit icmp any any echo-reply
access-list FW_IN_PERMIT extended permit icmp any any echo
access-list FW_IN_PERMIT extended permit udp any host 10.2.0.11 eq bootps
access-list FW_IN_PERMIT extended permit udp any host 10.2.0.10 eq bootps
access-list FW_IN_PERMIT extended permit udp any host 10.2.0.10 eq domain
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.255.255.0 host 10.2.0.10 eq 123
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.255.255.0 host 10.2.0.10 eq 514
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.255.255.0 host 10.2.0.10 eq 162
access-list FW_IN_PERMIT extended permit tcp 10.3.0.0 255.255.0.0 host 10.2.0.10 eq 1645
access-list FW_IN_PERMIT extended permit udp 10.1.0.0 255.255.255.0 host 10.0.1.100 eq 5246
access-list FW_IN_PERMIT extended permit udp 10.1.0.0 255.255.255.0 host 10.0.1.100 eq 5247
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.0.0.0 host 10.2.0.12 eq 1812
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.0.0.0 host 10.2.0.12 eq 1813
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.0.0.0 any eq 123
access-list FW_IN_PERMIT extended permit tcp 10.0.0.0 255.0.0.0 any eq 22
access-list FW_IN_PERMIT extended permit tcp 10.0.0.0 255.0.0.0 host 10.2.0.11 eq 20
access-list FW_IN_PERMIT extended permit tcp 10.0.0.0 255.0.0.0 host 10.2.0.11 eq ftp
access-list FW_IN_PERMIT extended permit udp 10.0.0.0 255.0.0.0 host 10.2.0.11 eq tftp
!
!
access-group FW_IN_PERMIT in interface outside-0/1
access-group FW_IN_PERMIT in interface outside-0/2
!
username vladi-j password GqovsYuMF1C7A3Hx encrypted
!
class-map inspection_default
 match default-inspection-traffic
!
policy-map type inspect dns preset_dns_map
 parameters
  message-length maximum 512
policy-map global_policy
 class inspection_default
  inspect dns preset_dns_map
  inspect ftp 
  inspect tftp 
!
service-policy global_policy global
!
telnet timeout 5
ssh timeout 5
!
!
!
!
router ospf 1
 log-adjacency-changes
 network 0.0.0.0 0.0.0.0 area 0
 network 0.0.0.0 255.255.255.255 area 0
