# Layer 3 Switching with Inter-VLAN Routing (GNS3)

## Project Overview

This project demonstrates Layer 3 Switching and Inter-VLAN Routing.The lab focuses on:

* VLAN segmentation
* Switch Virtual Interfaces (SVI)
* Inter-VLAN communication
* Static routing between networks
* Layer 2 vs Layer 3 forwarding behavior
* MAC learning and ARP operations

The topology contains two VLANs connected to a Layer 3 switch and an external router connected to another subnet.


# Network Topology

### Devices Used

* One Layer 3 OVS Switch
* One FRRouting Router
* One Layer 2 OVS Switch
* Multiple VPCS Clients


# VLAN Configuration

## VLAN 10

Network: `192.168.2.0/29`

| Device     | IP Address  |
| ---------- | ----------- |
| PC1        | 192.168.2.2 |
| PC2        | 192.168.2.3 |
| SVI br0.10 | 192.168.2.1 |


## VLAN 20

Network: `192.168.2.8/29`

| Device     | IP Address   |
| ---------- | ------------ |
| PC3        | 192.168.2.10 |
| PC4        | 192.168.2.11 |
| SVI br0.20 | 192.168.2.9  |


## Router Link Network

Network: `10.0.0.0/30`

| Device         | IP Address |
| -------------- | ---------- |
| Layer 3 Switch | 10.0.0.1   |
| Router-1       | 10.0.0.2   |


## External LAN

Network: `192.168.3.0/24`

| Device        | IP Address  |
| ------------- | ----------- |
| Router-1 eth1 | 192.168.3.1 |
| PC5           | 192.168.3.2 |
| PC6           | 192.168.3.3 |
| PC7           | 192.168.3.4 |



# Key Experiments

# 1. Inter-VLAN Routing

Verified communication between:

* VLAN 10 ↔ VLAN 20
* VLANs ↔ External LAN

Observed successful Layer 3 forwarding using SVI interfaces.


# 2. MAC Address Learning

Verified switch MAC learning using:

Observed:

* MAC addresses learned dynamically
* VLAN-based MAC separation
* Port-to-MAC mapping


# 3. ARP Behavior

Observed ARP requests and replies:

* PC sends ARP for default gateway
* SVI responds with MAC address
* Router performs ARP for external LAN devices

Captured using Wireshark.


# 4. Broadcast Domain Isolation

Verified that:

* VLAN 10 broadcasts stay inside VLAN 10
* VLAN 20 broadcasts stay inside VLAN 20
* Broadcast traffic does not cross VLAN boundaries

Demonstrated VLAN isolation.


# 5. Layer 2 vs Layer 3 Forwarding

Observed:

## Same VLAN Communication

Traffic switched using MAC addresses only.

## Different VLAN Communication

Traffic routed through SVI interfaces using IP routing.


# 6. Static Routing Verification

Verified routing table using:

Confirmed:

* Router knows VLAN networks
* Layer 3 switch forwards traffic correctly


# 7. Failure Scenarios

## Wrong Gateway

Clients cannot communicate outside VLAN.


## Incorrect VLAN Assignment

Hosts placed in wrong VLAN lose connectivity.


## Missing Route

External LAN unreachable from VLANs.


## IP Forwarding Disabled

Inter-VLAN routing fails completely.


# Packet Analysis

Captured traffic using Wireshark and analyzed:

* ARP Requests and Replies
* ICMP Echo Requests/Replies
* VLAN-tagged Ethernet frames
* Routed packets between VLANs

Observed clear distinction between:

* Layer 2 switching
* Layer 3 routing


# Key Learnings

* VLANs create separate broadcast domains
* SVIs enable Inter-VLAN routing
* Layer 3 switches perform both switching and routing
* ARP resolves IP-to-MAC mappings
* Static routing enables communication between networks
* OVS supports enterprise-style VLAN operations
* IP forwarding is required for routing packets


# Outcome

Successfully implemented a Layer 3 switching environment with:

* VLAN segmentation
* Inter-VLAN routing
* Static routing
* MAC learning
* ARP analysis
* External network connectivity

This lab provided practical understanding of how modern Layer 3 switches route traffic between VLANs while maintaining Layer 2 switching functionality inside each VLAN.
