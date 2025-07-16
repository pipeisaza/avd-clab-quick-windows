# leaf2 Commands Output

## Table of Contents

- [show lldp neighbors](#show-lldp-neighbors)
- [show ip interface brief](#show-ip-interface-brief)
- [show interfaces description](#show-interfaces-description)
- [show version](#show-version)
- [show running-config](#show-running-config)
- [show ip bgp summary](#show-ip-bgp-summary)
- [show bgp evpn summary](#show-bgp-evpn-summary)
## show bgp evpn summary

```
BGP summary information for VRF default
Router identifier 192.0.255.130, local AS number 65102
Neighbor Status Codes: m - Under maintenance
  Description              Neighbor    V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc PfxAdv
  spine1                   192.0.255.1 4 65001             29        29    0    0 00:19:03 Estab   4      4      4
  spine2                   192.0.255.2 4 65001             29        32    0    0 00:19:02 Estab   4      4      8
```
## show interfaces description

```
Interface                      Status         Protocol           Description
Et49/1                         up             up                 P2P_LINK_TO_SPINE1_Ethernet2/1
Et50/1                         up             up                 P2P_LINK_TO_SPINE2_Ethernet2/1
Lo0                            up             up                 EVPN_Overlay_Peering
Lo1                            up             up                 VTEP_VXLAN_Tunnel_Source
Lo100                          up             up                 TEST_VRF_VTEP_DIAGNOSTICS
Ma0                            up             up                 oob_management
Po11                           down           lowerlayerdown     host11_leaf1_to_host11
Po12                           down           lowerlayerdown     host12_leaf3_to_host12
Vl100                          up             up                 TENANT_A_BGP_TO_COMPUTE
Vl4097                         up             up                 
Vx1                            up             up                 leaf2_VTEP
```
## show ip bgp summary

```
BGP summary information for VRF default
Router identifier 192.0.255.130, local AS number 65102
Neighbor Status Codes: m - Under maintenance
  Description              Neighbor      V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc PfxAdv
  spine1_Ethernet2/1       172.31.255.64 4 65001             28        28    0    0 00:19:02 Estab   3      3      3
  spine2_Ethernet2/1       172.31.255.66 4 65001             28        29    0    0 00:19:02 Estab   3      3      5
```
## show ip interface brief

```
Address
Interface       IP Address            Status     Protocol         MTU   Owner  
--------------- --------------------- ---------- ------------ --------- -------
Ethernet49/1    172.31.255.65/31      up         up              1500          
Ethernet50/1    172.31.255.67/31      up         up              1500          
Loopback0       192.0.255.130/32      up         up             65535          
Loopback1       192.0.254.2/32        up         up             65535          
Loopback100     10.255.1.2/32         up         up             65535          
Management0     192.168.123.22/24     up         up              1500          
Vlan100         10.100.100.1/24       up         up              1500          
Vlan4097        unassigned            up         up              9164
```
## show lldp neighbors

```
Last table change time   : 0:19:06 ago
Number of table inserts  : 5
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port            Neighbor Device ID       Neighbor Port ID    TTL
------------ ------------------------ ---------------------- ---
Et49/1          spine1.lab.net           Ethernet2/1         120
Et50/1          spine2.lab.net           Ethernet2/1         120
Ma0             spine2.lab.net           Management0         120
Ma0             spine1.lab.net           Management0         120
Ma0             leaf1.lab.net            Management0         120
```
## show running-config

```
! Command: show running-config
! device: leaf2 (cEOSLab, EOS-4.34.1F-41910311.orinocorel (engineering build))
!
no aaa root
!
username cvpadmin privilege 15 role network-admin secret sha512 $6$aQjjIocu2Pxl0baz$.3hUsqFqET6CHtNoc2nKIrmwPY39NYBaG.l2dX1hmiUc46lWorrG7V25b5XeqwSCJnRs4pOe9teK1/5RK8mve/
!
management api http-commands
   no shutdown
   !
   vrf MGMT
      no shutdown
!
daemon TerminAttr
   exec /usr/bin/TerminAttr -cvaddr=192.168.122.241:9910 -cvauth=key,qwerty -cvvrf=MGMT -smashexcludes=ale,flexCounter,hardware,kni,pulse,strata -ingestexclude=/Sysdb/cell/1/agent,/Sysdb/cell/2/agent -taillogs
   no shutdown
!
vlan internal order ascending range 1006 1199
!
no service interface inactive port-id allocation disabled
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model multi-agent
!
hostname leaf2
ip name-server vrf MGMT 8.8.8.8
dns domain lab.net
!
spanning-tree mode mstp
spanning-tree mst 0 priority 4096
!
system l1
   unsupported speed action error
   unsupported error-correction action error
!
vlan 100
   name TENANT_A_BGP_TO_COMPUTE
!
vlan 200
   name TENANT_A_TEST_L2_ONLY_VLAN
!
vrf instance MGMT
!
vrf instance TEST_VRF
!
management security
   password encryption-key common
!
interface Port-Channel11
   description host11_leaf1_to_host11
   switchport access vlan 200
   !
   evpn ethernet-segment
      identifier 0000:0000:d804:eca6:ffc4
      route-target import d8:04:ec:a6:ff:c4
   lacp system-id d804.eca6.ffc4
!
interface Port-Channel12
   description host12_leaf3_to_host12
   switchport trunk allowed vlan 100-150,200
   switchport mode trunk
   !
   evpn ethernet-segment
      identifier 0000:0000:1509:401c:dd4a
      route-target import 15:09:40:1c:dd:4a
   lacp system-id 1509.401c.dd4a
!
interface Ethernet1/1
   description host11_leaf2_Ethernet1/1
   channel-group 11 mode active
!
interface Ethernet1/2
   description host12_leaf2_Ethernet1/2
   channel-group 12 mode active
!
interface Ethernet49/1
   description P2P_LINK_TO_SPINE1_Ethernet2/1
   mtu 1500
   no switchport
   ip address 172.31.255.65/31
!
interface Ethernet50/1
   description P2P_LINK_TO_SPINE2_Ethernet2/1
   mtu 1500
   no switchport
   ip address 172.31.255.67/31
!
interface Loopback0
   description EVPN_Overlay_Peering
   ip address 192.0.255.130/32
!
interface Loopback1
   description VTEP_VXLAN_Tunnel_Source
   ip address 192.0.254.2/32
!
interface Loopback100
   description TEST_VRF_VTEP_DIAGNOSTICS
   vrf TEST_VRF
   ip address 10.255.1.2/32
!
interface Management0
   description oob_management
   vrf MGMT
   ip address 192.168.123.22/24
!
interface Vlan100
   description TENANT_A_BGP_TO_COMPUTE
   vrf TEST_VRF
   ip address virtual 10.100.100.1/24
!
interface Vxlan1
   description leaf2_VTEP
   vxlan source-interface Loopback1
   vxlan udp-port 4789
   vxlan vlan 100 vni 10100
   vxlan vlan 200 vni 10200
   vxlan vrf TEST_VRF vni 10
!
ip virtual-router mac-address 00:1c:73:00:dc:01
ip address virtual source-nat vrf TEST_VRF address 10.255.1.2
!
ip routing
no ip routing vrf MGMT
ip routing vrf TEST_VRF
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 192.0.255.128/25 eq 32
   seq 20 permit 192.0.254.0/24 eq 32
!
ip route vrf MGMT 0.0.0.0/0 192.168.123.1
!
ntp local-interface vrf MGMT Management0
ntp server vrf MGMT time1.google.com
ntp server vrf MGMT time2.google.com
ntp server vrf MGMT time3.google.com
!
route-map RM-CONN-2-BGP permit 10
   match ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY
!
router bfd
   multihop interval 300 min-rx 300 multiplier 3
!
router bgp 65102
   router-id 192.0.255.130
   maximum-paths 4 ecmp 4
   neighbor EVPN-OVERLAY-PEERS peer group
   neighbor EVPN-OVERLAY-PEERS update-source Loopback0
   neighbor EVPN-OVERLAY-PEERS bfd
   neighbor EVPN-OVERLAY-PEERS ebgp-multihop 3
   neighbor EVPN-OVERLAY-PEERS password 7 $1c$caHDPKDBzOjl6ZrDQLicDQ==
   neighbor EVPN-OVERLAY-PEERS send-community
   neighbor EVPN-OVERLAY-PEERS maximum-routes 0
   neighbor IPv4-UNDERLAY-PEERS peer group
   neighbor IPv4-UNDERLAY-PEERS password 7 $1c$caHDPKDBzOjl6ZrDQLicDQ==
   neighbor IPv4-UNDERLAY-PEERS send-community
   neighbor IPv4-UNDERLAY-PEERS maximum-routes 12000
   neighbor 172.31.255.64 peer group IPv4-UNDERLAY-PEERS
   neighbor 172.31.255.64 remote-as 65001
   neighbor 172.31.255.64 description spine1_Ethernet2/1
   neighbor 172.31.255.66 peer group IPv4-UNDERLAY-PEERS
   neighbor 172.31.255.66 remote-as 65001
   neighbor 172.31.255.66 description spine2_Ethernet2/1
   neighbor 192.0.255.1 peer group EVPN-OVERLAY-PEERS
   neighbor 192.0.255.1 remote-as 65001
   neighbor 192.0.255.1 description spine1
   neighbor 192.0.255.2 peer group EVPN-OVERLAY-PEERS
   neighbor 192.0.255.2 remote-as 65001
   neighbor 192.0.255.2 description spine2
   redistribute connected route-map RM-CONN-2-BGP
   !
   vlan 100
      rd 192.0.255.130:10100
      route-target both 10100:10100
      redistribute learned
   !
   vlan 200
      rd 192.0.255.130:10200
      route-target both 10200:10200
      redistribute learned
   !
   address-family evpn
      neighbor EVPN-OVERLAY-PEERS activate
   !
   address-family ipv4
      no neighbor EVPN-OVERLAY-PEERS activate
      neighbor IPv4-UNDERLAY-PEERS activate
   !
   vrf TEST_VRF
      rd 192.0.255.130:10
      route-target import evpn 10:10
      route-target export evpn 10:10
      router-id 192.0.255.130
      redistribute connected
!
router multicast
   ipv4
      software-forwarding kernel
   !
   ipv6
      software-forwarding kernel
!
end
```
## show version

```
Arista cEOSLab
Hardware version: 
Serial number: 55DAE829E0CE19FA7F07E09F87E125C3
Hardware MAC address: 001c.739c.2722
System MAC address: 001c.739c.2722

Software image version: 4.34.1F-41910311.orinocorel (engineering build)
Architecture: x86_64
Internal build version: 4.34.1F-41910311.orinocorel
Internal build ID: 375a0395-b269-4d4c-b708-8d7617e4924b
Image format version: 1.0
Image optimization: None

Kernel version: 6.6.87.2-microsoft-standard-WSL2

Uptime: 28 minutes
Total memory: 8064240 kB
Free memory: 1346948 kB
```
