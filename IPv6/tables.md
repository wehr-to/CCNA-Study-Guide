# IPv6 Address Types

| Address Type       | Prefix                     | Routable?        | Scope         | Use Case                                                                 |
|--------------------|----------------------------|------------------|---------------|--------------------------------------------------------------------------|
| Link-local         | FE80::/10                  | No               | Local link    | Used between neighbors on same link (routing adjacencies, NDP, etc.)     |
| Loopback           | ::1/128                    | No               | Host-only     | Local testing (like 127.0.0.1 in IPv4)                                   |
| Unspecified        | ::/128                     | No               | Special       | "No address assigned" state (e.g., during DAD)                           |
| Multicast (some)   | FF00::/8                   | Some             | Varies by group | Depends on multicast scope; many aren’t forwarded                      |
| Unique Local (ULA) | FC00::/7 (usually FD00::/8) | Yes (within org) | Private/internal | Private routing inside orgs — like IPv4’s RFC 1918                   |

# IPv6 Address Examples

| Address     | Example     | Routable?         | Notes                                         |
|-------------|-------------|-------------------|-----------------------------------------------|
| Link-local  | FE80::1     | No                | Required for OSPFv3, NDP, RA, etc.            |
| Loopback    | ::1         | No                | Local host only                               |
| Unspecified | ::          | No                | Seen in DHCPv6 / autoconfig states            |
| ULA         | FD00::/8    | Yes (internal only) | Like 10.0.0.0/8 for IPv6                      |
