# Networking Home Lab (CCNA)

## Overview

Welcome to my Networking Home Lab repository.

This repository documents my journey of learning computer networking through hands-on labs. Every topology is built, configured, verified
and troubleshot in a practical environment to strengthen my understanding of CCNA-level networking concepts.

Rather than simply making configurations work, I focus on understanding **how protocols behave**, **why networks fail**
and **how to troubleshoot them using industry-standard tools and methodologies**.

---

# Lab Architecture

The lab uses a distributed setup where the GNS3 graphical interface runs locally while the emulation server is hosted on an AWS EC2 Ubuntu instance.

This architecture allows me to build larger topologies while keeping the local machine lightweight.

**Infrastructure**

* **Network Emulator:** GNS3
* **Cloud Backend:** AWS EC2 (Ubuntu)
* **Routing:** FRRouting (FRR)
* **Virtual Switching:** Open vSwitch (OVS)
* **Packet Analysis:** Wireshark

---

# Learning Objectives

The primary goal of this home lab is to:

* Build and configure enterprise style network topologies
* Understand Layer 2 and Layer 3 networking concepts
* Learn systematic network troubleshooting
* Analyze packet flow using Wireshark
* Document every lab for future reference and revision

---

# Technologies & Topics

## Layer 2

* VLAN Configuration
* Inter-VLAN Routing
* Rapid Spanning Tree Protocol (RSTP)
* Switchport Security
* Etherchannel
* Layer 2 Connectivity Verification

## Layer 3

* IPv4 Addressing
* IPv6 Addressing
* OSPF
* Subnetting

## Network Services

* DHCP
* NAT/PAT
* Access Control Lists (ACLs)
* SSH
* Syslog
* NTP
* DHCP
* DNS

## Traffic Management

* Quality of Service (QoS)
* Classification & Marking

## Network Analysis

* Packet Capture
* Protocol Analysis
* Packet Header Inspection
* Network Traffic Verification

---

# Lab Workflow

Each lab follows the same engineering workflow:

1. Design the network topology.
2. Configure routers and switches.
3. Verify connectivity using CLI commands.
4. Capture packets using Wireshark.
5. Introduce intentional faults.
6. Troubleshoot and restore network functionality.
7. Document configurations and observations.

---

# Verification & Troubleshooting

Every topology includes a validation phase using standard networking tools such as:

* `ping`
* `traceroute`
* `show ip route`
* `show interfaces`
* `show vlan`
* `show ip ospf neighbor`
* `show running-config`

Packet captures are analyzed in Wireshark to observe protocol behavior, routing updates, ARP resolution, and packet forwarding.

---

# Repository Contents

Each completed lab will typically include:

* Network topology
* Device configurations
* Verification commands
* Wireshark packet captures
* Troubleshooting notes
* Lessons learned

---

# Learning Philosophy

One of the best ways to learn networking is by intentionally creating failures and understanding how to diagnose them.

Every lab is treated as a real troubleshooting exercise building the network, validating expected behavior, identifying issues and systematically resolving them using CLI verification commands and packet analysis.

The goal is not just to configure networks, but to understand **why they work** and **how to troubleshoot them when they don't**.
