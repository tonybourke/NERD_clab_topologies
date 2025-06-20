# spine1

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
- [Spanning Tree](#spanning-tree)
  - [Spanning Tree Summary](#spanning-tree-summary)
  - [Spanning Tree Device Configuration](#spanning-tree-device-configuration)
- [Internal VLAN Allocation Policy](#internal-vlan-allocation-policy)
  - [Internal VLAN Allocation Policy Summary](#internal-vlan-allocation-policy-summary)
  - [Internal VLAN Allocation Policy Device Configuration](#internal-vlan-allocation-policy-device-configuration)
- [Interfaces](#interfaces)
  - [Ethernet Interfaces](#ethernet-interfaces)
  - [Loopback Interfaces](#loopback-interfaces)
- [Routing](#routing)
  - [Service Routing Protocols Model](#service-routing-protocols-model)
  - [IP Routing](#ip-routing)
  - [IPv6 Routing](#ipv6-routing)
  - [Static Routes](#static-routes)
  - [Router BGP](#router-bgp)
- [BFD](#bfd)
  - [Router BFD](#router-bfd)
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
| Management0 | OOB_MANAGEMENT | oob | MGMT | 172.20.20.101/24 | 172.20.20.1 |

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
   ip address 172.20.20.101/24
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

## Spanning Tree

### Spanning Tree Summary

STP mode: **none**

### Spanning Tree Device Configuration

```eos
!
spanning-tree mode none
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

## Interfaces

### Ethernet Interfaces

#### Ethernet Interfaces Summary

##### L2

| Interface | Description | Mode | VLANs | Native VLAN | Trunk Group | Channel-Group |
| --------- | ----------- | ---- | ----- | ----------- | ----------- | ------------- |

*Inherited from Port-Channel Interface

##### IPv4

| Interface | Description | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet2 | P2P_leaf1_Ethernet3 | - | 192.168.108.0/31 | default | 1550 | False | - | - |
| Ethernet3 | P2P_leaf2_Ethernet3 | - | 192.168.108.6/31 | default | 1550 | False | - | - |
| Ethernet4 | P2P_leaf3_Ethernet3 | - | 192.168.108.12/31 | default | 1550 | False | - | - |
| Ethernet5 | P2P_leaf4_Ethernet3 | - | 192.168.108.18/31 | default | 1550 | False | - | - |
| Ethernet6 | P2P_leaf5_Ethernet3 | - | 192.168.108.24/31 | default | 1550 | False | - | - |
| Ethernet7 | P2P_leaf6_Ethernet3 | - | 192.168.108.30/31 | default | 1550 | False | - | - |
| Ethernet8 | P2P_leaf7_Ethernet3 | - | 192.168.108.36/31 | default | 1550 | False | - | - |
| Ethernet9 | P2P_leaf8_Ethernet3 | - | 192.168.108.42/31 | default | 1550 | False | - | - |
| Ethernet10 | P2P_leaf9_Ethernet3 | - | 192.168.108.48/31 | default | 1550 | False | - | - |
| Ethernet11 | P2P_leaf10_Ethernet3 | - | 192.168.108.54/31 | default | 1550 | False | - | - |
| Ethernet12 | P2P_leaf11_Ethernet3 | - | 192.168.108.60/31 | default | 1550 | False | - | - |
| Ethernet13 | P2P_leaf12_Ethernet3 | - | 192.168.108.66/31 | default | 1550 | False | - | - |
| Ethernet14 | P2P_leaf13_Ethernet3 | - | 192.168.108.72/31 | default | 1550 | False | - | - |
| Ethernet15 | P2P_leaf14_Ethernet3 | - | 192.168.108.78/31 | default | 1550 | False | - | - |
| Ethernet16 | P2P_leaf15_Ethernet3 | - | 192.168.108.84/31 | default | 1550 | False | - | - |
| Ethernet17 | P2P_leaf16_Ethernet3 | - | 192.168.108.90/31 | default | 1550 | False | - | - |
| Ethernet18 | P2P_leaf17_Ethernet3 | - | 192.168.108.96/31 | default | 1550 | False | - | - |
| Ethernet19 | P2P_leaf18_Ethernet3 | - | 192.168.108.102/31 | default | 1550 | False | - | - |
| Ethernet20 | P2P_leaf19_Ethernet3 | - | 192.168.108.108/31 | default | 1550 | False | - | - |
| Ethernet21 | P2P_leaf20_Ethernet3 | - | 192.168.108.114/31 | default | 1550 | False | - | - |
| Ethernet22 | P2P_leaf21_Ethernet3 | - | 192.168.108.120/31 | default | 1550 | False | - | - |
| Ethernet23 | P2P_leaf22_Ethernet3 | - | 192.168.108.126/31 | default | 1550 | False | - | - |
| Ethernet24 | P2P_leaf23_Ethernet3 | - | 192.168.108.132/31 | default | 1550 | False | - | - |
| Ethernet25 | P2P_leaf24_Ethernet3 | - | 192.168.108.138/31 | default | 1550 | False | - | - |
| Ethernet26 | P2P_leaf25_Ethernet3 | - | 192.168.108.144/31 | default | 1550 | False | - | - |
| Ethernet27 | P2P_leaf26_Ethernet3 | - | 192.168.108.150/31 | default | 1550 | False | - | - |
| Ethernet28 | P2P_leaf27_Ethernet3 | - | 192.168.108.156/31 | default | 1550 | False | - | - |
| Ethernet29 | P2P_leaf28_Ethernet3 | - | 192.168.108.162/31 | default | 1550 | False | - | - |
| Ethernet30 | P2P_leaf29_Ethernet3 | - | 192.168.108.168/31 | default | 1550 | False | - | - |
| Ethernet31 | P2P_leaf30_Ethernet3 | - | 192.168.108.174/31 | default | 1550 | False | - | - |
| Ethernet32 | P2P_leaf31_Ethernet3 | - | 192.168.108.180/31 | default | 1550 | False | - | - |
| Ethernet33 | P2P_leaf32_Ethernet3 | - | 192.168.108.186/31 | default | 1550 | False | - | - |
| Ethernet34 | P2P_leaf33_Ethernet3 | - | 192.168.108.192/31 | default | 1550 | False | - | - |
| Ethernet35 | P2P_leaf34_Ethernet3 | - | 192.168.108.198/31 | default | 1550 | False | - | - |
| Ethernet36 | P2P_leaf35_Ethernet3 | - | 192.168.108.204/31 | default | 1550 | False | - | - |
| Ethernet37 | P2P_leaf36_Ethernet3 | - | 192.168.108.210/31 | default | 1550 | False | - | - |
| Ethernet38 | P2P_leaf37_Ethernet3 | - | 192.168.108.216/31 | default | 1550 | False | - | - |
| Ethernet39 | P2P_leaf38_Ethernet3 | - | 192.168.108.222/31 | default | 1550 | False | - | - |
| Ethernet40 | P2P_leaf39_Ethernet3 | - | 192.168.108.228/31 | default | 1550 | False | - | - |
| Ethernet41 | P2P_leaf40_Ethernet3 | - | 192.168.108.234/31 | default | 1550 | False | - | - |
| Ethernet42 | P2P_leaf41_Ethernet3 | - | 192.168.108.240/31 | default | 1550 | False | - | - |
| Ethernet43 | P2P_leaf42_Ethernet3 | - | 192.168.108.246/31 | default | 1550 | False | - | - |
| Ethernet44 | P2P_leaf43_Ethernet3 | - | 192.168.108.252/31 | default | 1550 | False | - | - |
| Ethernet45 | P2P_leaf44_Ethernet3 | - | 192.168.109.2/31 | default | 1550 | False | - | - |
| Ethernet46 | P2P_leaf45_Ethernet3 | - | 192.168.109.8/31 | default | 1550 | False | - | - |
| Ethernet47 | P2P_leaf46_Ethernet3 | - | 192.168.109.14/31 | default | 1550 | False | - | - |
| Ethernet48 | P2P_leaf47_Ethernet3 | - | 192.168.109.20/31 | default | 1550 | False | - | - |
| Ethernet49 | P2P_leaf48_Ethernet3 | - | 192.168.109.26/31 | default | 1550 | False | - | - |
| Ethernet50 | P2P_leaf49_Ethernet3 | - | 192.168.109.32/31 | default | 1550 | False | - | - |
| Ethernet51 | P2P_leaf50_Ethernet3 | - | 192.168.109.38/31 | default | 1550 | False | - | - |
| Ethernet52 | P2P_borderleaf1_Ethernet3 | - | 192.168.110.28/31 | default | 1550 | False | - | - |
| Ethernet53 | P2P_borderleaf2_Ethernet3 | - | 192.168.110.34/31 | default | 1550 | False | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet2
   description P2P_leaf1_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.0/31
!
interface Ethernet3
   description P2P_leaf2_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.6/31
!
interface Ethernet4
   description P2P_leaf3_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.12/31
!
interface Ethernet5
   description P2P_leaf4_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.18/31
!
interface Ethernet6
   description P2P_leaf5_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.24/31
!
interface Ethernet7
   description P2P_leaf6_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.30/31
!
interface Ethernet8
   description P2P_leaf7_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.36/31
!
interface Ethernet9
   description P2P_leaf8_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.42/31
!
interface Ethernet10
   description P2P_leaf9_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.48/31
!
interface Ethernet11
   description P2P_leaf10_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.54/31
!
interface Ethernet12
   description P2P_leaf11_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.60/31
!
interface Ethernet13
   description P2P_leaf12_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.66/31
!
interface Ethernet14
   description P2P_leaf13_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.72/31
!
interface Ethernet15
   description P2P_leaf14_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.78/31
!
interface Ethernet16
   description P2P_leaf15_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.84/31
!
interface Ethernet17
   description P2P_leaf16_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.90/31
!
interface Ethernet18
   description P2P_leaf17_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.96/31
!
interface Ethernet19
   description P2P_leaf18_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.102/31
!
interface Ethernet20
   description P2P_leaf19_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.108/31
!
interface Ethernet21
   description P2P_leaf20_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.114/31
!
interface Ethernet22
   description P2P_leaf21_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.120/31
!
interface Ethernet23
   description P2P_leaf22_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.126/31
!
interface Ethernet24
   description P2P_leaf23_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.132/31
!
interface Ethernet25
   description P2P_leaf24_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.138/31
!
interface Ethernet26
   description P2P_leaf25_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.144/31
!
interface Ethernet27
   description P2P_leaf26_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.150/31
!
interface Ethernet28
   description P2P_leaf27_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.156/31
!
interface Ethernet29
   description P2P_leaf28_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.162/31
!
interface Ethernet30
   description P2P_leaf29_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.168/31
!
interface Ethernet31
   description P2P_leaf30_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.174/31
!
interface Ethernet32
   description P2P_leaf31_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.180/31
!
interface Ethernet33
   description P2P_leaf32_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.186/31
!
interface Ethernet34
   description P2P_leaf33_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.192/31
!
interface Ethernet35
   description P2P_leaf34_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.198/31
!
interface Ethernet36
   description P2P_leaf35_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.204/31
!
interface Ethernet37
   description P2P_leaf36_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.210/31
!
interface Ethernet38
   description P2P_leaf37_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.216/31
!
interface Ethernet39
   description P2P_leaf38_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.222/31
!
interface Ethernet40
   description P2P_leaf39_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.228/31
!
interface Ethernet41
   description P2P_leaf40_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.234/31
!
interface Ethernet42
   description P2P_leaf41_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.240/31
!
interface Ethernet43
   description P2P_leaf42_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.246/31
!
interface Ethernet44
   description P2P_leaf43_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.108.252/31
!
interface Ethernet45
   description P2P_leaf44_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.2/31
!
interface Ethernet46
   description P2P_leaf45_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.8/31
!
interface Ethernet47
   description P2P_leaf46_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.14/31
!
interface Ethernet48
   description P2P_leaf47_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.20/31
!
interface Ethernet49
   description P2P_leaf48_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.26/31
!
interface Ethernet50
   description P2P_leaf49_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.32/31
!
interface Ethernet51
   description P2P_leaf50_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.109.38/31
!
interface Ethernet52
   description P2P_borderleaf1_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.110.28/31
!
interface Ethernet53
   description P2P_borderleaf2_Ethernet3
   no shutdown
   mtu 1550
   no switchport
   ip address 192.168.110.34/31
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | ROUTER_ID | default | 192.168.101.101/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | ROUTER_ID | default | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   description ROUTER_ID
   no shutdown
   ip address 192.168.101.101/32
```

## Routing

### Service Routing Protocols Model

Multi agent routing protocol model enabled

```eos
!
service routing protocols model multi-agent
```

### IP Routing

#### IP Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | True |
| MGMT | False |

#### IP Routing Device Configuration

```eos
!
ip routing
no ip routing vrf MGMT
```

### IPv6 Routing

#### IPv6 Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | False |
| MGMT | false |

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
| 65001 | 192.168.101.101 |

| BGP Tuning |
| ---------- |
| no bgp default ipv4-unicast |
| maximum-paths 4 ecmp 4 |

#### Router BGP Peer Groups

##### EVPN-OVERLAY-PEERS

| Settings | Value |
| -------- | ----- |
| Address Family | evpn |
| Next-hop unchanged | True |
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

#### BGP Neighbors

| Neighbor | Remote AS | VRF | Shutdown | Send-community | Maximum-routes | Allowas-in | BFD | RIB Pre-Policy Retain | Route-Reflector Client | Passive | TTL Max Hops |
| -------- | --------- | --- | -------- | -------------- | -------------- | ---------- | --- | --------------------- | ---------------------- | ------- | ------------ |
| 192.168.101.1 | 65100 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.2 | 65100 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.3 | 65102 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.4 | 65102 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.5 | 65104 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.6 | 65104 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.7 | 65106 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.8 | 65106 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.9 | 65108 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.10 | 65108 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.11 | 65110 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.12 | 65110 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.13 | 65112 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.14 | 65112 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.15 | 65114 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.16 | 65114 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.17 | 65116 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.18 | 65116 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.19 | 65118 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.20 | 65118 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.21 | 65120 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.22 | 65120 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.23 | 65122 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.24 | 65122 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.25 | 65124 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.26 | 65124 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.27 | 65126 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.28 | 65126 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.29 | 65128 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.30 | 65128 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.31 | 65130 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.32 | 65130 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.33 | 65132 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.34 | 65132 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.35 | 65134 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.36 | 65134 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.37 | 65136 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.38 | 65136 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.39 | 65138 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.40 | 65138 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.41 | 65140 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.42 | 65140 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.43 | 65142 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.44 | 65142 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.45 | 65144 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.46 | 65144 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.47 | 65146 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.48 | 65146 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.49 | 65148 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.50 | 65148 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.91 | 65190 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.101.92 | 65191 | default | - | Inherited from peer group EVPN-OVERLAY-PEERS | Inherited from peer group EVPN-OVERLAY-PEERS | - | Inherited from peer group EVPN-OVERLAY-PEERS | - | - | - | - |
| 192.168.108.1 | 65100 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.7 | 65100 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.13 | 65102 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.19 | 65102 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.25 | 65104 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.31 | 65104 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.37 | 65106 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.43 | 65106 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.49 | 65108 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.55 | 65108 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.61 | 65110 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.67 | 65110 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.73 | 65112 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.79 | 65112 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.85 | 65114 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.91 | 65114 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.97 | 65116 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.103 | 65116 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.109 | 65118 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.115 | 65118 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.121 | 65120 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.127 | 65120 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.133 | 65122 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.139 | 65122 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.145 | 65124 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.151 | 65124 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.157 | 65126 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.163 | 65126 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.169 | 65128 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.175 | 65128 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.181 | 65130 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.187 | 65130 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.193 | 65132 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.199 | 65132 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.205 | 65134 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.211 | 65134 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.217 | 65136 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.223 | 65136 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.229 | 65138 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.235 | 65138 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.241 | 65140 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.247 | 65140 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.108.253 | 65142 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.3 | 65142 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.9 | 65144 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.15 | 65144 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.21 | 65146 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.27 | 65146 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.33 | 65148 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.109.39 | 65148 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.110.29 | 65190 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |
| 192.168.110.35 | 65191 | default | - | Inherited from peer group IPv4-UNDERLAY-PEERS | Inherited from peer group IPv4-UNDERLAY-PEERS | - | - | - | - | - | - |

#### Router BGP EVPN Address Family

##### EVPN Peer Groups

| Peer Group | Activate | Route-map In | Route-map Out | Encapsulation | Next-hop-self Source Interface |
| ---------- | -------- | ------------ | ------------- | ------------- | ------------------------------ |
| EVPN-OVERLAY-PEERS | True |  - | - | default | - |

#### Router BGP Device Configuration

```eos
!
router bgp 65001
   router-id 192.168.101.101
   no bgp default ipv4-unicast
   maximum-paths 4 ecmp 4
   neighbor EVPN-OVERLAY-PEERS peer group
   neighbor EVPN-OVERLAY-PEERS next-hop-unchanged
   neighbor EVPN-OVERLAY-PEERS update-source Loopback0
   neighbor EVPN-OVERLAY-PEERS bfd
   neighbor EVPN-OVERLAY-PEERS ebgp-multihop 3
   neighbor EVPN-OVERLAY-PEERS send-community
   neighbor EVPN-OVERLAY-PEERS maximum-routes 0
   neighbor IPv4-UNDERLAY-PEERS peer group
   neighbor IPv4-UNDERLAY-PEERS send-community
   neighbor IPv4-UNDERLAY-PEERS maximum-routes 12000
   neighbor 192.168.101.1 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.1 remote-as 65100
   neighbor 192.168.101.1 description leaf1_Loopback0
   neighbor 192.168.101.2 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.2 remote-as 65100
   neighbor 192.168.101.2 description leaf2_Loopback0
   neighbor 192.168.101.3 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.3 remote-as 65102
   neighbor 192.168.101.3 description leaf3_Loopback0
   neighbor 192.168.101.4 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.4 remote-as 65102
   neighbor 192.168.101.4 description leaf4_Loopback0
   neighbor 192.168.101.5 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.5 remote-as 65104
   neighbor 192.168.101.5 description leaf5_Loopback0
   neighbor 192.168.101.6 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.6 remote-as 65104
   neighbor 192.168.101.6 description leaf6_Loopback0
   neighbor 192.168.101.7 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.7 remote-as 65106
   neighbor 192.168.101.7 description leaf7_Loopback0
   neighbor 192.168.101.8 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.8 remote-as 65106
   neighbor 192.168.101.8 description leaf8_Loopback0
   neighbor 192.168.101.9 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.9 remote-as 65108
   neighbor 192.168.101.9 description leaf9_Loopback0
   neighbor 192.168.101.10 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.10 remote-as 65108
   neighbor 192.168.101.10 description leaf10_Loopback0
   neighbor 192.168.101.11 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.11 remote-as 65110
   neighbor 192.168.101.11 description leaf11_Loopback0
   neighbor 192.168.101.12 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.12 remote-as 65110
   neighbor 192.168.101.12 description leaf12_Loopback0
   neighbor 192.168.101.13 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.13 remote-as 65112
   neighbor 192.168.101.13 description leaf13_Loopback0
   neighbor 192.168.101.14 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.14 remote-as 65112
   neighbor 192.168.101.14 description leaf14_Loopback0
   neighbor 192.168.101.15 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.15 remote-as 65114
   neighbor 192.168.101.15 description leaf15_Loopback0
   neighbor 192.168.101.16 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.16 remote-as 65114
   neighbor 192.168.101.16 description leaf16_Loopback0
   neighbor 192.168.101.17 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.17 remote-as 65116
   neighbor 192.168.101.17 description leaf17_Loopback0
   neighbor 192.168.101.18 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.18 remote-as 65116
   neighbor 192.168.101.18 description leaf18_Loopback0
   neighbor 192.168.101.19 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.19 remote-as 65118
   neighbor 192.168.101.19 description leaf19_Loopback0
   neighbor 192.168.101.20 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.20 remote-as 65118
   neighbor 192.168.101.20 description leaf20_Loopback0
   neighbor 192.168.101.21 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.21 remote-as 65120
   neighbor 192.168.101.21 description leaf21_Loopback0
   neighbor 192.168.101.22 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.22 remote-as 65120
   neighbor 192.168.101.22 description leaf22_Loopback0
   neighbor 192.168.101.23 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.23 remote-as 65122
   neighbor 192.168.101.23 description leaf23_Loopback0
   neighbor 192.168.101.24 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.24 remote-as 65122
   neighbor 192.168.101.24 description leaf24_Loopback0
   neighbor 192.168.101.25 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.25 remote-as 65124
   neighbor 192.168.101.25 description leaf25_Loopback0
   neighbor 192.168.101.26 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.26 remote-as 65124
   neighbor 192.168.101.26 description leaf26_Loopback0
   neighbor 192.168.101.27 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.27 remote-as 65126
   neighbor 192.168.101.27 description leaf27_Loopback0
   neighbor 192.168.101.28 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.28 remote-as 65126
   neighbor 192.168.101.28 description leaf28_Loopback0
   neighbor 192.168.101.29 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.29 remote-as 65128
   neighbor 192.168.101.29 description leaf29_Loopback0
   neighbor 192.168.101.30 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.30 remote-as 65128
   neighbor 192.168.101.30 description leaf30_Loopback0
   neighbor 192.168.101.31 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.31 remote-as 65130
   neighbor 192.168.101.31 description leaf31_Loopback0
   neighbor 192.168.101.32 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.32 remote-as 65130
   neighbor 192.168.101.32 description leaf32_Loopback0
   neighbor 192.168.101.33 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.33 remote-as 65132
   neighbor 192.168.101.33 description leaf33_Loopback0
   neighbor 192.168.101.34 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.34 remote-as 65132
   neighbor 192.168.101.34 description leaf34_Loopback0
   neighbor 192.168.101.35 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.35 remote-as 65134
   neighbor 192.168.101.35 description leaf35_Loopback0
   neighbor 192.168.101.36 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.36 remote-as 65134
   neighbor 192.168.101.36 description leaf36_Loopback0
   neighbor 192.168.101.37 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.37 remote-as 65136
   neighbor 192.168.101.37 description leaf37_Loopback0
   neighbor 192.168.101.38 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.38 remote-as 65136
   neighbor 192.168.101.38 description leaf38_Loopback0
   neighbor 192.168.101.39 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.39 remote-as 65138
   neighbor 192.168.101.39 description leaf39_Loopback0
   neighbor 192.168.101.40 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.40 remote-as 65138
   neighbor 192.168.101.40 description leaf40_Loopback0
   neighbor 192.168.101.41 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.41 remote-as 65140
   neighbor 192.168.101.41 description leaf41_Loopback0
   neighbor 192.168.101.42 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.42 remote-as 65140
   neighbor 192.168.101.42 description leaf42_Loopback0
   neighbor 192.168.101.43 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.43 remote-as 65142
   neighbor 192.168.101.43 description leaf43_Loopback0
   neighbor 192.168.101.44 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.44 remote-as 65142
   neighbor 192.168.101.44 description leaf44_Loopback0
   neighbor 192.168.101.45 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.45 remote-as 65144
   neighbor 192.168.101.45 description leaf45_Loopback0
   neighbor 192.168.101.46 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.46 remote-as 65144
   neighbor 192.168.101.46 description leaf46_Loopback0
   neighbor 192.168.101.47 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.47 remote-as 65146
   neighbor 192.168.101.47 description leaf47_Loopback0
   neighbor 192.168.101.48 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.48 remote-as 65146
   neighbor 192.168.101.48 description leaf48_Loopback0
   neighbor 192.168.101.49 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.49 remote-as 65148
   neighbor 192.168.101.49 description leaf49_Loopback0
   neighbor 192.168.101.50 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.50 remote-as 65148
   neighbor 192.168.101.50 description leaf50_Loopback0
   neighbor 192.168.101.91 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.91 remote-as 65190
   neighbor 192.168.101.91 description borderleaf1_Loopback0
   neighbor 192.168.101.92 peer group EVPN-OVERLAY-PEERS
   neighbor 192.168.101.92 remote-as 65191
   neighbor 192.168.101.92 description borderleaf2_Loopback0
   neighbor 192.168.108.1 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.1 remote-as 65100
   neighbor 192.168.108.1 description leaf1_Ethernet3
   neighbor 192.168.108.7 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.7 remote-as 65100
   neighbor 192.168.108.7 description leaf2_Ethernet3
   neighbor 192.168.108.13 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.13 remote-as 65102
   neighbor 192.168.108.13 description leaf3_Ethernet3
   neighbor 192.168.108.19 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.19 remote-as 65102
   neighbor 192.168.108.19 description leaf4_Ethernet3
   neighbor 192.168.108.25 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.25 remote-as 65104
   neighbor 192.168.108.25 description leaf5_Ethernet3
   neighbor 192.168.108.31 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.31 remote-as 65104
   neighbor 192.168.108.31 description leaf6_Ethernet3
   neighbor 192.168.108.37 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.37 remote-as 65106
   neighbor 192.168.108.37 description leaf7_Ethernet3
   neighbor 192.168.108.43 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.43 remote-as 65106
   neighbor 192.168.108.43 description leaf8_Ethernet3
   neighbor 192.168.108.49 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.49 remote-as 65108
   neighbor 192.168.108.49 description leaf9_Ethernet3
   neighbor 192.168.108.55 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.55 remote-as 65108
   neighbor 192.168.108.55 description leaf10_Ethernet3
   neighbor 192.168.108.61 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.61 remote-as 65110
   neighbor 192.168.108.61 description leaf11_Ethernet3
   neighbor 192.168.108.67 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.67 remote-as 65110
   neighbor 192.168.108.67 description leaf12_Ethernet3
   neighbor 192.168.108.73 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.73 remote-as 65112
   neighbor 192.168.108.73 description leaf13_Ethernet3
   neighbor 192.168.108.79 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.79 remote-as 65112
   neighbor 192.168.108.79 description leaf14_Ethernet3
   neighbor 192.168.108.85 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.85 remote-as 65114
   neighbor 192.168.108.85 description leaf15_Ethernet3
   neighbor 192.168.108.91 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.91 remote-as 65114
   neighbor 192.168.108.91 description leaf16_Ethernet3
   neighbor 192.168.108.97 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.97 remote-as 65116
   neighbor 192.168.108.97 description leaf17_Ethernet3
   neighbor 192.168.108.103 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.103 remote-as 65116
   neighbor 192.168.108.103 description leaf18_Ethernet3
   neighbor 192.168.108.109 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.109 remote-as 65118
   neighbor 192.168.108.109 description leaf19_Ethernet3
   neighbor 192.168.108.115 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.115 remote-as 65118
   neighbor 192.168.108.115 description leaf20_Ethernet3
   neighbor 192.168.108.121 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.121 remote-as 65120
   neighbor 192.168.108.121 description leaf21_Ethernet3
   neighbor 192.168.108.127 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.127 remote-as 65120
   neighbor 192.168.108.127 description leaf22_Ethernet3
   neighbor 192.168.108.133 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.133 remote-as 65122
   neighbor 192.168.108.133 description leaf23_Ethernet3
   neighbor 192.168.108.139 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.139 remote-as 65122
   neighbor 192.168.108.139 description leaf24_Ethernet3
   neighbor 192.168.108.145 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.145 remote-as 65124
   neighbor 192.168.108.145 description leaf25_Ethernet3
   neighbor 192.168.108.151 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.151 remote-as 65124
   neighbor 192.168.108.151 description leaf26_Ethernet3
   neighbor 192.168.108.157 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.157 remote-as 65126
   neighbor 192.168.108.157 description leaf27_Ethernet3
   neighbor 192.168.108.163 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.163 remote-as 65126
   neighbor 192.168.108.163 description leaf28_Ethernet3
   neighbor 192.168.108.169 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.169 remote-as 65128
   neighbor 192.168.108.169 description leaf29_Ethernet3
   neighbor 192.168.108.175 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.175 remote-as 65128
   neighbor 192.168.108.175 description leaf30_Ethernet3
   neighbor 192.168.108.181 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.181 remote-as 65130
   neighbor 192.168.108.181 description leaf31_Ethernet3
   neighbor 192.168.108.187 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.187 remote-as 65130
   neighbor 192.168.108.187 description leaf32_Ethernet3
   neighbor 192.168.108.193 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.193 remote-as 65132
   neighbor 192.168.108.193 description leaf33_Ethernet3
   neighbor 192.168.108.199 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.199 remote-as 65132
   neighbor 192.168.108.199 description leaf34_Ethernet3
   neighbor 192.168.108.205 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.205 remote-as 65134
   neighbor 192.168.108.205 description leaf35_Ethernet3
   neighbor 192.168.108.211 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.211 remote-as 65134
   neighbor 192.168.108.211 description leaf36_Ethernet3
   neighbor 192.168.108.217 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.217 remote-as 65136
   neighbor 192.168.108.217 description leaf37_Ethernet3
   neighbor 192.168.108.223 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.223 remote-as 65136
   neighbor 192.168.108.223 description leaf38_Ethernet3
   neighbor 192.168.108.229 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.229 remote-as 65138
   neighbor 192.168.108.229 description leaf39_Ethernet3
   neighbor 192.168.108.235 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.235 remote-as 65138
   neighbor 192.168.108.235 description leaf40_Ethernet3
   neighbor 192.168.108.241 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.241 remote-as 65140
   neighbor 192.168.108.241 description leaf41_Ethernet3
   neighbor 192.168.108.247 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.247 remote-as 65140
   neighbor 192.168.108.247 description leaf42_Ethernet3
   neighbor 192.168.108.253 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.108.253 remote-as 65142
   neighbor 192.168.108.253 description leaf43_Ethernet3
   neighbor 192.168.109.3 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.3 remote-as 65142
   neighbor 192.168.109.3 description leaf44_Ethernet3
   neighbor 192.168.109.9 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.9 remote-as 65144
   neighbor 192.168.109.9 description leaf45_Ethernet3
   neighbor 192.168.109.15 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.15 remote-as 65144
   neighbor 192.168.109.15 description leaf46_Ethernet3
   neighbor 192.168.109.21 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.21 remote-as 65146
   neighbor 192.168.109.21 description leaf47_Ethernet3
   neighbor 192.168.109.27 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.27 remote-as 65146
   neighbor 192.168.109.27 description leaf48_Ethernet3
   neighbor 192.168.109.33 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.33 remote-as 65148
   neighbor 192.168.109.33 description leaf49_Ethernet3
   neighbor 192.168.109.39 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.109.39 remote-as 65148
   neighbor 192.168.109.39 description leaf50_Ethernet3
   neighbor 192.168.110.29 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.110.29 remote-as 65190
   neighbor 192.168.110.29 description borderleaf1_Ethernet3
   neighbor 192.168.110.35 peer group IPv4-UNDERLAY-PEERS
   neighbor 192.168.110.35 remote-as 65191
   neighbor 192.168.110.35 description borderleaf2_Ethernet3
   redistribute connected route-map RM-CONN-2-BGP
   !
   address-family evpn
      neighbor EVPN-OVERLAY-PEERS activate
   !
   address-family ipv4
      no neighbor EVPN-OVERLAY-PEERS activate
      neighbor IPv4-UNDERLAY-PEERS activate
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

## Filters

### Prefix-lists

#### Prefix-lists Summary

##### PL-LOOPBACKS-EVPN-OVERLAY

| Sequence | Action |
| -------- | ------ |
| 10 | permit 192.168.101.0/24 eq 32 |

#### Prefix-lists Device Configuration

```eos
!
ip prefix-list PL-LOOPBACKS-EVPN-OVERLAY
   seq 10 permit 192.168.101.0/24 eq 32
```

### Route-maps

#### Route-maps Summary

##### RM-CONN-2-BGP

| Sequence | Type | Match | Set | Sub-Route-Map | Continue |
| -------- | ---- | ----- | --- | ------------- | -------- |
| 10 | permit | ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY | - | - | - |

#### Route-maps Device Configuration

```eos
!
route-map RM-CONN-2-BGP permit 10
   match ip address prefix-list PL-LOOPBACKS-EVPN-OVERLAY
```

## VRF Instances

### VRF Instances Summary

| VRF Name | IP Routing |
| -------- | ---------- |
| MGMT | disabled |

### VRF Instances Device Configuration

```eos
!
vrf instance MGMT
```
