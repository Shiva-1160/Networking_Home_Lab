# Subnetting Lab (GNS3)

## Project Overview

This project demonstrates etworking concepts using GNS3 with a Linux-based FRRouting router, Open vSwitch (OVS) and multiple VPCS hosts.
The lab focuses on subnetting, inter-subnet routing, ARP behavior and packet flow across different broadcast domains.

---

## Network Topology

1. One FRRouting Router (gateway for all subnets)
2. Three OVS Switches (one per subnet)
3. Multiple PCs distributed across subnets
4. Network divided into multiple /26 subnets

---

## IP Addressing

### Subnet 1: 192.168.23.0/26

* Gateway: 192.168.23.1
* Hosts: 192.168.23.2, .3, .4

### Subnet 2: 192.168.23.64/26

* Gateway: 192.168.23.65
* Hosts: 192.168.23.66, .67, .68

### Subnet 3: 192.168.23.128/26

* Gateway: 192.168.23.129
* Hosts: 192.168.23.130, .131, .132

---

## Configuration Details

1. Router configured with multiple interfaces, each assigned to a different subnet
2. IP forwarding enabled on router for inter-subnet communication
3. OVS used as Layer 2 switches within each subnet
4. PCs configured with static IP and appropriate default gateway

---

## Key Experiments

### 1. Subnetting Validation

* Tested valid and invalid host addresses
* Identified network and broadcast addresses
* Verified subnet boundaries (/26)

---

### 2. Gateway Behavior

* Configured correct and incorrect default gateways
* Observed:

  * Same subnet communication works without gateway
  * Inter-subnet communication fails with wrong gateway

---

### 3. ARP Behavior

* Observed ARP requests within a subnet
* Verified that ARP does not cross subnets
* Confirmed router generates ARP in destination subnet

---

### 4. Routing Decisions

* Analyzed how router selects outgoing interface
* Verified longest prefix match concept
* Understood routing table-based forwarding

---

### 5. Failure Scenarios

* Incorrect subnet mask
* Wrong IP assignment
* Interface shutdown
* Cable disconnection

Observed how each issue affects connectivity

---

### 6. Packet Analysis

* Captured traffic using Wireshark
* Analyzed:

  * ARP requests/replies
  * ICMP echo (ping)
  * Packet flow across router

---

## Verification

* Connectivity tested using `ping` across all subnets
* ARP tables verified during communication
* Routing behavior validated through successful inter-subnet traffic

---

## Tools Used

* GNS3
* Wireshark

---

## Key Learnings

* Subnet mask defines network boundaries
* ARP works only within a broadcast domain
* Routers do not forward broadcast traffic
* Default gateway is required for inter-subnet communication
* Routing decisions are based on destination IP and prefix matching

---

## Outcome

Successfully implemented a multi-subnet network and analyzed packet flow across Layer 2 and Layer 3, gaining strong practical understanding of subnetting, ARP and routing behavior.
