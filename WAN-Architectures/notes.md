## Leased Line Bandwidth Standards

# VPNs, Tunneling, and WAN Technologies

## GRE & DMVPN

- GRE creates tunnels like IPsec, but does not encrypt the original packet.
- DMVPN is a Cisco-developed solution that allows routers to dynamically create a full mesh of IPsec tunnels without having to manually configure every single tunnel.

## Internet Access Technologies

- DSL provides Internet connectivity via phone lines.
- Cable (CATV) Internet provides Internet connectivity via TV lines.
- A cable modem is required to convert data into a format suitable to be sent over the TV lines.
- A DSL modem is required to convert data into a format suitable to be sent over the phone lines.

## VPN Types

- Site-to-site VPNs are used to permanently connect two sites over the Internet.
- Remote-access VPNs are used to provide on-demand access to the company network for end devices.
- Site-to-site VPNs typically use IPsec.
- Remote-access VPNs typically use TLS.

## MPLS VPN Behavior

- In Layer 3 MPLS VPNs, CE routers and PE routers can form routing protocol peerings.
- In Layer 2 MPLS VPNs, CE routers form routing protocol peerings with each other.
- In Layer 2 MPLS VPNs, the entire service provider network is transparent to the customer.

## Q&A

**Q: Does GRE support broadcast and multicast traffic?**  
A: Yes

**Q: Does IPsec support broadcast and multicast traffic?**  
A: No

**Q: In MPLS, what does CE router stand for?**  
A: Customer Edge

**Q: In MPLS, what does P router stand for?**  
A: Provider (Core)

**Q: In MPLS, what does PE router stand for?**  
A: Provider Edge

**Q: What does DMVPN stand for?**  
A: Dynamic Multipoint VPN

**Q: What does DSL stand for?**  
A: Digital Subscriber Line

**Q: What does GRE stand for?**  
A: Generic Routing Encapsulation

**Q: What does modem stand for?**  
A: modulator-demodulator

**Q: What does MPLS stand for?**  
A: Multi Protocol Label Switching

**Q: What does SSL stand for?**  
A: Secure Sockets Layer

**Q: What does TLS stand for?**  
A: Transport Layer Security

| Standard | Bandwidth   |
| -------- | ----------- |
| T1       | 1.544 Mbps  |
| E1       | 2.048 Mbps  |
| T2       | 6.312 Mbps  |
| E2       | 8.448 Mbps  |
| E3       | 34.368 Mbps |
| T3       | 44.736 Mbps |

## Internet Connectivity Models

| Connectivity Type | Description                     |
| ----------------- | ------------------------------- |
| Single-Homed      | 1 connection to 1 ISP           |
| Dual-Homed        | 2 connections to 1 ISP          |
| Multihomed        | 1 connection to each of 2 ISPs  |
| Dual-Multihomed   | 2 connections to each of 2 ISPs |
