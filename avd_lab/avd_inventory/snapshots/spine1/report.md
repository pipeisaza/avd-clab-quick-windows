# spine1 Commands Output

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
Router identifier 192.0.255.1, local AS number 65001
Neighbor Status Codes: m - Under maintenance
  Description              Neighbor      V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc PfxAdv
  leaf1                    192.0.255.129 4 65101             32        30    0    0 00:19:01 Estab   4      4      4
  leaf2                    192.0.255.130 4 65102             29        29    0    0 00:19:03 Estab   4      4      4
```
## show interfaces description

```
Interface                      Status         Protocol           Description
Et1/1                          up             up                 P2P_LINK_TO_LEAF1_Ethernet49/1
Et2/1                          up             up                 P2P_LINK_TO_LEAF2_Ethernet49/1
Lo0                            up             up                 EVPN_Overlay_Peering
Ma0                            up             up                 oob_management
```
## show ip bgp summary

```
BGP summary information for VRF default
Router identifier 192.0.255.1, local AS number 65001
Neighbor Status Codes: m - Under maintenance
  Description              Neighbor      V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc PfxAdv
  leaf1_Ethernet49/1       172.31.255.1  4 65101             29        29    0    0 00:19:00 Estab   2      2      3
  leaf2_Ethernet49/1       172.31.255.65 4 65102             28        28    0    0 00:19:01 Estab   2      2      3
```
## show ip interface brief

```
Address
Interface       IP Address            Status     Protocol         MTU   Owner  
--------------- --------------------- ---------- ------------ --------- -------
Ethernet1/1     172.31.255.0/31       up         up              1500          
Ethernet2/1     172.31.255.64/31      up         up              1500          
Loopback0       192.0.255.1/32        up         up             65535          
Management0     192.168.123.11/24     up         up              1500
```
## show lldp neighbors

```
Last table change time   : 0:19:06 ago
Number of table inserts  : 5
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port           Neighbor Device ID       Neighbor Port ID    TTL
----------- ------------------------ ---------------------- ---
Et1/1          leaf1.lab.net            Ethernet49/1        120
Et2/1          leaf2.lab.net            Ethernet49/1        120
Ma0            leaf2.lab.net            Management0         120
Ma0            spine2.lab.net           Management0         120
Ma0            leaf1.lab.net            Management0         120
```
## show running-config

```
! Command: show running-config
! device: spine1 (cEOSLab, EOS-4.34.1F-41910311.orinocorel (engineering build))
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
hostname spine1
ip name-server vrf MGMT 8.8.8.8
dns domain lab.net
!
spanning-tree mode none
!
system l1
   unsupported speed action error
   unsupported error-correction action error
!
vrf instance MGMT
!
management security
   password encryption-key common
!
interface Ethernet1/1
   description P2P_LINK_TO_LEAF1_Ethernet49/1
   mtu 1500
   no switchport
   ip address 172.31.255.0/31
!
interface Ethernet2/1
   description P2P_LINK_TO_LEAF2_Ethernet49/1
   mtu 1500
   no switchport
   ip address 172.31.255.64/31
!
interface Loopback0
   description EVPN_Overlay_Peering
   ip address 192.0.255.1/32
!
interface Management0
   description oob_management
   vrf MGMT
   ip address 192.168.123.11/24
!
ip routing
no ip routing vrf MGMT
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 192.0.255.0/25 eq 32
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
router bgp 65001
   router-id 192.0.255.1
   maximum-paths 4 ecmp 4
   neighbor EVPN-OVERLAY-PEERS peer group
   neighbor EVPN-OVERLAY-PEERS next-hop-unchanged
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
   neighbor 172.31.255.1 peer group IPv4-UNDERLAY-PEERS
   neighbor 172.31.255.1 remote-as 65101
   neighbor 172.31.255.1 description leaf1_Ethernet49/1
   neighbor 172.31.255.65 peer group IPv4-UNDERLAY-PEERS
   neighbor 172.31.255.65 remote-as 65102
   neighbor 172.31.255.65 description leaf2_Ethernet49/1
   neighbor 192.0.255.129 peer group EVPN-OVERLAY-PEERS
   neighbor 192.0.255.129 remote-as 65101
   neighbor 192.0.255.129 description leaf1
   neighbor 192.0.255.130 peer group EVPN-OVERLAY-PEERS
   neighbor 192.0.255.130 remote-as 65102
   neighbor 192.0.255.130 description leaf2
   redistribute connected route-map RM-CONN-2-BGP
   !
   address-family evpn
      neighbor EVPN-OVERLAY-PEERS activate
   !
   address-family ipv4
      no neighbor EVPN-OVERLAY-PEERS activate
      neighbor IPv4-UNDERLAY-PEERS activate
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
Serial number: D71FFF3306E0CA35D95BE540DAD29DA4
Hardware MAC address: 001c.73d6.e19b
System MAC address: 001c.73d6.e19b

Software image version: 4.34.1F-41910311.orinocorel (engineering build)
Architecture: x86_64
Internal build version: 4.34.1F-41910311.orinocorel
Internal build ID: 375a0395-b269-4d4c-b708-8d7617e4924b
Image format version: 1.0
Image optimization: None

Kernel version: 6.6.87.2-microsoft-standard-WSL2

Uptime: 28 minutes
Total memory: 8064240 kB
Free memory: 1337244 kB
```
