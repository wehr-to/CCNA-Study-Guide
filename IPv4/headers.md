# IPv4 Header and Fragmentation Notes

## General

- A router will drop a packet with a TTL of 0  
- A value of 4 (Binary 0100) in the IP header 'Version' field indicates IP version 4.  
- A value of 6 (Binary 0110) in the IP header 'Version' field indicates IP version 6.  
- IPv4 packets are fragmented if they are larger than the MTU (Maximum Transmission Unit)  
- The MTU is usually 1500 bytes.  
- The recommended default TTL of an IPv4 packet is 64  
- Unfragmented IPv4 packets will always have the MF bit set to 0  
- IPv4 Header: The IHL field specifies the length of the header in 4-byte (32 bit) increments.

## IPv4 Header Field Lengths

| Field                    | Length    |
|--------------------------|-----------|
| Version                  | 4 bits    |
| IHL                      | 4 bits    |
| DSCP                     | 6 bits    |
| ECN                      | 2 bits    |
| Total Length             | 16 bits   |
| Identification           | 16 bits   |
| Flags                    | 3 bits    |
| Fragment Offset          | 13 bits   |
| TTL                      | 8 bits    |
| Protocol                 | 8 bits    |
| Header Checksum          | 16 bits   |
| Source IP Address        | 32 bits   |
| Destination IP Address   | 32 bits   |

## Fragmentation Behavior

- IPv4 header: All fragments of the same packet will have the same value in the identification field.

### IPv4 Header 'Flags' Field

| Bit   | Name       | Meaning                  |
|--------|------------|---------------------------|
| 0      | Reserved   | Always set to 0          |
| 1      | DF         | Don’t Fragment Bit       |
| 2      | MF         | More Fragments Bit       |

## Protocol Field Values

| Protocol | Value |
|----------|-------|
| ICMP     | 1     |
| TCP      | 6     |
| UDP      | 17    |
| OSPF     | 89    |

## Q&A

Q: IPv4 header: What does 'DSCP' stand for?  
A: Differentiated Services Code Point

Q: What does 'DF bit' stand for?  
A: Dont Fragment Bit

Q: What does 'MF bit' stand for?  
A: More Fragments Bit

Q: IPv4 header: What does 'ECN' stand for?  
A: Explicit Congestion Notification

Q: IPv4 header: What does 'IHL' stand for?  
A: Internet Header Length

Q: IPv4 header: What does 'TTL' stand for?  
A: Time to Live

Q: IPv4 header: What is the maximum length of the 'Options' field?  
A: 320 bits / 40 bytes

Q: IPv4 header: What is the maximum value of the 'Total Length' field?  
A: 65,535

Q: IPv4 header: What is the maximum value of the IHL field?  
A: 15

Q: IPv4 header: What is the minimum length of the 'Options' field?  
A: 0 bits

Q: IPv4 header: What is the minimum value of the 'Total Length' field?  
A: 20 (=IPv4 header with no encapsulated data)

Q: IPv4 header: What is the minimum value of the IHL field?  
A: 5

Q: IPv4 header: Which field indicates the protocol of the encapsulated L4PDU?  
A: Protocol

Q: IPv4 header: Which field indicates the total length of the packet?  
A: Total Length

Q: IPv4 header: Which field is used to check for errors in the header?  
A: Header Checksum

Q: IPv4 header: Which field is used to identify which packet a fragment belongs to?  
A: Identification

Q: IPv4 header: Which field is used to indicate the position of a fragment within an original, unfragmented IP packet?  
A: Fragment Offset

Q: IPv4 header: Which field is used to prevent infinite routing loops?  
A: TTL

Q: IPv4 header: Which field is used to prioritize delay-sensitive network traffic?  
A: DSCP

Q: IPv4 header: Which field provides end-to-end notification of network congestion?  
A: ECN

Q: What is the maximum length of the IPv4 header?  
A: 60 Bytes

Q: What is the minimum length of the IPv4 header?  
A: 20 Bytes

| **Field**         | **Length** | **Purpose**                                                   | **Real-World Use / Issue**                                                           |
|------------------|------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Version          | 4 bits     | Specifies IP version (IPv4 = 4, IPv6 = 6)                      | Packets with incorrect version may be dropped by intermediate routers               |
| IHL              | 4 bits     | Internet Header Length (in 32-bit words)                       | Value of 5 = 20 bytes (no options); max = 15 (60 bytes)                             |
| DSCP             | 6 bits     | Differentiated Services Code Point — traffic prioritization    | Used in QoS (e.g., VoIP gets higher priority); misconfigured = poor service         |
| ECN              | 2 bits     | Explicit Congestion Notification                               | Allows routers to signal congestion without dropping packets                        |
| Total Length     | 16 bits    | Total size of IP packet (header + data)                        | Max = 65,535 bytes; MTU mismatch = fragmentation or drops                           |
| Identification   | 16 bits    | Identifies fragments belonging to the same packet              | Used to reassemble fragments — all fragments share the same ID                      |
| Flags            | 3 bits     | Bit 0 = Reserved, Bit 1 = DF (Don’t Fragment), Bit 2 = MF (More Fragments) | DF = don’t fragment — can break apps if MTU not accounted for                      |
| Fragment Offset  | 13 bits    | Shows position of a fragment in the original payload           | Improper reassembly = corrupted packet                                               |
| TTL              | 8 bits     | Time To Live — max hops before being dropped                   | Prevents routing loops; traceroute relies on TTL                                     |
| Protocol         | 8 bits     | Specifies Layer 4 protocol (1=ICMP, 6=TCP, 17=UDP, 89=OSPF)     | Used to decide which transport protocol to use                                       |
| Header Checksum  | 16 bits    | Error-checking for the IPv4 header only                        | Routers recalculate this; corrupted headers = packet dropped                        |
| Source IP        | 32 bits    | Where the packet came from                                     | Used in routing, NAT, ACLs, logging                                                 |
| Destination IP   | 32 bits    | Where the packet is going                                      | Must match target — misroute = blackhole                                            |
| Options          | Variable   | Used for rare features (e.g., source routing)                  | Increases header size; almost never used today                                       |

| **Acronym** | **Stands For**                       | **Plain Meaning**                                                                 |
|------------|--------------------------------------|-----------------------------------------------------------------------------------|
| TTL        | Time To Live                         | Limits how many routers a packet can cross before being dropped (prevents loops) |
| IHL        | Internet Header Length               | Tells how long the IPv4 header is (in 32-bit chunks)                             |
| DSCP       | Differentiated Services Code Point   | QoS value for prioritizing certain types of traffic (e.g., VoIP)                 |
| ECN        | Explicit Congestion Notification     | Notifies endpoints of congestion without dropping packets                        |
| MF         | More Fragments                       | If set to 1, more fragments of the packet are coming                             |
| DF         | Don't Fragment                       | If set to 1, routers must not fragment this packet (or else drop it)             |
| FCS        | Frame Check Sequence                 | Ethernet trailer that detects bit errors in frames (uses CRC)                   |
| CRC        | Cyclic Redundancy Check              | The math algorithm used by FCS to detect errors                                  |
| PDU        | Protocol Data Unit                   | A generic term for data at each OSI layer (IP packet = L3 PDU)                   |

| **Acronym** | **Stands For**                     | **Plain Meaning**                                                            |
|------------|------------------------------------|------------------------------------------------------------------------------|
| ICMP       | Internet Control Message Protocol  | Used for ping, traceroute, error messaging                                  |
| TCP        | Transmission Control Protocol      | Reliable, connection-oriented transport protocol                            |
| UDP        | User Datagram Protocol             | Fast, connectionless transport protocol                                     |
| OSPF       | Open Shortest Path First           | Link-state routing protocol (uses Protocol = 89)                            |
| MTU        | Maximum Transmission Unit          | Largest size a packet can be without needing fragmentation                  |
| MAC        | Media Access Control               | Layer 2 address used in LAN communication (physical address)                |
| NAT        | Network Address Translation        | Translates private IPs to public ones for internet access                   |
