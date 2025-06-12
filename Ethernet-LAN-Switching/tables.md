| Acronym | Stands For               | Plain Meaning                                                        |
|---------|--------------------------|------------------------------------------------------------------------|
| HTYPE   | Hardware Type            | What kind of hardware address is used (e.g., Ethernet MAC)            |
| PTYPE   | Protocol Type            | What kind of Layer 3 protocol is being mapped (e.g., IPv4)            |
| HLEN    | Hardware Length          | How many bytes the hardware address is (usually 6 for MAC)            |
| PLEN    | Protocol Length          | How many bytes the protocol address is (usually 4 for IPv4)           |
| OPER    | Operation                | 1 = Request, 2 = Reply — indicates ARP request or reply                |
| SHA     | Sender Hardware Address  | Sender’s MAC address                                                  |
| SPA     | Sender Protocol Address  | Sender’s IP address                                                   |
| THA     | Target Hardware Address  | Destination MAC (set to 0s in request)                                |
| TPA     | Target Protocol Address  | Destination IP address                                                |

## Ethernet II frame field
| Aspect             | Ethernet II Details                                          |
|--------------------|--------------------------------------------------------------|
| Field Size         | 2 bytes                                                      |
| Purpose            | Identify Layer 3 protocol                                    |
| Used By            | Routers, switches, NICs                                      |
| Critical For       | Decoding Ethernet payloads                                   |
| Interpretation Rule| ≥ 1536 = Type (EtherType); ≤ 1500 = Length (IEEE 802.3 frames) |

| Hex | Decimal | Binary |
|-----|---------|--------|
| 0   | 0       | 0000   |
| 1   | 1       | 0001   |
| 2   | 2       | 0010   |
| 3   | 3       | 0011   |
| 4   | 4       | 0100   |
| 5   | 5       | 0101   |
| 6   | 6       | 0110   |
| 7   | 7       | 0111   |
| 8   | 8       | 1000   |
| 9   | 9       | 1001   |
| A   | 10      | 1010   |
| B   | 11      | 1011   |
| C   | 12      | 1100   |
| D   | 13      | 1101   |
| E   | 14      | 1110   |
| F   | 15      | 1111   |

| Hexadecimal | Decimal |
|-------------|---------|
| A           | 10      |
| B           | 11      |
| C           | 12      |
| D           | 13      |
| E           | 14      |
| F           | 15      |

| EtherType (Hex) | Decimal | Protocol                        | Description                           |
|------------------|---------|----------------------------------|---------------------------------------|
| 0x0800           | 2048    | IPv4                             | Internet Protocol version 4           |
| 0x0806           | 2054    | ARP                              | Address Resolution Protocol           |
| 0x86DD           | 34525   | IPv6                             | Internet Protocol version 6           |
| 0x8100           | 33024   | 802.1Q VLAN tag                  | VLAN-tagged frame                     |
| 0x8847           | —       | MPLS unicast                     | MPLS (Multiprotocol Label Switching)  |
| 0x88CC           | —       | LLDP                             | Link Layer Discovery Protocol         |
