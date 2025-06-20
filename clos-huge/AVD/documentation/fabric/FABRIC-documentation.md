# FABRIC

## Table of Contents

- [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Switches with inband Management IP](#fabric-switches-with-inband-management-ip)
- [Fabric Topology](#fabric-topology)
- [Fabric IP Allocation](#fabric-ip-allocation)
  - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
  - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
  - [Loopback Interfaces (BGP EVPN Peering)](#loopback-interfaces-bgp-evpn-peering)
  - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
  - [VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-vteps-only)
  - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

## Fabric Switches and Management IP

| POD | Type | Node | Management IP | Platform | Provisioned in CloudVision | Serial Number |
| --- | ---- | ---- | ------------- | -------- | -------------------------- | ------------- |
| FABRIC | l3leaf | borderleaf1 | 172.20.20.91/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | borderleaf2 | 172.20.20.92/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf1 | 172.20.20.11/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf2 | 172.20.20.12/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf3 | 172.20.20.13/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf4 | 172.20.20.14/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf5 | 172.20.20.15/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf6 | 172.20.20.16/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf7 | 172.20.20.17/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf8 | 172.20.20.18/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf9 | 172.20.20.19/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf10 | 172.20.20.20/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf11 | 172.20.20.21/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf12 | 172.20.20.22/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf13 | 172.20.20.23/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf14 | 172.20.20.24/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf15 | 172.20.20.25/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf16 | 172.20.20.26/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf17 | 172.20.20.27/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf18 | 172.20.20.28/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf19 | 172.20.20.29/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf20 | 172.20.20.30/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf21 | 172.20.20.31/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf22 | 172.20.20.32/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf23 | 172.20.20.33/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf24 | 172.20.20.34/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf25 | 172.20.20.35/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf26 | 172.20.20.36/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf27 | 172.20.20.37/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf28 | 172.20.20.38/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf29 | 172.20.20.39/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf30 | 172.20.20.40/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf31 | 172.20.20.41/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf32 | 172.20.20.42/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf33 | 172.20.20.43/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf34 | 172.20.20.44/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf35 | 172.20.20.45/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf36 | 172.20.20.46/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf37 | 172.20.20.47/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf38 | 172.20.20.48/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf39 | 172.20.20.49/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf40 | 172.20.20.50/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf41 | 172.20.20.51/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf42 | 172.20.20.52/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf43 | 172.20.20.53/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf44 | 172.20.20.54/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf45 | 172.20.20.55/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf46 | 172.20.20.56/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf47 | 172.20.20.57/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf48 | 172.20.20.58/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf49 | 172.20.20.59/24 | cEOS-lab | Provisioned | - |
| FABRIC | l3leaf | leaf50 | 172.20.20.60/24 | cEOS-lab | Provisioned | - |
| FABRIC | spine | spine1 | 172.20.20.101/24 | cEOS-lab | Provisioned | - |
| FABRIC | spine | spine2 | 172.20.20.102/24 | cEOS-lab | Provisioned | - |
| FABRIC | spine | spine3 | 172.20.20.103/24 | cEOS-lab | Provisioned | - |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

### Fabric Switches with inband Management IP

| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

## Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| l3leaf | borderleaf1 | Ethernet3 | spine | spine1 | Ethernet52 |
| l3leaf | borderleaf1 | Ethernet4 | spine | spine2 | Ethernet52 |
| l3leaf | borderleaf1 | Ethernet5 | spine | spine3 | Ethernet52 |
| l3leaf | borderleaf2 | Ethernet3 | spine | spine1 | Ethernet53 |
| l3leaf | borderleaf2 | Ethernet4 | spine | spine2 | Ethernet53 |
| l3leaf | borderleaf2 | Ethernet5 | spine | spine3 | Ethernet53 |
| l3leaf | leaf1 | Ethernet1 | mlag_peer | leaf2 | Ethernet1 |
| l3leaf | leaf1 | Ethernet2 | mlag_peer | leaf2 | Ethernet2 |
| l3leaf | leaf1 | Ethernet3 | spine | spine1 | Ethernet2 |
| l3leaf | leaf1 | Ethernet4 | spine | spine2 | Ethernet2 |
| l3leaf | leaf1 | Ethernet5 | spine | spine3 | Ethernet2 |
| l3leaf | leaf2 | Ethernet3 | spine | spine1 | Ethernet3 |
| l3leaf | leaf2 | Ethernet4 | spine | spine2 | Ethernet3 |
| l3leaf | leaf2 | Ethernet5 | spine | spine3 | Ethernet3 |
| l3leaf | leaf3 | Ethernet1 | mlag_peer | leaf4 | Ethernet1 |
| l3leaf | leaf3 | Ethernet2 | mlag_peer | leaf4 | Ethernet2 |
| l3leaf | leaf3 | Ethernet3 | spine | spine1 | Ethernet4 |
| l3leaf | leaf3 | Ethernet4 | spine | spine2 | Ethernet4 |
| l3leaf | leaf3 | Ethernet5 | spine | spine3 | Ethernet4 |
| l3leaf | leaf4 | Ethernet3 | spine | spine1 | Ethernet5 |
| l3leaf | leaf4 | Ethernet4 | spine | spine2 | Ethernet5 |
| l3leaf | leaf4 | Ethernet5 | spine | spine3 | Ethernet5 |
| l3leaf | leaf5 | Ethernet1 | mlag_peer | leaf6 | Ethernet1 |
| l3leaf | leaf5 | Ethernet2 | mlag_peer | leaf6 | Ethernet2 |
| l3leaf | leaf5 | Ethernet3 | spine | spine1 | Ethernet6 |
| l3leaf | leaf5 | Ethernet4 | spine | spine2 | Ethernet6 |
| l3leaf | leaf5 | Ethernet5 | spine | spine3 | Ethernet6 |
| l3leaf | leaf6 | Ethernet3 | spine | spine1 | Ethernet7 |
| l3leaf | leaf6 | Ethernet4 | spine | spine2 | Ethernet7 |
| l3leaf | leaf6 | Ethernet5 | spine | spine3 | Ethernet7 |
| l3leaf | leaf7 | Ethernet1 | mlag_peer | leaf8 | Ethernet1 |
| l3leaf | leaf7 | Ethernet2 | mlag_peer | leaf8 | Ethernet2 |
| l3leaf | leaf7 | Ethernet3 | spine | spine1 | Ethernet8 |
| l3leaf | leaf7 | Ethernet4 | spine | spine2 | Ethernet8 |
| l3leaf | leaf7 | Ethernet5 | spine | spine3 | Ethernet8 |
| l3leaf | leaf8 | Ethernet3 | spine | spine1 | Ethernet9 |
| l3leaf | leaf8 | Ethernet4 | spine | spine2 | Ethernet9 |
| l3leaf | leaf8 | Ethernet5 | spine | spine3 | Ethernet9 |
| l3leaf | leaf9 | Ethernet1 | mlag_peer | leaf10 | Ethernet1 |
| l3leaf | leaf9 | Ethernet2 | mlag_peer | leaf10 | Ethernet2 |
| l3leaf | leaf9 | Ethernet3 | spine | spine1 | Ethernet10 |
| l3leaf | leaf9 | Ethernet4 | spine | spine2 | Ethernet10 |
| l3leaf | leaf9 | Ethernet5 | spine | spine3 | Ethernet10 |
| l3leaf | leaf10 | Ethernet3 | spine | spine1 | Ethernet11 |
| l3leaf | leaf10 | Ethernet4 | spine | spine2 | Ethernet11 |
| l3leaf | leaf10 | Ethernet5 | spine | spine3 | Ethernet11 |
| l3leaf | leaf11 | Ethernet1 | mlag_peer | leaf12 | Ethernet1 |
| l3leaf | leaf11 | Ethernet2 | mlag_peer | leaf12 | Ethernet2 |
| l3leaf | leaf11 | Ethernet3 | spine | spine1 | Ethernet12 |
| l3leaf | leaf11 | Ethernet4 | spine | spine2 | Ethernet12 |
| l3leaf | leaf11 | Ethernet5 | spine | spine3 | Ethernet12 |
| l3leaf | leaf12 | Ethernet3 | spine | spine1 | Ethernet13 |
| l3leaf | leaf12 | Ethernet4 | spine | spine2 | Ethernet13 |
| l3leaf | leaf12 | Ethernet5 | spine | spine3 | Ethernet13 |
| l3leaf | leaf13 | Ethernet1 | mlag_peer | leaf14 | Ethernet1 |
| l3leaf | leaf13 | Ethernet2 | mlag_peer | leaf14 | Ethernet2 |
| l3leaf | leaf13 | Ethernet3 | spine | spine1 | Ethernet14 |
| l3leaf | leaf13 | Ethernet4 | spine | spine2 | Ethernet14 |
| l3leaf | leaf13 | Ethernet5 | spine | spine3 | Ethernet14 |
| l3leaf | leaf14 | Ethernet3 | spine | spine1 | Ethernet15 |
| l3leaf | leaf14 | Ethernet4 | spine | spine2 | Ethernet15 |
| l3leaf | leaf14 | Ethernet5 | spine | spine3 | Ethernet15 |
| l3leaf | leaf15 | Ethernet1 | mlag_peer | leaf16 | Ethernet1 |
| l3leaf | leaf15 | Ethernet2 | mlag_peer | leaf16 | Ethernet2 |
| l3leaf | leaf15 | Ethernet3 | spine | spine1 | Ethernet16 |
| l3leaf | leaf15 | Ethernet4 | spine | spine2 | Ethernet16 |
| l3leaf | leaf15 | Ethernet5 | spine | spine3 | Ethernet16 |
| l3leaf | leaf16 | Ethernet3 | spine | spine1 | Ethernet17 |
| l3leaf | leaf16 | Ethernet4 | spine | spine2 | Ethernet17 |
| l3leaf | leaf16 | Ethernet5 | spine | spine3 | Ethernet17 |
| l3leaf | leaf17 | Ethernet1 | mlag_peer | leaf18 | Ethernet1 |
| l3leaf | leaf17 | Ethernet2 | mlag_peer | leaf18 | Ethernet2 |
| l3leaf | leaf17 | Ethernet3 | spine | spine1 | Ethernet18 |
| l3leaf | leaf17 | Ethernet4 | spine | spine2 | Ethernet18 |
| l3leaf | leaf17 | Ethernet5 | spine | spine3 | Ethernet18 |
| l3leaf | leaf18 | Ethernet3 | spine | spine1 | Ethernet19 |
| l3leaf | leaf18 | Ethernet4 | spine | spine2 | Ethernet19 |
| l3leaf | leaf18 | Ethernet5 | spine | spine3 | Ethernet19 |
| l3leaf | leaf19 | Ethernet1 | mlag_peer | leaf20 | Ethernet1 |
| l3leaf | leaf19 | Ethernet2 | mlag_peer | leaf20 | Ethernet2 |
| l3leaf | leaf19 | Ethernet3 | spine | spine1 | Ethernet20 |
| l3leaf | leaf19 | Ethernet4 | spine | spine2 | Ethernet20 |
| l3leaf | leaf19 | Ethernet5 | spine | spine3 | Ethernet20 |
| l3leaf | leaf20 | Ethernet3 | spine | spine1 | Ethernet21 |
| l3leaf | leaf20 | Ethernet4 | spine | spine2 | Ethernet21 |
| l3leaf | leaf20 | Ethernet5 | spine | spine3 | Ethernet21 |
| l3leaf | leaf21 | Ethernet1 | mlag_peer | leaf22 | Ethernet1 |
| l3leaf | leaf21 | Ethernet2 | mlag_peer | leaf22 | Ethernet2 |
| l3leaf | leaf21 | Ethernet3 | spine | spine1 | Ethernet22 |
| l3leaf | leaf21 | Ethernet4 | spine | spine2 | Ethernet22 |
| l3leaf | leaf21 | Ethernet5 | spine | spine3 | Ethernet22 |
| l3leaf | leaf22 | Ethernet3 | spine | spine1 | Ethernet23 |
| l3leaf | leaf22 | Ethernet4 | spine | spine2 | Ethernet23 |
| l3leaf | leaf22 | Ethernet5 | spine | spine3 | Ethernet23 |
| l3leaf | leaf23 | Ethernet1 | mlag_peer | leaf24 | Ethernet1 |
| l3leaf | leaf23 | Ethernet2 | mlag_peer | leaf24 | Ethernet2 |
| l3leaf | leaf23 | Ethernet3 | spine | spine1 | Ethernet24 |
| l3leaf | leaf23 | Ethernet4 | spine | spine2 | Ethernet24 |
| l3leaf | leaf23 | Ethernet5 | spine | spine3 | Ethernet24 |
| l3leaf | leaf24 | Ethernet3 | spine | spine1 | Ethernet25 |
| l3leaf | leaf24 | Ethernet4 | spine | spine2 | Ethernet25 |
| l3leaf | leaf24 | Ethernet5 | spine | spine3 | Ethernet25 |
| l3leaf | leaf25 | Ethernet1 | mlag_peer | leaf26 | Ethernet1 |
| l3leaf | leaf25 | Ethernet2 | mlag_peer | leaf26 | Ethernet2 |
| l3leaf | leaf25 | Ethernet3 | spine | spine1 | Ethernet26 |
| l3leaf | leaf25 | Ethernet4 | spine | spine2 | Ethernet26 |
| l3leaf | leaf25 | Ethernet5 | spine | spine3 | Ethernet26 |
| l3leaf | leaf26 | Ethernet3 | spine | spine1 | Ethernet27 |
| l3leaf | leaf26 | Ethernet4 | spine | spine2 | Ethernet27 |
| l3leaf | leaf26 | Ethernet5 | spine | spine3 | Ethernet27 |
| l3leaf | leaf27 | Ethernet1 | mlag_peer | leaf28 | Ethernet1 |
| l3leaf | leaf27 | Ethernet2 | mlag_peer | leaf28 | Ethernet2 |
| l3leaf | leaf27 | Ethernet3 | spine | spine1 | Ethernet28 |
| l3leaf | leaf27 | Ethernet4 | spine | spine2 | Ethernet28 |
| l3leaf | leaf27 | Ethernet5 | spine | spine3 | Ethernet28 |
| l3leaf | leaf28 | Ethernet3 | spine | spine1 | Ethernet29 |
| l3leaf | leaf28 | Ethernet4 | spine | spine2 | Ethernet29 |
| l3leaf | leaf28 | Ethernet5 | spine | spine3 | Ethernet29 |
| l3leaf | leaf29 | Ethernet1 | mlag_peer | leaf30 | Ethernet1 |
| l3leaf | leaf29 | Ethernet2 | mlag_peer | leaf30 | Ethernet2 |
| l3leaf | leaf29 | Ethernet3 | spine | spine1 | Ethernet30 |
| l3leaf | leaf29 | Ethernet4 | spine | spine2 | Ethernet30 |
| l3leaf | leaf29 | Ethernet5 | spine | spine3 | Ethernet30 |
| l3leaf | leaf30 | Ethernet3 | spine | spine1 | Ethernet31 |
| l3leaf | leaf30 | Ethernet4 | spine | spine2 | Ethernet31 |
| l3leaf | leaf30 | Ethernet5 | spine | spine3 | Ethernet31 |
| l3leaf | leaf31 | Ethernet1 | mlag_peer | leaf32 | Ethernet1 |
| l3leaf | leaf31 | Ethernet2 | mlag_peer | leaf32 | Ethernet2 |
| l3leaf | leaf31 | Ethernet3 | spine | spine1 | Ethernet32 |
| l3leaf | leaf31 | Ethernet4 | spine | spine2 | Ethernet32 |
| l3leaf | leaf31 | Ethernet5 | spine | spine3 | Ethernet32 |
| l3leaf | leaf32 | Ethernet3 | spine | spine1 | Ethernet33 |
| l3leaf | leaf32 | Ethernet4 | spine | spine2 | Ethernet33 |
| l3leaf | leaf32 | Ethernet5 | spine | spine3 | Ethernet33 |
| l3leaf | leaf33 | Ethernet1 | mlag_peer | leaf34 | Ethernet1 |
| l3leaf | leaf33 | Ethernet2 | mlag_peer | leaf34 | Ethernet2 |
| l3leaf | leaf33 | Ethernet3 | spine | spine1 | Ethernet34 |
| l3leaf | leaf33 | Ethernet4 | spine | spine2 | Ethernet34 |
| l3leaf | leaf33 | Ethernet5 | spine | spine3 | Ethernet34 |
| l3leaf | leaf34 | Ethernet3 | spine | spine1 | Ethernet35 |
| l3leaf | leaf34 | Ethernet4 | spine | spine2 | Ethernet35 |
| l3leaf | leaf34 | Ethernet5 | spine | spine3 | Ethernet35 |
| l3leaf | leaf35 | Ethernet1 | mlag_peer | leaf36 | Ethernet1 |
| l3leaf | leaf35 | Ethernet2 | mlag_peer | leaf36 | Ethernet2 |
| l3leaf | leaf35 | Ethernet3 | spine | spine1 | Ethernet36 |
| l3leaf | leaf35 | Ethernet4 | spine | spine2 | Ethernet36 |
| l3leaf | leaf35 | Ethernet5 | spine | spine3 | Ethernet36 |
| l3leaf | leaf36 | Ethernet3 | spine | spine1 | Ethernet37 |
| l3leaf | leaf36 | Ethernet4 | spine | spine2 | Ethernet37 |
| l3leaf | leaf36 | Ethernet5 | spine | spine3 | Ethernet37 |
| l3leaf | leaf37 | Ethernet1 | mlag_peer | leaf38 | Ethernet1 |
| l3leaf | leaf37 | Ethernet2 | mlag_peer | leaf38 | Ethernet2 |
| l3leaf | leaf37 | Ethernet3 | spine | spine1 | Ethernet38 |
| l3leaf | leaf37 | Ethernet4 | spine | spine2 | Ethernet38 |
| l3leaf | leaf37 | Ethernet5 | spine | spine3 | Ethernet38 |
| l3leaf | leaf38 | Ethernet3 | spine | spine1 | Ethernet39 |
| l3leaf | leaf38 | Ethernet4 | spine | spine2 | Ethernet39 |
| l3leaf | leaf38 | Ethernet5 | spine | spine3 | Ethernet39 |
| l3leaf | leaf39 | Ethernet1 | mlag_peer | leaf40 | Ethernet1 |
| l3leaf | leaf39 | Ethernet2 | mlag_peer | leaf40 | Ethernet2 |
| l3leaf | leaf39 | Ethernet3 | spine | spine1 | Ethernet40 |
| l3leaf | leaf39 | Ethernet4 | spine | spine2 | Ethernet40 |
| l3leaf | leaf39 | Ethernet5 | spine | spine3 | Ethernet40 |
| l3leaf | leaf40 | Ethernet3 | spine | spine1 | Ethernet41 |
| l3leaf | leaf40 | Ethernet4 | spine | spine2 | Ethernet41 |
| l3leaf | leaf40 | Ethernet5 | spine | spine3 | Ethernet41 |
| l3leaf | leaf41 | Ethernet1 | mlag_peer | leaf42 | Ethernet1 |
| l3leaf | leaf41 | Ethernet2 | mlag_peer | leaf42 | Ethernet2 |
| l3leaf | leaf41 | Ethernet3 | spine | spine1 | Ethernet42 |
| l3leaf | leaf41 | Ethernet4 | spine | spine2 | Ethernet42 |
| l3leaf | leaf41 | Ethernet5 | spine | spine3 | Ethernet42 |
| l3leaf | leaf42 | Ethernet3 | spine | spine1 | Ethernet43 |
| l3leaf | leaf42 | Ethernet4 | spine | spine2 | Ethernet43 |
| l3leaf | leaf42 | Ethernet5 | spine | spine3 | Ethernet43 |
| l3leaf | leaf43 | Ethernet1 | mlag_peer | leaf44 | Ethernet1 |
| l3leaf | leaf43 | Ethernet2 | mlag_peer | leaf44 | Ethernet2 |
| l3leaf | leaf43 | Ethernet3 | spine | spine1 | Ethernet44 |
| l3leaf | leaf43 | Ethernet4 | spine | spine2 | Ethernet44 |
| l3leaf | leaf43 | Ethernet5 | spine | spine3 | Ethernet44 |
| l3leaf | leaf44 | Ethernet3 | spine | spine1 | Ethernet45 |
| l3leaf | leaf44 | Ethernet4 | spine | spine2 | Ethernet45 |
| l3leaf | leaf44 | Ethernet5 | spine | spine3 | Ethernet45 |
| l3leaf | leaf45 | Ethernet1 | mlag_peer | leaf46 | Ethernet1 |
| l3leaf | leaf45 | Ethernet2 | mlag_peer | leaf46 | Ethernet2 |
| l3leaf | leaf45 | Ethernet3 | spine | spine1 | Ethernet46 |
| l3leaf | leaf45 | Ethernet4 | spine | spine2 | Ethernet46 |
| l3leaf | leaf45 | Ethernet5 | spine | spine3 | Ethernet46 |
| l3leaf | leaf46 | Ethernet3 | spine | spine1 | Ethernet47 |
| l3leaf | leaf46 | Ethernet4 | spine | spine2 | Ethernet47 |
| l3leaf | leaf46 | Ethernet5 | spine | spine3 | Ethernet47 |
| l3leaf | leaf47 | Ethernet1 | mlag_peer | leaf48 | Ethernet1 |
| l3leaf | leaf47 | Ethernet2 | mlag_peer | leaf48 | Ethernet2 |
| l3leaf | leaf47 | Ethernet3 | spine | spine1 | Ethernet48 |
| l3leaf | leaf47 | Ethernet4 | spine | spine2 | Ethernet48 |
| l3leaf | leaf47 | Ethernet5 | spine | spine3 | Ethernet48 |
| l3leaf | leaf48 | Ethernet3 | spine | spine1 | Ethernet49 |
| l3leaf | leaf48 | Ethernet4 | spine | spine2 | Ethernet49 |
| l3leaf | leaf48 | Ethernet5 | spine | spine3 | Ethernet49 |
| l3leaf | leaf49 | Ethernet1 | mlag_peer | leaf50 | Ethernet1 |
| l3leaf | leaf49 | Ethernet2 | mlag_peer | leaf50 | Ethernet2 |
| l3leaf | leaf49 | Ethernet3 | spine | spine1 | Ethernet50 |
| l3leaf | leaf49 | Ethernet4 | spine | spine2 | Ethernet50 |
| l3leaf | leaf49 | Ethernet5 | spine | spine3 | Ethernet50 |
| l3leaf | leaf50 | Ethernet3 | spine | spine1 | Ethernet51 |
| l3leaf | leaf50 | Ethernet4 | spine | spine2 | Ethernet51 |
| l3leaf | leaf50 | Ethernet5 | spine | spine3 | Ethernet51 |

## Fabric IP Allocation

### Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |
| 192.168.108.0/22 | 1024 | 312 | 30.47 % |

### Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| borderleaf1 | Ethernet3 | 192.168.110.29/31 | spine1 | Ethernet52 | 192.168.110.28/31 |
| borderleaf1 | Ethernet4 | 192.168.110.31/31 | spine2 | Ethernet52 | 192.168.110.30/31 |
| borderleaf1 | Ethernet5 | 192.168.110.33/31 | spine3 | Ethernet52 | 192.168.110.32/31 |
| borderleaf2 | Ethernet3 | 192.168.110.35/31 | spine1 | Ethernet53 | 192.168.110.34/31 |
| borderleaf2 | Ethernet4 | 192.168.110.37/31 | spine2 | Ethernet53 | 192.168.110.36/31 |
| borderleaf2 | Ethernet5 | 192.168.110.39/31 | spine3 | Ethernet53 | 192.168.110.38/31 |
| leaf1 | Ethernet3 | 192.168.108.1/31 | spine1 | Ethernet2 | 192.168.108.0/31 |
| leaf1 | Ethernet4 | 192.168.108.3/31 | spine2 | Ethernet2 | 192.168.108.2/31 |
| leaf1 | Ethernet5 | 192.168.108.5/31 | spine3 | Ethernet2 | 192.168.108.4/31 |
| leaf2 | Ethernet3 | 192.168.108.7/31 | spine1 | Ethernet3 | 192.168.108.6/31 |
| leaf2 | Ethernet4 | 192.168.108.9/31 | spine2 | Ethernet3 | 192.168.108.8/31 |
| leaf2 | Ethernet5 | 192.168.108.11/31 | spine3 | Ethernet3 | 192.168.108.10/31 |
| leaf3 | Ethernet3 | 192.168.108.13/31 | spine1 | Ethernet4 | 192.168.108.12/31 |
| leaf3 | Ethernet4 | 192.168.108.15/31 | spine2 | Ethernet4 | 192.168.108.14/31 |
| leaf3 | Ethernet5 | 192.168.108.17/31 | spine3 | Ethernet4 | 192.168.108.16/31 |
| leaf4 | Ethernet3 | 192.168.108.19/31 | spine1 | Ethernet5 | 192.168.108.18/31 |
| leaf4 | Ethernet4 | 192.168.108.21/31 | spine2 | Ethernet5 | 192.168.108.20/31 |
| leaf4 | Ethernet5 | 192.168.108.23/31 | spine3 | Ethernet5 | 192.168.108.22/31 |
| leaf5 | Ethernet3 | 192.168.108.25/31 | spine1 | Ethernet6 | 192.168.108.24/31 |
| leaf5 | Ethernet4 | 192.168.108.27/31 | spine2 | Ethernet6 | 192.168.108.26/31 |
| leaf5 | Ethernet5 | 192.168.108.29/31 | spine3 | Ethernet6 | 192.168.108.28/31 |
| leaf6 | Ethernet3 | 192.168.108.31/31 | spine1 | Ethernet7 | 192.168.108.30/31 |
| leaf6 | Ethernet4 | 192.168.108.33/31 | spine2 | Ethernet7 | 192.168.108.32/31 |
| leaf6 | Ethernet5 | 192.168.108.35/31 | spine3 | Ethernet7 | 192.168.108.34/31 |
| leaf7 | Ethernet3 | 192.168.108.37/31 | spine1 | Ethernet8 | 192.168.108.36/31 |
| leaf7 | Ethernet4 | 192.168.108.39/31 | spine2 | Ethernet8 | 192.168.108.38/31 |
| leaf7 | Ethernet5 | 192.168.108.41/31 | spine3 | Ethernet8 | 192.168.108.40/31 |
| leaf8 | Ethernet3 | 192.168.108.43/31 | spine1 | Ethernet9 | 192.168.108.42/31 |
| leaf8 | Ethernet4 | 192.168.108.45/31 | spine2 | Ethernet9 | 192.168.108.44/31 |
| leaf8 | Ethernet5 | 192.168.108.47/31 | spine3 | Ethernet9 | 192.168.108.46/31 |
| leaf9 | Ethernet3 | 192.168.108.49/31 | spine1 | Ethernet10 | 192.168.108.48/31 |
| leaf9 | Ethernet4 | 192.168.108.51/31 | spine2 | Ethernet10 | 192.168.108.50/31 |
| leaf9 | Ethernet5 | 192.168.108.53/31 | spine3 | Ethernet10 | 192.168.108.52/31 |
| leaf10 | Ethernet3 | 192.168.108.55/31 | spine1 | Ethernet11 | 192.168.108.54/31 |
| leaf10 | Ethernet4 | 192.168.108.57/31 | spine2 | Ethernet11 | 192.168.108.56/31 |
| leaf10 | Ethernet5 | 192.168.108.59/31 | spine3 | Ethernet11 | 192.168.108.58/31 |
| leaf11 | Ethernet3 | 192.168.108.61/31 | spine1 | Ethernet12 | 192.168.108.60/31 |
| leaf11 | Ethernet4 | 192.168.108.63/31 | spine2 | Ethernet12 | 192.168.108.62/31 |
| leaf11 | Ethernet5 | 192.168.108.65/31 | spine3 | Ethernet12 | 192.168.108.64/31 |
| leaf12 | Ethernet3 | 192.168.108.67/31 | spine1 | Ethernet13 | 192.168.108.66/31 |
| leaf12 | Ethernet4 | 192.168.108.69/31 | spine2 | Ethernet13 | 192.168.108.68/31 |
| leaf12 | Ethernet5 | 192.168.108.71/31 | spine3 | Ethernet13 | 192.168.108.70/31 |
| leaf13 | Ethernet3 | 192.168.108.73/31 | spine1 | Ethernet14 | 192.168.108.72/31 |
| leaf13 | Ethernet4 | 192.168.108.75/31 | spine2 | Ethernet14 | 192.168.108.74/31 |
| leaf13 | Ethernet5 | 192.168.108.77/31 | spine3 | Ethernet14 | 192.168.108.76/31 |
| leaf14 | Ethernet3 | 192.168.108.79/31 | spine1 | Ethernet15 | 192.168.108.78/31 |
| leaf14 | Ethernet4 | 192.168.108.81/31 | spine2 | Ethernet15 | 192.168.108.80/31 |
| leaf14 | Ethernet5 | 192.168.108.83/31 | spine3 | Ethernet15 | 192.168.108.82/31 |
| leaf15 | Ethernet3 | 192.168.108.85/31 | spine1 | Ethernet16 | 192.168.108.84/31 |
| leaf15 | Ethernet4 | 192.168.108.87/31 | spine2 | Ethernet16 | 192.168.108.86/31 |
| leaf15 | Ethernet5 | 192.168.108.89/31 | spine3 | Ethernet16 | 192.168.108.88/31 |
| leaf16 | Ethernet3 | 192.168.108.91/31 | spine1 | Ethernet17 | 192.168.108.90/31 |
| leaf16 | Ethernet4 | 192.168.108.93/31 | spine2 | Ethernet17 | 192.168.108.92/31 |
| leaf16 | Ethernet5 | 192.168.108.95/31 | spine3 | Ethernet17 | 192.168.108.94/31 |
| leaf17 | Ethernet3 | 192.168.108.97/31 | spine1 | Ethernet18 | 192.168.108.96/31 |
| leaf17 | Ethernet4 | 192.168.108.99/31 | spine2 | Ethernet18 | 192.168.108.98/31 |
| leaf17 | Ethernet5 | 192.168.108.101/31 | spine3 | Ethernet18 | 192.168.108.100/31 |
| leaf18 | Ethernet3 | 192.168.108.103/31 | spine1 | Ethernet19 | 192.168.108.102/31 |
| leaf18 | Ethernet4 | 192.168.108.105/31 | spine2 | Ethernet19 | 192.168.108.104/31 |
| leaf18 | Ethernet5 | 192.168.108.107/31 | spine3 | Ethernet19 | 192.168.108.106/31 |
| leaf19 | Ethernet3 | 192.168.108.109/31 | spine1 | Ethernet20 | 192.168.108.108/31 |
| leaf19 | Ethernet4 | 192.168.108.111/31 | spine2 | Ethernet20 | 192.168.108.110/31 |
| leaf19 | Ethernet5 | 192.168.108.113/31 | spine3 | Ethernet20 | 192.168.108.112/31 |
| leaf20 | Ethernet3 | 192.168.108.115/31 | spine1 | Ethernet21 | 192.168.108.114/31 |
| leaf20 | Ethernet4 | 192.168.108.117/31 | spine2 | Ethernet21 | 192.168.108.116/31 |
| leaf20 | Ethernet5 | 192.168.108.119/31 | spine3 | Ethernet21 | 192.168.108.118/31 |
| leaf21 | Ethernet3 | 192.168.108.121/31 | spine1 | Ethernet22 | 192.168.108.120/31 |
| leaf21 | Ethernet4 | 192.168.108.123/31 | spine2 | Ethernet22 | 192.168.108.122/31 |
| leaf21 | Ethernet5 | 192.168.108.125/31 | spine3 | Ethernet22 | 192.168.108.124/31 |
| leaf22 | Ethernet3 | 192.168.108.127/31 | spine1 | Ethernet23 | 192.168.108.126/31 |
| leaf22 | Ethernet4 | 192.168.108.129/31 | spine2 | Ethernet23 | 192.168.108.128/31 |
| leaf22 | Ethernet5 | 192.168.108.131/31 | spine3 | Ethernet23 | 192.168.108.130/31 |
| leaf23 | Ethernet3 | 192.168.108.133/31 | spine1 | Ethernet24 | 192.168.108.132/31 |
| leaf23 | Ethernet4 | 192.168.108.135/31 | spine2 | Ethernet24 | 192.168.108.134/31 |
| leaf23 | Ethernet5 | 192.168.108.137/31 | spine3 | Ethernet24 | 192.168.108.136/31 |
| leaf24 | Ethernet3 | 192.168.108.139/31 | spine1 | Ethernet25 | 192.168.108.138/31 |
| leaf24 | Ethernet4 | 192.168.108.141/31 | spine2 | Ethernet25 | 192.168.108.140/31 |
| leaf24 | Ethernet5 | 192.168.108.143/31 | spine3 | Ethernet25 | 192.168.108.142/31 |
| leaf25 | Ethernet3 | 192.168.108.145/31 | spine1 | Ethernet26 | 192.168.108.144/31 |
| leaf25 | Ethernet4 | 192.168.108.147/31 | spine2 | Ethernet26 | 192.168.108.146/31 |
| leaf25 | Ethernet5 | 192.168.108.149/31 | spine3 | Ethernet26 | 192.168.108.148/31 |
| leaf26 | Ethernet3 | 192.168.108.151/31 | spine1 | Ethernet27 | 192.168.108.150/31 |
| leaf26 | Ethernet4 | 192.168.108.153/31 | spine2 | Ethernet27 | 192.168.108.152/31 |
| leaf26 | Ethernet5 | 192.168.108.155/31 | spine3 | Ethernet27 | 192.168.108.154/31 |
| leaf27 | Ethernet3 | 192.168.108.157/31 | spine1 | Ethernet28 | 192.168.108.156/31 |
| leaf27 | Ethernet4 | 192.168.108.159/31 | spine2 | Ethernet28 | 192.168.108.158/31 |
| leaf27 | Ethernet5 | 192.168.108.161/31 | spine3 | Ethernet28 | 192.168.108.160/31 |
| leaf28 | Ethernet3 | 192.168.108.163/31 | spine1 | Ethernet29 | 192.168.108.162/31 |
| leaf28 | Ethernet4 | 192.168.108.165/31 | spine2 | Ethernet29 | 192.168.108.164/31 |
| leaf28 | Ethernet5 | 192.168.108.167/31 | spine3 | Ethernet29 | 192.168.108.166/31 |
| leaf29 | Ethernet3 | 192.168.108.169/31 | spine1 | Ethernet30 | 192.168.108.168/31 |
| leaf29 | Ethernet4 | 192.168.108.171/31 | spine2 | Ethernet30 | 192.168.108.170/31 |
| leaf29 | Ethernet5 | 192.168.108.173/31 | spine3 | Ethernet30 | 192.168.108.172/31 |
| leaf30 | Ethernet3 | 192.168.108.175/31 | spine1 | Ethernet31 | 192.168.108.174/31 |
| leaf30 | Ethernet4 | 192.168.108.177/31 | spine2 | Ethernet31 | 192.168.108.176/31 |
| leaf30 | Ethernet5 | 192.168.108.179/31 | spine3 | Ethernet31 | 192.168.108.178/31 |
| leaf31 | Ethernet3 | 192.168.108.181/31 | spine1 | Ethernet32 | 192.168.108.180/31 |
| leaf31 | Ethernet4 | 192.168.108.183/31 | spine2 | Ethernet32 | 192.168.108.182/31 |
| leaf31 | Ethernet5 | 192.168.108.185/31 | spine3 | Ethernet32 | 192.168.108.184/31 |
| leaf32 | Ethernet3 | 192.168.108.187/31 | spine1 | Ethernet33 | 192.168.108.186/31 |
| leaf32 | Ethernet4 | 192.168.108.189/31 | spine2 | Ethernet33 | 192.168.108.188/31 |
| leaf32 | Ethernet5 | 192.168.108.191/31 | spine3 | Ethernet33 | 192.168.108.190/31 |
| leaf33 | Ethernet3 | 192.168.108.193/31 | spine1 | Ethernet34 | 192.168.108.192/31 |
| leaf33 | Ethernet4 | 192.168.108.195/31 | spine2 | Ethernet34 | 192.168.108.194/31 |
| leaf33 | Ethernet5 | 192.168.108.197/31 | spine3 | Ethernet34 | 192.168.108.196/31 |
| leaf34 | Ethernet3 | 192.168.108.199/31 | spine1 | Ethernet35 | 192.168.108.198/31 |
| leaf34 | Ethernet4 | 192.168.108.201/31 | spine2 | Ethernet35 | 192.168.108.200/31 |
| leaf34 | Ethernet5 | 192.168.108.203/31 | spine3 | Ethernet35 | 192.168.108.202/31 |
| leaf35 | Ethernet3 | 192.168.108.205/31 | spine1 | Ethernet36 | 192.168.108.204/31 |
| leaf35 | Ethernet4 | 192.168.108.207/31 | spine2 | Ethernet36 | 192.168.108.206/31 |
| leaf35 | Ethernet5 | 192.168.108.209/31 | spine3 | Ethernet36 | 192.168.108.208/31 |
| leaf36 | Ethernet3 | 192.168.108.211/31 | spine1 | Ethernet37 | 192.168.108.210/31 |
| leaf36 | Ethernet4 | 192.168.108.213/31 | spine2 | Ethernet37 | 192.168.108.212/31 |
| leaf36 | Ethernet5 | 192.168.108.215/31 | spine3 | Ethernet37 | 192.168.108.214/31 |
| leaf37 | Ethernet3 | 192.168.108.217/31 | spine1 | Ethernet38 | 192.168.108.216/31 |
| leaf37 | Ethernet4 | 192.168.108.219/31 | spine2 | Ethernet38 | 192.168.108.218/31 |
| leaf37 | Ethernet5 | 192.168.108.221/31 | spine3 | Ethernet38 | 192.168.108.220/31 |
| leaf38 | Ethernet3 | 192.168.108.223/31 | spine1 | Ethernet39 | 192.168.108.222/31 |
| leaf38 | Ethernet4 | 192.168.108.225/31 | spine2 | Ethernet39 | 192.168.108.224/31 |
| leaf38 | Ethernet5 | 192.168.108.227/31 | spine3 | Ethernet39 | 192.168.108.226/31 |
| leaf39 | Ethernet3 | 192.168.108.229/31 | spine1 | Ethernet40 | 192.168.108.228/31 |
| leaf39 | Ethernet4 | 192.168.108.231/31 | spine2 | Ethernet40 | 192.168.108.230/31 |
| leaf39 | Ethernet5 | 192.168.108.233/31 | spine3 | Ethernet40 | 192.168.108.232/31 |
| leaf40 | Ethernet3 | 192.168.108.235/31 | spine1 | Ethernet41 | 192.168.108.234/31 |
| leaf40 | Ethernet4 | 192.168.108.237/31 | spine2 | Ethernet41 | 192.168.108.236/31 |
| leaf40 | Ethernet5 | 192.168.108.239/31 | spine3 | Ethernet41 | 192.168.108.238/31 |
| leaf41 | Ethernet3 | 192.168.108.241/31 | spine1 | Ethernet42 | 192.168.108.240/31 |
| leaf41 | Ethernet4 | 192.168.108.243/31 | spine2 | Ethernet42 | 192.168.108.242/31 |
| leaf41 | Ethernet5 | 192.168.108.245/31 | spine3 | Ethernet42 | 192.168.108.244/31 |
| leaf42 | Ethernet3 | 192.168.108.247/31 | spine1 | Ethernet43 | 192.168.108.246/31 |
| leaf42 | Ethernet4 | 192.168.108.249/31 | spine2 | Ethernet43 | 192.168.108.248/31 |
| leaf42 | Ethernet5 | 192.168.108.251/31 | spine3 | Ethernet43 | 192.168.108.250/31 |
| leaf43 | Ethernet3 | 192.168.108.253/31 | spine1 | Ethernet44 | 192.168.108.252/31 |
| leaf43 | Ethernet4 | 192.168.108.255/31 | spine2 | Ethernet44 | 192.168.108.254/31 |
| leaf43 | Ethernet5 | 192.168.109.1/31 | spine3 | Ethernet44 | 192.168.109.0/31 |
| leaf44 | Ethernet3 | 192.168.109.3/31 | spine1 | Ethernet45 | 192.168.109.2/31 |
| leaf44 | Ethernet4 | 192.168.109.5/31 | spine2 | Ethernet45 | 192.168.109.4/31 |
| leaf44 | Ethernet5 | 192.168.109.7/31 | spine3 | Ethernet45 | 192.168.109.6/31 |
| leaf45 | Ethernet3 | 192.168.109.9/31 | spine1 | Ethernet46 | 192.168.109.8/31 |
| leaf45 | Ethernet4 | 192.168.109.11/31 | spine2 | Ethernet46 | 192.168.109.10/31 |
| leaf45 | Ethernet5 | 192.168.109.13/31 | spine3 | Ethernet46 | 192.168.109.12/31 |
| leaf46 | Ethernet3 | 192.168.109.15/31 | spine1 | Ethernet47 | 192.168.109.14/31 |
| leaf46 | Ethernet4 | 192.168.109.17/31 | spine2 | Ethernet47 | 192.168.109.16/31 |
| leaf46 | Ethernet5 | 192.168.109.19/31 | spine3 | Ethernet47 | 192.168.109.18/31 |
| leaf47 | Ethernet3 | 192.168.109.21/31 | spine1 | Ethernet48 | 192.168.109.20/31 |
| leaf47 | Ethernet4 | 192.168.109.23/31 | spine2 | Ethernet48 | 192.168.109.22/31 |
| leaf47 | Ethernet5 | 192.168.109.25/31 | spine3 | Ethernet48 | 192.168.109.24/31 |
| leaf48 | Ethernet3 | 192.168.109.27/31 | spine1 | Ethernet49 | 192.168.109.26/31 |
| leaf48 | Ethernet4 | 192.168.109.29/31 | spine2 | Ethernet49 | 192.168.109.28/31 |
| leaf48 | Ethernet5 | 192.168.109.31/31 | spine3 | Ethernet49 | 192.168.109.30/31 |
| leaf49 | Ethernet3 | 192.168.109.33/31 | spine1 | Ethernet50 | 192.168.109.32/31 |
| leaf49 | Ethernet4 | 192.168.109.35/31 | spine2 | Ethernet50 | 192.168.109.34/31 |
| leaf49 | Ethernet5 | 192.168.109.37/31 | spine3 | Ethernet50 | 192.168.109.36/31 |
| leaf50 | Ethernet3 | 192.168.109.39/31 | spine1 | Ethernet51 | 192.168.109.38/31 |
| leaf50 | Ethernet4 | 192.168.109.41/31 | spine2 | Ethernet51 | 192.168.109.40/31 |
| leaf50 | Ethernet5 | 192.168.109.43/31 | spine3 | Ethernet51 | 192.168.109.42/31 |

### Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 192.168.101.0/24 | 256 | 55 | 21.49 % |

### Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| FABRIC | borderleaf1 | 192.168.101.91/32 |
| FABRIC | borderleaf2 | 192.168.101.92/32 |
| FABRIC | leaf1 | 192.168.101.1/32 |
| FABRIC | leaf2 | 192.168.101.2/32 |
| FABRIC | leaf3 | 192.168.101.3/32 |
| FABRIC | leaf4 | 192.168.101.4/32 |
| FABRIC | leaf5 | 192.168.101.5/32 |
| FABRIC | leaf6 | 192.168.101.6/32 |
| FABRIC | leaf7 | 192.168.101.7/32 |
| FABRIC | leaf8 | 192.168.101.8/32 |
| FABRIC | leaf9 | 192.168.101.9/32 |
| FABRIC | leaf10 | 192.168.101.10/32 |
| FABRIC | leaf11 | 192.168.101.11/32 |
| FABRIC | leaf12 | 192.168.101.12/32 |
| FABRIC | leaf13 | 192.168.101.13/32 |
| FABRIC | leaf14 | 192.168.101.14/32 |
| FABRIC | leaf15 | 192.168.101.15/32 |
| FABRIC | leaf16 | 192.168.101.16/32 |
| FABRIC | leaf17 | 192.168.101.17/32 |
| FABRIC | leaf18 | 192.168.101.18/32 |
| FABRIC | leaf19 | 192.168.101.19/32 |
| FABRIC | leaf20 | 192.168.101.20/32 |
| FABRIC | leaf21 | 192.168.101.21/32 |
| FABRIC | leaf22 | 192.168.101.22/32 |
| FABRIC | leaf23 | 192.168.101.23/32 |
| FABRIC | leaf24 | 192.168.101.24/32 |
| FABRIC | leaf25 | 192.168.101.25/32 |
| FABRIC | leaf26 | 192.168.101.26/32 |
| FABRIC | leaf27 | 192.168.101.27/32 |
| FABRIC | leaf28 | 192.168.101.28/32 |
| FABRIC | leaf29 | 192.168.101.29/32 |
| FABRIC | leaf30 | 192.168.101.30/32 |
| FABRIC | leaf31 | 192.168.101.31/32 |
| FABRIC | leaf32 | 192.168.101.32/32 |
| FABRIC | leaf33 | 192.168.101.33/32 |
| FABRIC | leaf34 | 192.168.101.34/32 |
| FABRIC | leaf35 | 192.168.101.35/32 |
| FABRIC | leaf36 | 192.168.101.36/32 |
| FABRIC | leaf37 | 192.168.101.37/32 |
| FABRIC | leaf38 | 192.168.101.38/32 |
| FABRIC | leaf39 | 192.168.101.39/32 |
| FABRIC | leaf40 | 192.168.101.40/32 |
| FABRIC | leaf41 | 192.168.101.41/32 |
| FABRIC | leaf42 | 192.168.101.42/32 |
| FABRIC | leaf43 | 192.168.101.43/32 |
| FABRIC | leaf44 | 192.168.101.44/32 |
| FABRIC | leaf45 | 192.168.101.45/32 |
| FABRIC | leaf46 | 192.168.101.46/32 |
| FABRIC | leaf47 | 192.168.101.47/32 |
| FABRIC | leaf48 | 192.168.101.48/32 |
| FABRIC | leaf49 | 192.168.101.49/32 |
| FABRIC | leaf50 | 192.168.101.50/32 |
| FABRIC | spine1 | 192.168.101.101/32 |
| FABRIC | spine2 | 192.168.101.102/32 |
| FABRIC | spine3 | 192.168.101.103/32 |

### VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------------ | ------------------- | ------------------ | ------------------ |
| 192.168.102.0/24 | 256 | 52 | 20.32 % |

### VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
| FABRIC | borderleaf1 | 192.168.102.91/32 |
| FABRIC | borderleaf2 | 192.168.102.92/32 |
| FABRIC | leaf1 | 192.168.102.1/32 |
| FABRIC | leaf2 | 192.168.102.1/32 |
| FABRIC | leaf3 | 192.168.102.3/32 |
| FABRIC | leaf4 | 192.168.102.3/32 |
| FABRIC | leaf5 | 192.168.102.5/32 |
| FABRIC | leaf6 | 192.168.102.5/32 |
| FABRIC | leaf7 | 192.168.102.7/32 |
| FABRIC | leaf8 | 192.168.102.7/32 |
| FABRIC | leaf9 | 192.168.102.9/32 |
| FABRIC | leaf10 | 192.168.102.9/32 |
| FABRIC | leaf11 | 192.168.102.11/32 |
| FABRIC | leaf12 | 192.168.102.11/32 |
| FABRIC | leaf13 | 192.168.102.13/32 |
| FABRIC | leaf14 | 192.168.102.13/32 |
| FABRIC | leaf15 | 192.168.102.15/32 |
| FABRIC | leaf16 | 192.168.102.15/32 |
| FABRIC | leaf17 | 192.168.102.17/32 |
| FABRIC | leaf18 | 192.168.102.17/32 |
| FABRIC | leaf19 | 192.168.102.19/32 |
| FABRIC | leaf20 | 192.168.102.19/32 |
| FABRIC | leaf21 | 192.168.102.21/32 |
| FABRIC | leaf22 | 192.168.102.21/32 |
| FABRIC | leaf23 | 192.168.102.23/32 |
| FABRIC | leaf24 | 192.168.102.23/32 |
| FABRIC | leaf25 | 192.168.102.25/32 |
| FABRIC | leaf26 | 192.168.102.25/32 |
| FABRIC | leaf27 | 192.168.102.27/32 |
| FABRIC | leaf28 | 192.168.102.27/32 |
| FABRIC | leaf29 | 192.168.102.29/32 |
| FABRIC | leaf30 | 192.168.102.29/32 |
| FABRIC | leaf31 | 192.168.102.31/32 |
| FABRIC | leaf32 | 192.168.102.31/32 |
| FABRIC | leaf33 | 192.168.102.33/32 |
| FABRIC | leaf34 | 192.168.102.33/32 |
| FABRIC | leaf35 | 192.168.102.35/32 |
| FABRIC | leaf36 | 192.168.102.35/32 |
| FABRIC | leaf37 | 192.168.102.37/32 |
| FABRIC | leaf38 | 192.168.102.37/32 |
| FABRIC | leaf39 | 192.168.102.39/32 |
| FABRIC | leaf40 | 192.168.102.39/32 |
| FABRIC | leaf41 | 192.168.102.41/32 |
| FABRIC | leaf42 | 192.168.102.41/32 |
| FABRIC | leaf43 | 192.168.102.43/32 |
| FABRIC | leaf44 | 192.168.102.43/32 |
| FABRIC | leaf45 | 192.168.102.45/32 |
| FABRIC | leaf46 | 192.168.102.45/32 |
| FABRIC | leaf47 | 192.168.102.47/32 |
| FABRIC | leaf48 | 192.168.102.47/32 |
| FABRIC | leaf49 | 192.168.102.49/32 |
| FABRIC | leaf50 | 192.168.102.49/32 |
