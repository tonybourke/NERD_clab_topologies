# leaf48

## Table of Contents

- [Management](#management)
  - [Management Interfaces](#management-interfaces)
  - [DNS Domain](#dns-domain)
  - [IP Name Servers](#ip-name-servers)
  - [Management API HTTP](#management-api-http)
- [Authentication](#authentication)
  - [Local Users](#local-users)
  - [Enable Password](#enable-password)
  - [AAA Authentication](#aaa-authentication)
  - [AAA Authorization](#aaa-authorization)
- [MLAG](#mlag)
  - [MLAG Summary](#mlag-summary)
  - [MLAG Device Configuration](#mlag-device-configuration)
- [Spanning Tree](#spanning-tree)
  - [Spanning Tree Summary](#spanning-tree-summary)
  - [Spanning Tree Device Configuration](#spanning-tree-device-configuration)
- [Internal VLAN Allocation Policy](#internal-vlan-allocation-policy)
  - [Internal VLAN Allocation Policy Summary](#internal-vlan-allocation-policy-summary)
  - [Internal VLAN Allocation Policy Device Configuration](#internal-vlan-allocation-policy-device-configuration)
- [VLANs](#vlans)
  - [VLANs Summary](#vlans-summary)
  - [VLANs Device Configuration](#vlans-device-configuration)
- [Interfaces](#interfaces)
  - [Ethernet Interfaces](#ethernet-interfaces)
  - [Port-Channel Interfaces](#port-channel-interfaces)
  - [Loopback Interfaces](#loopback-interfaces)
  - [VLAN Interfaces](#vlan-interfaces)
  - [VXLAN Interface](#vxlan-interface)
- [Routing](#routing)
  - [Service Routing Protocols Model](#service-routing-protocols-model)
  - [Virtual Router MAC Address](#virtual-router-mac-address)
  - [IP Routing](#ip-routing)
  - [IPv6 Routing](#ipv6-routing)
  - [Static Routes](#static-routes)
  - [Router BGP](#router-bgp)
- [BFD](#bfd)
  - [Router BFD](#router-bfd)
- [Multicast](#multicast)
  - [IP IGMP Snooping](#ip-igmp-snooping)
- [Filters](#filters)
  - [Prefix-lists](#prefix-lists)
  - [Route-maps](#route-maps)
- [VRF Instances](#vrf-instances)
  - [VRF Instances Summary](#vrf-instances-summary)
  - [VRF Instances Device Configuration](#vrf-instances-device-configuration)

## Management

### Management Interfaces

#### Management Interfaces Summary

##### IPv4

| Management Interface | Description | Type | VRF | IP Address | Gateway |
| -------------------- | ----------- | ---- | --- | ---------- | ------- |
| Management0 | OOB_MANAGEMENT | oob | MGMT | 172.20.20.58/24 | 172.20.20.1 |

##### IPv6

| Management Interface | Description | Type | VRF | IPv6 Address | IPv6 Gateway |
| -------------------- | ----------- | ---- | --- | ------------ | ------------ |
| Management0 | OOB_MANAGEMENT | oob | MGMT | - | - |

#### Management Interfaces Device Configuration

```eos
!
interface Management0
   description OOB_MANAGEMENT
   no shutdown
   vrf MGMT
   ip address 172.20.20.58/24
```

### DNS Domain

DNS domain: atd.lab

#### DNS Domain Device Configuration

```eos
dns domain atd.lab
!
```

### IP Name Servers

#### IP Name Servers Summary

| Name Server | VRF | Priority |
| ----------- | --- | -------- |
| 192.168.1.9 | MGMT | - |

#### IP Name Servers Device Configuration

```eos
ip name-server vrf MGMT 192.168.1.9
```

### Management API HTTP

#### Management API HTTP Summary

| HTTP | HTTPS | UNIX-Socket | Default Services |
| ---- | ----- | ----------- | ---------------- |
| False | True | - | - |

#### Management API VRF Access

| VRF Name | IPv4 ACL | IPv6 ACL |
| -------- | -------- | -------- |
| MGMT | - | - |

#### Management API HTTP Device Configuration

```eos
!
management api http-commands
   protocol https
   no shutdown
   !
   vrf MGMT
      no shutdown
```

## Authentication

### Local Users

#### Local Users Summary

| User | Privilege | Role | Disabled | Shell |
| ---- | --------- | ---- | -------- | ----- |
| admin | 15 | network-admin | False | - |

#### Local Users Device Configuration

```eos
!
username admin privilege 15 role network-admin secret sha512 <removed>
username admin ssh-key ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCnwfwaeNOyHbwiE977rJSApT/qZ1eAGwaPKDwNgMuCzbu2HsIFQhFHNpVZpSYp3c9KLGWVYRRk0h5PatK41B56mMxTnHC2V6yiXEjWVo3n8RBCSTialsLh7j94hZyat3pFI6JAVi3Syv/LwuouXycIGyuhqph3SchEzmBJOohB7QCTktgqSmT80UolIPwNTSJQ0yY2dKs62spv/V7DPyE9VRbXoXhXBmHiE4mGyVy2TuhZ+TUFHIGhjZJidv8h+EqKe9HhDIe/eDlOzoioeQAgr9lvzWSVChbFfhFuV1grPTeaITF7Q9fdnLtMuge0oOcWbh03hUcbsM4C5tcCt+mkBmG8VyC2Ul7PgcZRCyFB8CHEvaj8ImRejisDys9WMkp9MzPBV8q673xQZzZuMAzt9olCx4Kv6DHbef8DZEZPv6dOJPOMDI5jsZx5OzE5l7hODFLeeW8ef+UwbQgt2rxbg1152YnUjgd6aejw2OH8bBZBwZkwRh65FtUE8XcLGnU= tony@autobox-huge
```

### Enable Password

Enable password has been disabled

### AAA Authentication

#### AAA Authentication Summary

| Type | Sub-type | User Stores |
| ---- | -------- | ---------- |
| Login | default | local |

#### AAA Authentication Device Configuration

```eos
aaa authentication login default local
!
```

### AAA Authorization

#### AAA Authorization Summary

| Type | User Stores |
| ---- | ----------- |
| Exec | local |

Authorization for configuration commands is disabled.

#### AAA Authorization Device Configuration

```eos
aaa authorization exec default local
!
```

## MLAG

### MLAG Summary

| Domain-id | Local-interface | Peer-address | Peer-link |
| --------- | --------------- | ------------ | --------- |
| mlag24 | Vlan4094 | 10.255.252.92 | Port-Channel1 |

Dual primary detection is disabled.

### MLAG Device Configuration

```eos
!
mlag configuration
   domain-id mlag24
   local-interface Vlan4094
   peer-address 10.255.252.92
   peer-link Port-Channel1
   reload-delay mlag 300
   reload-delay non-mlag 330
```

## Spanning Tree

### Spanning Tree Summary

STP mode: **mstp**

#### MSTP Instance and Priority

| Instance(s) | Priority |
| -------- | -------- |
| 0 | 16384 |

#### Global Spanning-Tree Settings

- Spanning Tree disabled for VLANs: **4093-4094**

### Spanning Tree Device Configuration

```eos
!
spanning-tree mode mstp
no spanning-tree vlan-id 4093-4094
spanning-tree mst 0 priority 16384
```

## Internal VLAN Allocation Policy

### Internal VLAN Allocation Policy Summary

| Policy Allocation | Range Beginning | Range Ending |
| ------------------| --------------- | ------------ |
| ascending | 1006 | 1199 |

### Internal VLAN Allocation Policy Device Configuration

```eos
!
vlan internal order ascending range 1006 1199
```

## VLANs

### VLANs Summary

| VLAN ID | Name | Trunk Groups |
| ------- | ---- | ------------ |
| 10 | DMZ | - |
| 20 | Internal | - |
| 30 | Dev | - |
| 40 | QA | - |
| 50 | Guest | - |
| 100 | VLAN_100 | - |
| 200 | VLAN_200 | - |
| 300 | VLAN_200 | - |
| 400 | VLAN_200 | - |
| 500 | VLAN_500 | - |
| 1000 | VLAN_1000 | - |
| 1001 | VLAN_1001 | - |
| 1002 | VLAN_1002 | - |
| 1003 | VLAN_1003 | - |
| 1004 | VLAN_1004 | - |
| 1005 | VLAN_1005 | - |
| 1006 | VLAN_1006 | - |
| 3009 | MLAG_L3_VRF_VRF_A | MLAG |
| 4093 | MLAG_L3 | MLAG |
| 4094 | MLAG | MLAG |

### VLANs Device Configuration

```eos
!
vlan 10
   name DMZ
!
vlan 20
   name Internal
!
vlan 30
   name Dev
!
vlan 40
   name QA
!
vlan 50
   name Guest
!
vlan 100
   name VLAN_100
!
vlan 200
   name VLAN_200
!
vlan 300
   name VLAN_200
!
vlan 400
   name VLAN_200
!
vlan 500
   name VLAN_500
!
vlan 1000
   name VLAN_1000
!
vlan 1001
   name VLAN_1001
!
vlan 1002
   name VLAN_1002
!
vlan 1003
   name VLAN_1003
!
vlan 1004
   name VLAN_1004
!
vlan 1005
   name VLAN_1005
!
vlan 1006
   name VLAN_1006
!
vlan 3009
   name MLAG_L3_VRF_VRF_A
   trunk group MLAG
!
vlan 4093
   name MLAG_L3
   trunk group MLAG
!
vlan 4094
   name MLAG
   trunk group MLAG
```

## Interfaces

### Ethernet Interfaces

#### Ethernet Interfaces Summary

##### L2

| Interface | Description | Mode | VLANs | Native VLAN | Trunk Group | Channel-Group |
| --------- | ----------- | ---- | ----- | ----------- | ----------- | ------------- |
| Ethernet1 | MLAG_leaf47_Ethernet1 | *trunk | *- | *- | *MLAG | 1 |
| Ethernet2 | MLAG_leaf47_Ethernet2 | *trunk | *- | *- | *MLAG | 1 |

*Inherited from Port-Channel Interface

##### IPv4

| Interface | Description | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet3 | P2P_spine1_Ethernet49 | - | 192.168.109.27/31 | default | 1550 | False | - | - |
| Ethernet4 | P2P_spine2_Ethernet49 | - | 192.168.109.29/31 | default | 1550 | False | - | - |
| Ethernet5 | P2P_spine3_Ethernet49 | - | 192.168.109.31/31 | default | 1550 | False | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet1
   description MLAG_leaf47_Ethernet1
   no shutdown
   channel-group 1 mode active
!
interface Ethernet2
   description MLAG_leaf47_Ethernet2
   no shutdown
   channel-group 1 mode active
!
interface Ethernet3
   description P2P_spine1_Ethernet49
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.27/31
!
interface Ethernet4
   description P2P_spine2_Ethernet49
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.29/31
!
interface Ethernet5
   description P2P_spine3_Ethernet49
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.31/31
```

### Port-Channel Interfaces

#### Port-Channel Interfaces Summary

##### L2

| Interface | Description | Mode | VLANs | Native VLAN | Trunk Group | LACP Fallback Timeout | LACP Fallback Mode | MLAG ID | EVPN ESI |
| --------- | ----------- | ---- | ----- | ----------- | ------------| --------------------- | ------------------ | ------- | -------- |
| Port-Channel1 | MLAG_leaf47_Port-Channel1 | trunk | - | - | MLAG | - | - | - | - |

#### Port-Channel Interfaces Device Configuration

```eos
!
interface Port-Channel1
   description MLAG_leaf47_Port-Channel1
   no shutdown
   switchport mode trunk
   switchport trunk group MLAG
   switchport
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | ROUTER_ID | default | 192.168.101.48/32 |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | 192.168.102.47/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | ROUTER_ID | default | - |
| Loopback1 | VXLAN_TUNNEL_SOURCE | default | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   description ROUTER_ID
   no shutdown
   ip address 192.168.101.48/32
!
interface Loopback1
   description VXLAN_TUNNEL_SOURCE
   no shutdown
   ip address 192.168.102.47/32
```

### VLAN Interfaces

#### VLAN Interfaces Summary

| Interface | Description | VRF |  MTU | Shutdown |
| --------- | ----------- | --- | ---- | -------- |
| Vlan10 | DMZ | VRF_A | - | False |
| Vlan20 | Internal | VRF_A | - | False |
| Vlan30 | Dev | VRF_A | - | False |
| Vlan40 | QA | VRF_A | - | False |
| Vlan50 | Guest | VRF_A | - | False |
| Vlan100 | VLAN_100 | VRF_A | - | False |
| Vlan200 | VLAN_200 | VRF_A | - | False |
| Vlan300 | VLAN_200 | VRF_A | - | False |
| Vlan400 | VLAN_200 | VRF_A | - | False |
| Vlan500 | VLAN_500 | VRF_A | - | True |
| Vlan3009 | MLAG_L3_VRF_VRF_A | VRF_A | 1550 | False |
| Vlan4093 | MLAG_L3 | default | 1550 | False |
| Vlan4094 | MLAG | default | 1550 | False |

##### IPv4

| Interface | VRF | IP Address | IP Address Virtual | IP Router Virtual Address | ACL In | ACL Out |
| --------- | --- | ---------- | ------------------ | ------------------------- | ------ | ------- |
| Vlan10 |  VRF_A  |  -  |  10.1.10.1/24  |  -  |  -  |  -  |
| Vlan20 |  VRF_A  |  -  |  10.1.20.1/24  |  -  |  -  |  -  |
| Vlan30 |  VRF_A  |  -  |  10.1.30.1/24  |  -  |  -  |  -  |
| Vlan40 |  VRF_A  |  -  |  10.1.40.1/24  |  -  |  -  |  -  |
| Vlan50 |  VRF_A  |  -  |  10.1.50.1/24  |  -  |  -  |  -  |
| Vlan100 |  VRF_A  |  -  |  10.1.100.1/24  |  -  |  -  |  -  |
| Vlan200 |  VRF_A  |  -  |  10.1.200.1/24  |  -  |  -  |  -  |
| Vlan300 |  VRF_A  |  -  |  10.1.31.1/24  |  -  |  -  |  -  |
| Vlan400 |  VRF_A  |  -  |  10.1.41.1/24  |  -  |  -  |  -  |
| Vlan500 |  VRF_A  |  -  |  10.1.51.1/24  |  -  |  -  |  -  |
| Vlan3009 |  VRF_A  |  10.255.251.93/31  |  -  |  -  |  -  |  -  |
| Vlan4093 |  default  |  10.255.251.93/31  |  -  |  -  |  -  |  -  |
| Vlan4094 |  default  |  10.255.252.93/31  |  -  |  -  |  -  |  -  |

#### VLAN Interfaces Device Configuration

```eos
!
interface Vlan10
   description DMZ
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.10.1/24
!
interface Vlan20
   description Internal
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.20.1/24
!
interface Vlan30
   description Dev
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.30.1/24
!
interface Vlan40
   description QA
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.40.1/24
!
interface Vlan50
   description Guest
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.50.1/24
!
interface Vlan100
   description VLAN_100
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.100.1/24
!
interface Vlan200
   description VLAN_200
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.200.1/24
!
interface Vlan300
   description VLAN_200
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.31.1/24
!
interface Vlan400
   description VLAN_200
   no shutdown
   vrf VRF_A
   ip address virtual 10.1.41.1/24
!
interface Vlan500
   description VLAN_500
   shutdown
   vrf VRF_A
   ip address virtual 10.1.51.1/24
!
interface Vlan3009
   description MLAG_L3_VRF_VRF_A
   no shutdown
   mtu 1550
   vrf VRF_A
   ip address 10.255.251.93/31
!
interface Vlan4093
   description MLAG_L3
   no shutdown
   mtu 1550
   ip address 10.255.251.93/31
!
interface Vlan4094
   description MLAG
   no shutdown
   mtu 1550
   no autostate
   ip address 10.255.252.93/31
```

### VXLAN Interface

#### VXLAN Interface Summary

| Setting | Value |
| ------- | ----- |
| Source Interface | Loopback1 |
| UDP port | 4789 |
| EVPN MLAG Shared Router MAC | mlag-system-id |

##### VLAN to VNI, Flood List and Multicast Group Mappings

| VLAN | VNI | Flood List | Multicast Group |
| ---- | --- | ---------- | --------------- |
| 10 | 10010 | - | - |
| 20 | 10020 | - | - |
| 30 | 10030 | - | - |
| 40 | 10040 | - | - |
| 50 | 10050 | - | - |
| 100 | 10100 | - | - |
| 200 | 10200 | - | - |
| 300 | 10300 | - | - |
| 400 | 10400 | - | - |
| 500 | 10500 | - | - |
| 1000 | 11000 | - | - |
| 1001 | 11001 | - | - |
| 1002 | 11002 | - | - |
| 1003 | 11003 | - | - |
| 1004 | 11004 | - | - |
| 1005 | 11005 | - | - |
| 1006 | 11006 | - | - |

##### VRF to VNI and Multicast Group Mappings

| VRF | VNI | Multicast Group |
| ---- | --- | --------------- |
| VRF_A | 10 | - |

#### VXLAN Interface Device Configuration

```eos
!
interface Vxlan1
   description leaf48_VTEP
   vxlan source-interface Loopback1
   vxlan virtual-router encapsulation mac-address mlag-system-id
   vxlan udp-port 4789
   vxlan vlan 10 vni 10010
   vxlan vlan 20 vni 10020
   vxlan vlan 30 vni 10030
   vxlan vlan 40 vni 10040
   vxlan vlan 50 vni 10050
   vxlan vlan 100 vni 10100
   vxlan vlan 200 vni 10200
   vxlan vlan 300 vni 10300
   vxlan vlan 400 vni 10400
   vxlan vlan 500 vni 10500
   vxlan vlan 1000 vni 11000
   vxlan vlan 1001 vni 11001
   vxlan vlan 1002 vni 11002
   vxlan vlan 1003 vni 11003
   vxlan vlan 1004 vni 11004
   vxlan vlan 1005 vni 11005
   vxlan vlan 1006 vni 11006
   vxlan vrf VRF_A vni 10
```

## Routing

### Service Routing Protocols Model

Multi agent routing protocol model enabled

```eos
!
service routing protocols model multi-agent
```

### Virtual Router MAC Address

#### Virtual Router MAC Address Summary

Virtual Router MAC Address: 00:1c:73:00:00:99

#### Virtual Router MAC Address Device Configuration

```eos
!
ip virtual-router mac-address 00:1c:73:00:00:99
```

### IP Routing

#### IP Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | True |
| MGMT | False |
| VRF_A | True |

#### IP Routing Device Configuration

```eos
!
ip routing
no ip routing vrf MGMT
ip routing vrf VRF_A
```

### IPv6 Routing

#### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | False |
| MGMT | false |
| VRF_A | false |

### Static Routes

#### Static Routes Summary

| VRF | Destination Prefix | Next Hop IP | Exit interface | Administrative Distance | Tag | Route Name | Metric |
| --- | ------------------ | ----------- | -------------- | ----------------------- | --- | ---------- | ------ |
| MGMT | 0.0.0.0/0 | 172.20.20.1 | - | 1 | - | - | - |

#### Static Routes Device Configuration

```eos
!
ip route vrf MGMT 0.0.0.0/0 172.20.20.1
```

### Router BGP

ASN Notation: asplain

#### Router BGP Summary

| BGP AS | Router ID |
| ------ | --------- |
| 65146 | 192.168.101.48 |

| BGP Tuning |
| ---------- |
| no bgp default ipv4-unicast |
| maximum-paths 4 ecmp 4 |

#### Router BGP Peer Groups

##### EVPN-OVERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | evpn |
| Source | Loopback0 |
| BFD | True |
| Ebgp multihop | 3 |
| Send community | all |
| Maximum routes | 0 (no limit) |

##### IPv4-UNDERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | ipv4 |
| Send community | all |
| Maximum routes | 12000 |

##### MLAG-IPv4-UNDERLAY-PEER

| Settings | Value |
| -------- | ----- |
| Address Family | ipv4 |
| Remote AS | 65146 |
| Next-hop self | True |
| Send community | all |
| Maximum routes | 12000 |

#### BGP Neighbors

| Neighbor | Remote AS | VRF | Shutdown | Send-community | Maximum-routes | Allowas-in | BFD | RIB Pre-Policy Retain | Route-Reflector Client | Passive | TTL Max Hops |
| -------- | --------- | --- | -------- | -------------- | -------------- | ---------- | --- | --------------------- | ---------------------- | ------- | ------------ |
| 10.255.251.92 | Inherited from peer group MLAG-IPv4-UNDERLAY-PEER | default | - | Inherited from peer group MLAG-IPv4-UNDERLAY-PEER | Inherited from peer group MLAG-IPv4-UNDERLAY-PEER | - | - | - | - | - | - |
| 192.168.101.101 | 65001 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.102 | 65001 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.103 | 65001 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.109.26 | 65001 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.28 | 65001 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.30 | 65001 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 10.255.251.92 | Inherited from peer group MLAG-IPv4-UNDERLAY-PEER | VRF_A | - | Inherited from peer group MLAG-IPv4-UNDERLAY-PEER | Inherited from peer group MLAG-IPv4-UNDERLAY-PEER | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True |  - | - | default | - |

#### Router BGP VLAN Aware Bundles

| VLAN Aware Bundle | Route-Distinguisher | Both Route-Target | Import Route Target | Export Route-Target | Redistribute | VLANs |
| ----------------- | ------------------- | ----------------- | ------------------- | ------------------- | ------------ | ----- |
| VLAN_1000 | 192.168.101.48:11000 | 11000:11000 | - | - | learned | 1000 |
| VLAN_1001 | 192.168.101.48:11001 | 11001:11001 | - | - | learned | 1001 |
| VLAN_1002 | 192.168.101.48:11002 | 11002:11002 | - | - | learned | 1002 |
| VLAN_1003 | 192.168.101.48:11003 | 11003:11003 | - | - | learned | 1003 |
| VLAN_1004 | 192.168.101.48:11004 | 11004:11004 | - | - | learned | 1004 |
| VLAN_1005 | 192.168.101.48:11005 | 11005:11005 | - | - | learned | 1005 |
| VLAN_1006 | 192.168.101.48:11006 | 11006:11006 | - | - | learned | 1006 |
| VRF_A | 192.168.101.48:10 | 10:10 | - | - | learned | 10,20,30,40,50,100,200,300,400,500 |

#### Router BGP VRFs

| VRF | Route-Distinguisher | Redistribute | Graceful Restart |
| --- | ------------------- | ------------ | ---------------- |
| VRF_A | 192.168.101.48:10 | connected | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65146
   router-id 192.168.101.48
   no bgp default ipv4-unicast
   maximum-paths 4 ecmp 4
   neighbor EVPN-OVERLAY-PEERS peer group
   neighbor EVPN-OVERLAY-PEERS update-source Loopback0
   neighbor EVPN-OVERLAY-PEERS bfd
   neighbor EVPN-OVERLAY-PEERS ebgp-multihop 3
   neighbor EVPN-OVERLAY-PEERS send-community
   neighbor EVPN-OVERLAY-PEERS maximum-routes 0
   neighbor IPv4-UNDERLAY-PEERS peer group
   neighbor IPv4-UNDERLAY-PEERS send-community
   neighbor IPv4-UNDERLAY-PEERS maximum-routes 12000
   neighbor MLAG-IPv4-UNDERLAY-PEER peer group
   neighbor MLAG-IPv4-UNDERLAY-PEER remote-as 65146
   neighbor MLAG-IPv4-UNDERLAY-PEER next-hop-self
   neighbor MLAG-IPv4-UNDERLAY-PEER description leaf47
   neighbor MLAG-IPv4-UNDERLAY-PEER route-map RM-MLAG-PEER-IN in
   neighbor MLAG-IPv4-UNDERLAY-PEER send-community
   neighbor MLAG-IPv4-UNDERLAY-PEER maximum-routes 12000
   neighbor 10.255.251.92 peer group MLAG-IPv4-UNDERLAY-PEER
   neighbor 10.255.251.92 description leaf47_Vlan4093
   neighbor 192.168.101.101 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.101 remote-as 65001
   neighbor 192.168.101.101 description spine1_Loopback0
   neighbor 192.168.101.102 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.102 remote-as 65001
   neighbor 192.168.101.102 description spine2_Loopback0
   neighbor 192.168.101.103 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.103 remote-as 65001
   neighbor 192.168.101.103 description spine3_Loopback0
   neighbor 192.168.109.26 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.26 remote-as 65001
   neighbor 192.168.109.26 description spine1_Ethernet49
   neighbor 192.168.109.28 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.28 remote-as 65001
   neighbor 192.168.109.28 description spine2_Ethernet49
   neighbor 192.168.109.30 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.30 remote-as 65001
   neighbor 192.168.109.30 description spine3_Ethernet49
   redistribute connected route-map RM-CONN-2-BGP
   !
   vlan-aware-bundle VLAN_1000
      rd 192.168.101.48:11000
      route-target both 11000:11000
      redistribute learned
      vlan 1000
   !
   vlan-aware-bundle VLAN_1001
      rd 192.168.101.48:11001
      route-target both 11001:11001
      redistribute learned
      vlan 1001
   !
   vlan-aware-bundle VLAN_1002
      rd 192.168.101.48:11002
      route-target both 11002:11002
      redistribute learned
      vlan 1002
   !
   vlan-aware-bundle VLAN_1003
      rd 192.168.101.48:11003
      route-target both 11003:11003
      redistribute learned
      vlan 1003
   !
   vlan-aware-bundle VLAN_1004
      rd 192.168.101.48:11004
      route-target both 11004:11004
      redistribute learned
      vlan 1004
   !
   vlan-aware-bundle VLAN_1005
      rd 192.168.101.48:11005
      route-target both 11005:11005
      redistribute learned
      vlan 1005
   !
   vlan-aware-bundle VLAN_1006
      rd 192.168.101.48:11006
      route-target both 11006:11006
      redistribute learned
      vlan 1006
   !
   vlan-aware-bundle VRF_A
      rd 192.168.101.48:10
      route-target both 10:10
      redistribute learned
      vlan 10,20,30,40,50,100,200,300,400,500
   !
   address-family evpn
      neighbor EVPN-OVERLAY-PEERS activate
   !
   address-family ipv4
      no neighbor EVPN-OVERLAY-PEERS activate
      neighbor IPv4-UNDERLAY-PEERS activate
      neighbor MLAG-IPv4-UNDERLAY-PEER activate
   !
   vrf VRF_A
      rd 192.168.101.48:10
      route-target import evpn 10:10
      route-target export evpn 10:10
      router-id 192.168.101.48
      neighbor 10.255.251.92 peer group MLAG-IPv4-UNDERLAY-PEER
      neighbor 10.255.251.92 description leaf47_Vlan3009
      redistribute connected route-map RM-CONN-2-BGP-VRFS
```

## BFD

### Router BFD

#### Router BFD Multihop Summary

| Interval | Minimum RX | Multiplier |
| -------- | ---------- | ---------- |
| 1200 | 1200 | 3 |

#### Router BFD Device Configuration

```eos
!
router bfd
   multihop interval 1200 min-rx 1200 multiplier 3
```

## Multicast

### IP IGMP Snooping

#### IP IGMP Snooping Summary

| IGMP Snooping | Fast Leave | Interface Restart Query | Proxy | Restart Query Interval | Robustness Variable |
| ------------- | ---------- | ----------------------- | ----- | ---------------------- | ------------------- |
| Enabled | - | - | - | - | - |

#### IP IGMP Snooping Device Configuration

```eos
```

## Filters

### Prefix-lists

#### Prefix-lists Summary

##### PL-LOOPBACKS-EVPN-OVERLAY

| Sequence | Action |
| -------- | ------ |
| 10 | permit 192.168.101.0/24 eq 32 |
| 20 | permit 192.168.102.0/24 eq 32 |

##### PL-MLAG-PEER-VRFS

| Sequence | Action |
| -------- | ------ |
| 10 | permit 10.255.251.92/31 |

#### Prefix-lists Device Configuration

```eos
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 192.168.101.0/24 eq 32
   seq 20 permit 192.168.102.0/24 eq 32
!
ip prefix-list PL-MLAG-PEER-VRFS
   seq 10 permit 10.255.251.92/31
```

### Route-maps

#### Route-maps Summary

##### RM-CONN-2-BGP

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY | - | - | - |

##### RM-CONN-2-BGP-VRFS

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | deny | ip address prefix-list PL-MLAG-PEER-VRFS | - | - | - |
| 20 | permit | - | - | - | - |

##### RM-MLAG-PEER-IN

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | - | origin incomplete | - | - |

#### Route-maps Device Configuration

```eos
!
route-map RM-CONN-2-BGP permit 10
   match ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY
!
route-map RM-CONN-2-BGP-VRFS deny 10
   match ip address prefix-list PL-MLAG-PEER-VRFS
!
route-map RM-CONN-2-BGP-VRFS permit 20
!
route-map RM-MLAG-PEER-IN permit 10
   description Make routes learned over MLAG Peer-link less preferred on spines to ensure optimal routing
   set origin incomplete
```

## VRF Instances

### VRF Instances Summary

| VRF Name | IP Routing |
| -------- | ---------- |
| MGMT | disabled |
| VRF_A | enabled |

### VRF Instances Device Configuration

```eos
!
vrf instance MGMT
!
vrf instance VRF_A
```
