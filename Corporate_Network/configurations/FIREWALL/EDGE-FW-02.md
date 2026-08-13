hostname EDGE-FW-02
domain-name Vladi-J.com
enable password GqovsYuMF1C7A3Hx encrypted
names
!
interface GigabitEthernet1/1
 description Unused Interface (      shutdown      )
 nameif outside-0/2
 security-level 0
 ip address 10.0.0.6 255.255.255.252
!
interface GigabitEthernet1/2
 description Inside Link to CORE-SW02 (      10.0.1.6/30      )
 nameif inside-0/2
 security-level 100
 ip address 10.0.1.9 255.255.255.252
!
interface GigabitEthernet1/3
 description Outside Link to EDGE-R1 (      10.0.0.6/30      )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/4
 description Inside Link to CORE-SW01 (      10.0.1.2/30      )
 nameif inside-0/1
 security-level 100
 ip address 10.0.1.13 255.255.255.252
!
interface GigabitEthernet1/5
 description Unused Interface (      shutdown      )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/6
 description Unused Interface (      shutdown      )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/7
 description Unused Interface (      shutdown      )
 no nameif
 no security-level
 no ip address
 shutdown
!
interface GigabitEthernet1/8
 description Outside Link to EDGE-R2 (      10.0.0.14/30      )
 nameif outside-0/1
 security-level 0
 ip address 10.0.0.14 255.255.255.252
!
interface Management1/1
 description Management Interface (      shutdown      )
 management-only
 no nameif
 no security-level
 no ip address
 shutdown
!
!
route outside-0/1 0.0.0.0 0.0.0.0 10.0.0.254 1
route outside-0/2 0.0.0.0 0.0.0.0 10.0.0.254 1
!
access-list FW_IN_PERMIT extended permit tcp any host 10.0.0.101 eq 2000
access-list FW_IN_PERMIT extended permit icmp any any echo-reply
access-list FW_IN_PERMIT extended permit icmp any any echo
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
  inspect icmp 
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
 router-id 10.0.0.114
 log-adjacency-changes
 network 0.0.0.0 0.0.0.0 area 0
 network 0.0.0.0 255.255.255.255 area 0
