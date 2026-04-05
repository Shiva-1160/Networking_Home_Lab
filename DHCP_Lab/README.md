# DHCP Lab (GNS3)

## Project Overview

This project demonstrates **Dynamic Host Configuration Protocol (DHCP)** using GNS3 with a Linux-based DHCP server, FRRouting router and Open vSwitch (OVS). 
The lab focuses on automatic IP allocation, DHCP packet flow (DORA), ARP-based conflict detection and troubleshooting scenarios.

---

## Network Topology

* One FRRouting Router (default gateway)
* One OVS Switch (Layer 2 connectivity)
* One Linux Server (DHCP Server)
* Multiple VPCS Clients

Single subnet network: `192.168.1.0/24`

---

## IP Addressing

* Network: `192.168.1.0/24`
* Gateway (Router): `192.168.1.1`
* DHCP Server: `192.168.1.2`
* Clients: Dynamically assigned (`192.168.1.3 – 192.168.1.254`)

---

## Configuration Details

### DHCP Server

Configured using `/etc/dhcp/dhcpd.conf`:

```
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.3 192.168.1.254;
  option routers 192.168.1.1;
}
```

### Router

* Configured with IP: `192.168.1.1/24`
* Acts as default gateway for clients

---

### Clients

* Configured using DHCP:


## Key Experiments

### 1. DHCP Process (DORA)

Observed complete DHCP workflow:

* Discover → Client broadcasts request
* Offer → Server offers IP
* Request → Client accepts IP
* ACK → Server confirms allocation

---

### 2. ARP Behavior in DHCP

* DHCP server sends ARP request before assigning IP
* Ensures no duplicate IP exists
* Client sends Gratuitous ARP after receiving IP

---

### 3. Lease Management

* Verified lease allocation and renewal
* Observed lease details using:

```
/var/lib/dhcp/dhcpd.leases
```

---

### 4. Switch MAC Table Learning

* Verified MAC address learning using:

```
ovs-appctl fdb/show br0
```

---

### 5. Failure Scenarios

#### Incorrect Subnet

* DHCP fails with bad range, address not in subnet

#### DHCP Service Down

* Clients fail to obtain IP as there is no DHCP server in the network

#### IP Conflict

* Static IP conflicts detected via ARP

#### Wrong Gateway

* Clients receive IP but cannot communicate outside network

---

### 6. Packet Analysis

Captured traffic using Wireshark and analyzed:

* DHCP Discover, Offer, Request, ACK
* ARP requests for conflict detection
* Gratuitous ARP from client

---

## Verification

* IP assignment verified using:

```
show ip
```

* Connectivity tested using ping
* DHCP server identified in client output
* Gateway and subnet validated

---

## Tools Used

* GNS3
* Wireshark

---

## Key Learnings

* DHCP automates IP allocation in networks
* Lease table tracks allocation but not real-time usage
* ARP is used for duplicate IP detection
* Broadcast-based protocols operate within same subnet
* Proper configuration is critical for network stability

---

## Outcome

Successfully implemented a DHCP-based network and analyzed IP allocation, ARP behavior and packet flow, gaining practical understanding of DHCP operations and troubleshooting in real-world scenarios.
