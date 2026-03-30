# Layer 2 & Layer 3 Network Lab (GNS3)

## Project Overview
This project demonstrates a basic Layer 2 and Layer 3 network using GNS3 with a Linux router, Open vSwitch (OVS), and multiple hosts.  
It focuses on understanding packet flow, switching and interface behavior in a virtual environment.

---

## Network Topology
1. &nbsp;One FRRouter (acts as gateway)  
2. &nbsp;One OVS Switch  
3. &nbsp;Four PCs connected to the switch  
4. &nbsp;All devices in a single subnet  

---

## IP Addressing
1. &nbsp;Network: 192.168.23.0/24  
2. &nbsp;Router : 192.168.23.1  
3. &nbsp;PC1    : 192.168.23.2  
4. &nbsp;PC2    : 192.168.23.3  
5. &nbsp;PC3    : 192.168.23.4  
6. &nbsp;PC4    : 192.168.23.5  

---

## Configuration Details
1. &nbsp;Router configured with IP and enabled forwarding  
2. &nbsp;OVS used as a Layer 2 switch connecting all devices  
3. &nbsp;PCs assigned IP addresses with router as gateway  

---

## Key Experiments
1. **Port Control Testing**  
   - `ovs-ofctl mod-port` (switch-level control)  
   - `ip link set down` (interface-level control)  
   - Observed how traffic behaves in both cases  

2. **Wrong Gateway Configuration**  
   - ARP still works but PC cannot reach the gateway  
   - Observed ARP broadcasts in Wireshark with no valid replies  

3. **Interface Misconfiguration (IP/Subnet)**  
   - Assigned wrong IP/subnet mask to a PC  
   - Devices in same network failed to communicate  
   - Understood importance of correct subnetting  

4. **Packet Analysis**  
   - Captured traffic using Wireshark  
   - Analyzed ARP requests, ICMP packets and failure scenarios  

---

## Verification
- Connectivity tested using `ping` between PCs and router  
- Traffic drop verified by disabling ports/interfaces  

---

## Tools Used
- GNS3  
- Linux Networking Tools  
- Wireshark  

---

## Outcome
Successfully built and tested a virtual network, gaining practical understanding of switching, routing and the difference between logical port blocking and interface shutdown.
