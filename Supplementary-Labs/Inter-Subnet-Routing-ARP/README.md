# Supplementary Lab - Inter-Subnet Routing & ARP
 
## Overview
 
Followed a YouTube tutorial outside Jeremy's IT Lab course to reinforce how communication differs within a subnet versus across subnets, and how ARP fits into that process. Added here as supplementary practice rather than part of the main day-by-day sequence.
 
## Topology
 
One router connecting two departments, each on its own VLAN/subnet behind its own switch.
 
- **Dept A (VLAN 10):** 2911 Router → 2960 Switch0 → PC0 (192.168.10.11), PC1 (192.168.10.12)
- **Dept B (VLAN 20):** 2911 Router → 2960 Switch1 → PC2 (192.168.20.13), PC3 (192.168.20.14)
## What I Tested
 
Ran pings from PC0 to a host on the same subnet (PC1) and to a host on a different subnet (PC2), then checked the ARP cache.
 
**Same subnet (PC0 → 192.168.10.12):** 4/4 packets received, 0% loss. Switch already knew both MAC addresses, so traffic stayed local with no routing needed.
 
**Different subnet (PC0 → 192.168.20.13):** First ping timed out, remaining 3/4 succeeded, 25% loss overall. The timeout was ARP resolving for the first time. Once ARP resolved the router's MAC and the reply path was established, subsequent pings succeeded.
 
**ARP cache check (`arp -a`):** Confirmed PC0 had resolved the physical (MAC) addresses for the local gateway/hosts it had communicated with.
 
## Key Takeaways
 
- Same-subnet communication is handled entirely at Layer 2 by the switch, no router involvement needed
- Cross-subnet communication requires the router as the gateway between VLANs, which adds a small amount of initial latency while ARP resolves
- The dropped first packet on a new destination is normal and expected. It reflects the ARP request/reply round trip, not a fault
- This reinforces why default gateway configuration matters on end devices. Without it, a host has no way to reach anything outside its own subnet
## Files
 
- `topology.png` — screenshot of the Packet Tracer topology
- `lab.pkt` — Packet Tracer file
