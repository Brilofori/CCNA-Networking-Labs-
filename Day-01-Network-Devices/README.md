# Day 01 - Network Devices

## Overview

Topology build based on Jeremy's IT Lab Day 1 (Network Devices). No device configurations in this lab — the goal was to replicate a site-to-site enterprise network and understand what each device does in the path.

## Topology

Two branch offices (New York and Tokyo) connected over a simulated WAN.

**New York Branch:** PC0, PC1 → 2960 Switch → 2911 Router → ASA 5506-X Firewall

**WAN:** Both branches connect through a router simulating the internet

**Tokyo Branch:** ASA 5506-X Firewall → 2911 Router → 2960 Switch → Server0, Meraki Server0


## Key Takeaways

- Switches operate at Layer 2, forwarding traffic within the local network based on MAC addresses
- Routers operate at Layer 3, forwarding traffic between different networks using IP addresses
- Firewalls (ASAs) sit at the network perimeter between the internal network and the WAN, filtering traffic before it leaves or enters the branch
- The "internet" in this topology is simulated by a router connecting the two ASAs, representing the WAN link between sites

## Files

- `Network topology.png` — screenshot of the Packet Tracer topology
- `day01-lecture.pkt` — Packet Tracer file
