
# Validate State Report

**Table of Contents:**

- [Validate State Report](validate-state-report)
  - [Test Results Summary](#test-results-summary)
  - [Failed Test Results Summary](#failed-test-results-summary)
  - [All Test Results](#all-test-results)

## Test Results Summary

### Summary Totals

| Total Tests | Total Tests Passed | Total Tests Failed |
| ----------- | ------------------ | ------------------ |
| 88 | 77 | 11 |

### Summary Totals Devices Under Tests

| DUT | Total Tests | Tests Passed | Tests Failed | Categories Failed |
| --- | ----------- | ------------ | ------------ | ----------------- |
| leaf1 |  31 | 26 | 5 | NTP, Interface State |
| leaf2 |  31 | 26 | 5 | NTP, Interface State |
| spine1 |  13 | 12 | 1 | NTP |
| spine2 |  13 | 13 | 0 | - |

### Summary Totals Per Category

| Test Category | Total Tests | Tests Passed | Tests Failed |
| ------------- | ----------- | ------------ | ------------ |
| NTP |  4 | 1 | 3 |
| Interface State |  28 | 20 | 8 |
| LLDP Topology |  8 | 8 | 0 |
| IP Reachability |  8 | 8 | 0 |
| BGP |  20 | 20 | 0 |
| Routing Table |  12 | 12 | 0 |
| Loopback0 Reachability |  8 | 8 | 0 |

## Failed Test Results Summary

| Test ID | Node | Test Category | Test Description | Test | Test Result | Failure Reason |
| ------- | ---- | ------------- | ---------------- | ---- | ----------- | -------------- |
| 1 | leaf1 | NTP | Synchronised with NTP server | NTP | FAIL | Not synchronised to NTP server |
| 2 | leaf2 | NTP | Synchronised with NTP server | NTP | FAIL | Not synchronised to NTP server |
| 3 | spine1 | NTP | Synchronised with NTP server | NTP | FAIL | Not synchronised to NTP server |
| 7 | leaf1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/1 - host11_leaf1_Ethernet1/1 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 8 | leaf1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/2 - host12_leaf1_Ethernet1/2 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 11 | leaf2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/1 - host11_leaf2_Ethernet1/1 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 12 | leaf2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/2 - host12_leaf2_Ethernet1/2 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 17 | leaf1 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel11 - host11_leaf1_to_host11 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 18 | leaf1 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel12 - host12_leaf3_to_host12 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 19 | leaf2 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel11 - host11_leaf1_to_host11 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 20 | leaf2 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel12 - host12_leaf3_to_host12 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |

## All Test Results

| Test ID | Node | Test Category | Test Description | Test | Test Result | Failure Reason |
| ------- | ---- | ------------- | ---------------- | ---- | ----------- | -------------- |
| 1 | leaf1 | NTP | Synchronised with NTP server | NTP | FAIL | Not synchronised to NTP server |
| 2 | leaf2 | NTP | Synchronised with NTP server | NTP | FAIL | Not synchronised to NTP server |
| 3 | spine1 | NTP | Synchronised with NTP server | NTP | FAIL | Not synchronised to NTP server |
| 4 | spine2 | NTP | Synchronised with NTP server | NTP | PASS | - |
| 5 | leaf1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet49/1 - P2P_LINK_TO_SPINE1_Ethernet1/1 | PASS | - |
| 6 | leaf1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet50/1 - P2P_LINK_TO_SPINE2_Ethernet1/1 | PASS | - |
| 7 | leaf1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/1 - host11_leaf1_Ethernet1/1 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 8 | leaf1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/2 - host12_leaf1_Ethernet1/2 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 9 | leaf2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet49/1 - P2P_LINK_TO_SPINE1_Ethernet2/1 | PASS | - |
| 10 | leaf2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet50/1 - P2P_LINK_TO_SPINE2_Ethernet2/1 | PASS | - |
| 11 | leaf2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/1 - host11_leaf2_Ethernet1/1 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 12 | leaf2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/2 - host12_leaf2_Ethernet1/2 | FAIL | Interface shutdown: False - interface status: Not present - line protocol status: Not present |
| 13 | spine1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/1 - P2P_LINK_TO_LEAF1_Ethernet49/1 | PASS | - |
| 14 | spine1 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet2/1 - P2P_LINK_TO_LEAF2_Ethernet49/1 | PASS | - |
| 15 | spine2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet1/1 - P2P_LINK_TO_LEAF1_Ethernet50/1 | PASS | - |
| 16 | spine2 | Interface State | Ethernet Interface & Line Protocol == "up" | Ethernet2/1 - P2P_LINK_TO_LEAF2_Ethernet50/1 | PASS | - |
| 17 | leaf1 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel11 - host11_leaf1_to_host11 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 18 | leaf1 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel12 - host12_leaf3_to_host12 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 19 | leaf2 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel11 - host11_leaf1_to_host11 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 20 | leaf2 | Interface State | Port-Channel Interface & Line Protocol == "up" | Port-Channel12 - host12_leaf3_to_host12 | FAIL | Interface shutdown: False - interface status: down - line protocol status: lowerLayerDown |
| 21 | leaf1 | Interface State | Vlan Interface & Line Protocol == "up" | Vlan100 - TENANT_A_BGP_TO_COMPUTE | PASS | - |
| 22 | leaf2 | Interface State | Vlan Interface & Line Protocol == "up" | Vlan100 - TENANT_A_BGP_TO_COMPUTE | PASS | - |
| 23 | leaf1 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | PASS | - |
| 24 | leaf2 | Interface State | Vxlan Interface Status & Line Protocol == "up" | Vxlan1 | PASS | - |
| 25 | leaf1 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 26 | leaf1 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback1 - VTEP_VXLAN_Tunnel_Source | PASS | - |
| 27 | leaf1 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback100 - TEST_VRF_VTEP_DIAGNOSTICS | PASS | - |
| 28 | leaf2 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 29 | leaf2 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback1 - VTEP_VXLAN_Tunnel_Source | PASS | - |
| 30 | leaf2 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback100 - TEST_VRF_VTEP_DIAGNOSTICS | PASS | - |
| 31 | spine1 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 32 | spine2 | Interface State | Loopback Interface Status & Line Protocol == "up" | Loopback0 - EVPN_Overlay_Peering | PASS | - |
| 33 | leaf1 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet49/1 - remote: spine1_Ethernet1/1 | PASS | - |
| 34 | leaf1 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet50/1 - remote: spine2_Ethernet1/1 | PASS | - |
| 35 | leaf2 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet49/1 - remote: spine1_Ethernet2/1 | PASS | - |
| 36 | leaf2 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet50/1 - remote: spine2_Ethernet2/1 | PASS | - |
| 37 | spine1 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1/1 - remote: leaf1_Ethernet49/1 | PASS | - |
| 38 | spine1 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet2/1 - remote: leaf2_Ethernet49/1 | PASS | - |
| 39 | spine2 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet1/1 - remote: leaf1_Ethernet50/1 | PASS | - |
| 40 | spine2 | LLDP Topology | LLDP topology - validate peer and interface | local: Ethernet2/1 - remote: leaf2_Ethernet50/1 | PASS | - |
| 41 | leaf1 | IP Reachability | ip reachability test p2p links | Source: leaf1_Ethernet49/1 - Destination: spine1_Ethernet1/1 | PASS | - |
| 42 | leaf1 | IP Reachability | ip reachability test p2p links | Source: leaf1_Ethernet50/1 - Destination: spine2_Ethernet1/1 | PASS | - |
| 43 | leaf2 | IP Reachability | ip reachability test p2p links | Source: leaf2_Ethernet49/1 - Destination: spine1_Ethernet2/1 | PASS | - |
| 44 | leaf2 | IP Reachability | ip reachability test p2p links | Source: leaf2_Ethernet50/1 - Destination: spine2_Ethernet2/1 | PASS | - |
| 45 | spine1 | IP Reachability | ip reachability test p2p links | Source: spine1_Ethernet1/1 - Destination: leaf1_Ethernet49/1 | PASS | - |
| 46 | spine1 | IP Reachability | ip reachability test p2p links | Source: spine1_Ethernet2/1 - Destination: leaf2_Ethernet49/1 | PASS | - |
| 47 | spine2 | IP Reachability | ip reachability test p2p links | Source: spine2_Ethernet1/1 - Destination: leaf1_Ethernet50/1 | PASS | - |
| 48 | spine2 | IP Reachability | ip reachability test p2p links | Source: spine2_Ethernet2/1 - Destination: leaf2_Ethernet50/1 | PASS | - |
| 49 | leaf1 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 50 | leaf2 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 51 | spine1 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 52 | spine2 | BGP | ArBGP is configured and operating | ArBGP | PASS | - |
| 53 | leaf1 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.0 | PASS | - |
| 54 | leaf1 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.2 | PASS | - |
| 55 | leaf2 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.64 | PASS | - |
| 56 | leaf2 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.66 | PASS | - |
| 57 | spine1 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.1 | PASS | - |
| 58 | spine1 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.65 | PASS | - |
| 59 | spine2 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.3 | PASS | - |
| 60 | spine2 | BGP | ip bgp peer state established (ipv4) | bgp_neighbor: 172.31.255.67 | PASS | - |
| 61 | leaf1 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.1 | PASS | - |
| 62 | leaf1 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.2 | PASS | - |
| 63 | leaf2 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.1 | PASS | - |
| 64 | leaf2 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.2 | PASS | - |
| 65 | spine1 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.129 | PASS | - |
| 66 | spine1 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.130 | PASS | - |
| 67 | spine2 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.129 | PASS | - |
| 68 | spine2 | BGP | bgp evpn peer state established (evpn) | bgp_neighbor: 192.0.255.130 | PASS | - |
| 69 | leaf1 | Routing Table | Remote VTEP address | 192.0.254.1 | PASS | - |
| 70 | leaf1 | Routing Table | Remote VTEP address | 192.0.254.2 | PASS | - |
| 71 | leaf2 | Routing Table | Remote VTEP address | 192.0.254.1 | PASS | - |
| 72 | leaf2 | Routing Table | Remote VTEP address | 192.0.254.2 | PASS | - |
| 73 | leaf1 | Routing Table | Remote Lo0 address | 192.0.255.129 | PASS | - |
| 74 | leaf1 | Routing Table | Remote Lo0 address | 192.0.255.130 | PASS | - |
| 75 | leaf1 | Routing Table | Remote Lo0 address | 192.0.255.1 | PASS | - |
| 76 | leaf1 | Routing Table | Remote Lo0 address | 192.0.255.2 | PASS | - |
| 77 | leaf2 | Routing Table | Remote Lo0 address | 192.0.255.129 | PASS | - |
| 78 | leaf2 | Routing Table | Remote Lo0 address | 192.0.255.130 | PASS | - |
| 79 | leaf2 | Routing Table | Remote Lo0 address | 192.0.255.1 | PASS | - |
| 80 | leaf2 | Routing Table | Remote Lo0 address | 192.0.255.2 | PASS | - |
| 81 | leaf1 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf1 - 192.0.255.129 Destination: 192.0.255.129 | PASS | - |
| 82 | leaf1 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf1 - 192.0.255.129 Destination: 192.0.255.130 | PASS | - |
| 83 | leaf1 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf1 - 192.0.255.129 Destination: 192.0.255.1 | PASS | - |
| 84 | leaf1 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf1 - 192.0.255.129 Destination: 192.0.255.2 | PASS | - |
| 85 | leaf2 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf2 - 192.0.255.130 Destination: 192.0.255.129 | PASS | - |
| 86 | leaf2 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf2 - 192.0.255.130 Destination: 192.0.255.130 | PASS | - |
| 87 | leaf2 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf2 - 192.0.255.130 Destination: 192.0.255.1 | PASS | - |
| 88 | leaf2 | Loopback0 Reachability | Loopback0 Reachability | Source: leaf2 - 192.0.255.130 Destination: 192.0.255.2 | PASS | - |
