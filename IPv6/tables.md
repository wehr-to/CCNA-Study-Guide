# IPv6 Address Types

| Address Type       | Prefix                     | Routable?        | Scope         | Use Case                                                                 |
|--------------------|----------------------------|------------------|---------------|--------------------------------------------------------------------------|
| Link-local         | FE80::/10                  | No               | Local link    | Used between neighbors on same link (routing adjacencies, NDP, etc.)     |
| Loopback           | ::1/128                    | No               | Host-only     | Local testing (like 127.0.0.1 in IPv4)                                   |
| Unspecified        | ::/128                     | No               | Special       | "No address assigned" state (e.g., during DAD)                           |
| Multicast (some)   | FF00::/8                   | Some             | Varies by group | Depends on multicast scope; many aren’t forwarded                      |
| Unique Local (ULA) | FC00::/7 (usually FD00::/8) | Yes (within org) | Private/internal | Private routing inside orgs, like IPv4’s RFC 1918                   |

# IPv6 Address Examples

| Address     | Example     | Routable?         | Notes                                         |
|-------------|-------------|-------------------|-----------------------------------------------|
| Link-local  | FE80::1     | No                | Required for OSPFv3, NDP, RA, etc.            |
| Loopback    | ::1         | No                | Local host only                               |
| Unspecified | ::          | No                | Seen in DHCPv6 / autoconfig states            |
| ULA         | FD00::/8    | Yes (internal only) | Like 10.0.0.0/8 for IPv6                      |

# IPv4 Multicast Addresses

| Address       | Description             |
|---------------|-------------------------|
| 224.0.0.1     | All Nodes               |
| 224.0.0.2     | All Routers             |
| 224.0.0.5     | All OSPF routers        |
| 224.0.0.6     | All OSPF DRs/BDRs       |
| 224.0.0.9     | All RIP routers         |
| 224.0.0.10    | All EIGRP routers       |

# IPv6 Multicast Addresses

| Address     | Description             |
|-------------|-------------------------|
| FF02::1     | All nodes               |
| FF02::2     | All routers             |
| FF02::5     | All OSPF routers        |
| FF02::6     | All OSPF DRs/BDRs       |
| FF02::9     | All RIP routers         |
| FF02::A     | All EIGRP routers       |
| FF01        | Interface-local         |
| FF02        | Link-local              |
| FF05        | Site-local              |
| FF08        | Organization-local      |
| FF0E        | Global                  |

# NDP (Neighbor Discovery Protocol) Message Types

| Message | ICMPv6 Type |
|---------|-------------|
| NDP RS  | ICMPv6 Type 133 |
| NDP RA  | ICMPv6 Type 134 |
| NDP NS  | ICMPv6 Type 135 |
| NDP NA  | ICMPv6 Type 136 |
