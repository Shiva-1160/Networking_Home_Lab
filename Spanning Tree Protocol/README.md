# Spanning Tree Protocol (STP) Loop Prevention Lab (GNS3)

## Project Overview

This project demonstrates the operation of the **Spanning Tree Protocol (STP)** in a Layer 2 switched network. The lab focuses on:

- STP loop prevention
- Root Bridge election
- BPDU exchange
- Port roles and states
- Path cost calculation
- Redundant link handling
- Broadcast loop prevention
- STP convergence behavior

The topology contains three interconnected Layer 2 switches forming a physical loop. STP is used to prevent Layer 2 broadcast storms by logically blocking redundant paths while maintaining network redundancy.

---

# Network Topology

## Devices Used

- Three Open vSwitch (OVS) Layer 2 Switches
- Four VPCS Clients
- Wireshark for packet analysis

### Network

```text
Network: 10.0.0.0/24
```

---

# Host Configuration

| Device | IP Address |
|----------|----------|
| PC1 | 10.0.0.2 |
| PC2 | 10.0.0.3 |
| PC3 | 10.0.0.4 |
| PC4 | 10.0.0.5 |

---

# Switch Information

| Switch | Bridge MAC Address |
|----------|----------|
| Switch-1 | 72:59:c8:f2:9f:4c |
| Switch-2 | a2:26:9c:52:5c:42 |
| Switch-3 | 22:e8:63:bc:46:4f |

---

# Key Experiments

## 1. Root Bridge Election

Observed how STP elects a Root Bridge based on:

- Bridge Priority
- Bridge MAC Address

Verified:

- Lowest Bridge ID becomes Root Bridge
- All non-root switches select Root Ports

## 2. BPDU Analysis

Captured and analyzed BPDU packets using Wireshark.

Observed:

- Configuration BPDUs
- Root Bridge ID
- Sender Bridge ID
- Path Cost
- Hello Time
- Max Age
- Forward Delay

Verified that switches continuously exchange BPDUs to maintain a loop-free topology.

---

## 3. Port Role Identification

Verified STP port roles:

### Root Port

Best path toward Root Bridge.

### Designated Port

Forwarding port for a network segment.

### Alternate/Blocked Port

Redundant path placed into blocking state.

Observed port role changes when topology parameters were modified.

---

## 4. Port State Verification

Observed STP states:

```text
Blocking
Listening
Learning
Forwarding
```

Verified state transitions during topology convergence.

Captured STP traffic during these transitions using Wireshark.

---

## 5. Path Cost Manipulation

Modified interface path costs to influence STP path selection.

Example:

interface eth0
spanning-tree cost 100

Observed:

- Root Port changes
- Alternate path selection
- Updated Root Path Cost calculations

---

## 6. Bridge Priority Manipulation

Modified bridge priority values to force Root Bridge election.

Example:

ovs-vsctl set Bridge br0 other_config:stp-priority=4096

Observed:

- New Root Bridge election
- BPDU updates
- Recalculation of spanning tree topology

---

## 7. Broadcast Loop Prevention

Generated broadcast traffic and verified:

- Frames are forwarded through active paths only
- Redundant links remain blocked
- No broadcast storm occurs

Confirmed successful loop prevention through STP.

---

## 8. End-to-End Connectivity Testing

Verified communication between:

- PC1 ↔ PC3
- PC1 ↔ PC4
- PC2 ↔ PC3
- PC2 ↔ PC4

Observed successful connectivity despite one redundant path being blocked.

---

## 9. Failure Scenarios

### Link Failure

Disconnected active switch-to-switch links.

Observed:

- STP recalculation
- Previously blocked ports transitioning to forwarding state
- Network connectivity restoration

### Root Bridge Failure

Stopped the Root Bridge.

Observed:

- New Root Bridge election
- Topology convergence
- BPDU updates

---

# Packet Analysis

Captured traffic using Wireshark and analyzed:

- STP Configuration BPDUs
- ARP Requests and Replies
- ICMP Echo Requests and Replies
- Broadcast Frames
- Topology Change Notifications (TCN)

Observed:

- Continuous BPDU exchange
- Root Bridge advertisements
- Path cost propagation
- Topology updates after failures

---

# Key Learnings

- STP prevents Layer 2 loops
- Bridge Priority influences Root Bridge election
- Path Cost determines preferred forwarding paths
- BPDUs are essential for topology calculation
- Redundant links improve availability
- STP blocks unnecessary paths while preserving redundancy
- Network connectivity survives link failures through reconvergence
- Wireshark provides visibility into STP operations and BPDU contents

---

# Outcome

Successfully implemented a redundant Layer 2 switched network with:

- STP enabled
- Root Bridge election
- BPDU analysis
- Loop prevention
- Path cost manipulation
- Bridge priority tuning
- Redundant path failover
- End-to-end connectivity validation

This lab provided practical understanding of how STP creates a loop-free topology while maintaining network redundancy and high availability in switched Ethernet environments.
