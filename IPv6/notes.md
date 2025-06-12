# IPv6 Notes

---

## Local-Only IPv6 Address Types

If you see a question like:  
"Which IPv6 address types are not forwarded beyond the local link?"  
Answer:  
Link-local, loopback, unspecified

---

## Unique Local IPv6 Address Structure

Four sections of an IPv6 'unique local' address:
- Hexadecimal FD (indicates a unique local address)
- Global ID
- Subnet identifier
- Interface identifier

---

## EUI-64 Identifier Generation

3 steps to convert a MAC address into an EUI-64 identifier:
1. Divide the MAC address in half  
2. Insert FFFE in the middle  
3. Invert the 7th bit  

---

## Address Communication Types

- Broadcast addresses provide one-to-all communication  
- Multicast addresses provide one-to-many communication  
- Unicast addresses provide one-to-one communication  
- Anycast addresses provide one-to-one-of-many communication  

---

## IPv6 Address Facts

- An IPv6 address contains 8 hexadecimal quartets.  
- An IPv6 address is 128 bits in length.  
- To shorten an IPv6 address, you can remove leading 0s from each quartet.  
- Typically, an enterprise requesting IPv6 addresses will receive a /48 block of addresses.  
- Typically, IPv6 subnets use a /64 prefix length.  
- IPv6 unique local addresses begin with FD.  

---

## MAC Address U/L Bit

- If the U/L bit of a MAC address is 0, it is a UAA.  
- If the U/L bit of a MAC address is 1, it is a LAA.  

---

## IPv6 Address Categories

- IPv6 unique local addresses are like private IPv4 addresses.  
- IPv6 global unicast addresses are like public IPv4 addresses.  
- IPv6 link-local addresses begin with FE80  
- The IPv6 global unicast range was originally defined as 2000::/3 (now it includes all addresses which aren't reserved for other purposes)  

---

## Duplicate Address Detection (DAD)

- Duplicate Address Detection (DAD) allows hosts to check if other devices on the local link are using the same IPv6 address.  

---

## Static Routes

- In a directly attached static route, the exit interface (only) is specified.  
- In a fully specified static route, the exit interface and next hop are both specified.  
- In a recursive static route, the next hop (only) is specified.  
- In IPv6, you can't use directly attached static routes if the interface is an Ethernet interface. (the command will work but the route will not)  
- To use an IPv6 link-local address as a next hop, you must configure a fully specified static route.  

---

## IPv6 Global Unicast Structure

**What are the three sections of an IPv6 global unicast address?**  
- Global routing prefix  
- Subnet identifier  
- Interface identifier  

---

## IPv6 Q&A

Q: How is the interface ID of an IPv6 link-local address generated?  
A: EUI-64

Q: Which RIR controls IP address assignments in Africa?  
A: AFRINIC

Q: Which RIR controls IP address assignments in Asia-Pacific?  
A: APNIC

Q: Which RIR controls IP address assignments in Canada, many Caribbean and North Atlantic islands, and the US?  
A: ARIN

Q: Which RIR controls IP address assignments in Europe, the Middle East, and parts of Central Asia?  
A: RIPE NCC

Q: Which RIR controls IP address assignments in Latin America and the Caribbean?  
A: LACNIC

Q: Does IPv6 use broadcast messages?  
A: No

Q: MAC addresses: What does LAA stand for?  
A: Locally Administered Address

Q: MAC addresses: What does UAA stand for?  
A: Universally Administered Address

Q: What does EUI stand for?  
A: Extended Unique Identifier

Q: What IPv6 address block is reserved for link-local addresses?  
A: FE80::/10

Q: What IPv6 address block is reserved for unique local addresses?  
A: FC00::/7

Q: What IPv6 address range is reserved for multicast addresses?  
A: FF00::/8

Q: What is the 7th bit of a MAC address called?  
A: U/L bit (Universal/Local bit)

Q: What is the IPv6 loopback address?  
A: ::1

Q: What is the IPv6 unspecified address?  
A: ::

Q: What is the size of the 'global ID' of an IPv6 unique local address?  
A: 40 bits

Q: What is the typical size of the 'global routing prefix' of an IPv6 global unicast address?  
A: 48 bits

Q: What is the typical size of the 'interface identifier' of an IPv6 global unicast address?  
A: 64 bits

Q: What is the typical size of the 'subnet identifier' of an IPv6 global unicast address?  
A: 16 bits

Q: Are routes for IPv6 link-local addresses added to the routing table?  
A: No

Q: How is an IPv6 solicited-node multicast address calculated from a unicast address?  
A: ff02::1:ff + Last 6 hex digits of unicast address

Q: To perform DAD, which address does a device send an NS to?  
A: Its own solicited-node multicast address

Q: What does DAD stand for?  
A: Duplicate Address Detection

Q: What does NDP stand for?  
A: Neighbor Discovery Protocol

Q: What does SLAAC stand for?  
A: Stateless Address Auto-configuration

Q: What does the NDP 'NA' message stand for?  
A: Neighbor Advertisement

Q: What does the NDP 'NS' message stand for?  
A: Neighbor Solicitation

Q: What does the NDP 'RA' message stand for?  
A: Router Advertisement

Q: What does the NDP 'RS' message stand for?  
A: Router Solicitation

Q: What is the length of the IPv6 header?  
A: 40 bytes

Q: When trying to learn a MAC address, what destination IP address are NDP NS messages sent to?  
A: The neighbor's solicited-node multicast address

Q: When using SLAAC, how is the interface ID generated?  
A: EUI-64, or randomly

Q: Which IPv6 header field functions like the IPv4 TTL field?  
A: Hop Limit

Q: Which IPv6 header field indicates the encapsulated Layer 4 protocol?  
A: Next Header

Q: Which IPv6 header field indicates the length of the encapsulated Layer 4 segment?  
A: Payload Length

Q: Which IPv6 header field indicates the version of IP?  
A: Version

Q: Which IPv6 header field is used for QoS?  
A: Traffic Class

Q: Which IPv6 header field is used to identify specific traffic flows?  
A: Flow Label

Q: Which NDP messages allow a device to learn the network prefix for SLAAC?  
A: RS/RA

Q: Which NDP messages does DAD use?  
A: NS/NA

Q: Which protocol replaces ARP in IPv6?  
A: NDP

---

## NDP Multicast Address Targets

- NDP RA messages are sent to FF02::1  
- NDP RS messages are sent to FF02::2
