# GRE (Generic Routing Encapsulation) – Protocol Overview

## What is GRE?

GRE (Generic Routing Encapsulation) is a tunneling protocol developed to encapsulate a wide variety of Layer 3 protocols over an IP network. It allows **non-IP or routing-incompatible protocols** to be carried through an IP-based infrastructure.

- GRE is defined in **RFC 2784**
- Protocol number **47** (not TCP/UDP)

## Key Features

| Feature            | Description |
|--------------------|-------------|
| Protocol Encapsulation | GRE can encapsulate IPv4, IPv6, IPX, AppleTalk, etc. |
| Stateless | GRE does not provide flow control or encryption |
| Compatible with IPsec | GRE can be combined with IPsec to add encryption and integrity |
| Allows Routing Protocols | GRE tunnels can carry routing protocols like OSPF, EIGRP, BGP across the tunnel |

## GRE Packet Structure

| Field               | Purpose |
|---------------------|---------|
| GRE Header          | 4 to 8 bytes, contains flags and protocol type |
| Encapsulated Packet | The original IP (or other) payload being tunneled |
| Outer IP Header     | Added by the router, routes the packet over the internet or WAN |

## GRE Tunnel Use Cases

- **Routing protocol adjacency over non-broadcast networks**
- **IPv6 over IPv4** (or vice versa)
- **Multiprotocol tunneling over IP**
- **Tunneling over MPLS, Frame Relay, or the internet**
- **Simplified VPN overlays (GRE over IPsec)**

## GRE Configuration Example (Cisco IOS)

### Router A (Tunnel Source: 192.0.2.1)
```bash
interface Tunnel0
 ip address 10.0.0.1 255.255.255.252
 tunnel source 192.0.2.1
 tunnel destination 192.0.2.2
```

| Feature          | GRE                         | IPsec                 |
| ---------------- | --------------------------- | --------------------- |
| Encryption       | Not provided              | Yes                 |
| Protocol Support | Multiprotocol             | IP-only             |
| Routing Support  | Carries routing protocols | Limited without GRE |

```
To secure GRE, combine it with IPsec:
GRE handles the encapsulation
IPsec handles encryption and authentication
```

