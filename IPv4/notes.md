Q: If the host portion of an IPv4 address is all 0s, what kind of address is it?  
Network Address  
Q: If the host portion of an IPv4 address is all 1s, what kind of address is it?  
Broadcast Address  

Q: IPv4 addresses beginning with 127 are used for loopback addresses.  

Q: What kind of address is used to test the network software stack on the local device?  
Loopback Address  

Q: What are the groups of 8 bits in an IP address called?  
Octets  
Q: What is the class D IPv4 address range reserved for?  
Multicast Addresses  
Q: What is the class E IPv4 address range reserved for?  
Experimental Purposes (Think E for Experimental)  

Q: What is the length of an IP address? (bits)  
32 Bits  
Q: What is the length of an IP address? (bytes)  
4 Bytes  
Q: What is the maximum value for a binary octet? (1111 1111)  
255  

---

### Prefix Lengths & Netmasks

Q: If an interface has the shutdown command applied to it, what will the 'status' column of show ip interface brief display?  
administratively down  
Q: Interfaces on Cisco [device type] are administratively down by default.  
Routers  
Q: Interfaces on Cisco [device type] are NOT administratively down by default.  
Switches  

The Status field of the show ip interface brief command shows the Layer 1 status of the interface.  
The Protocol field of the show ip interface brief command shows the Layer 2 status of the interface.  
The 'Protocol' field of the show ip interface brief command shows the Layer 2 status of the interface.  
The 'Status' field of the show ip interface brief command shows the Layer 1 status of the interface.  

---

### Formulas

Q: What is the formula to calculate the maximum number of hosts in a network?  
(2^n)-2  
(n = number of host bits)  

---

### Classes:

**A**  
Q: Which IPv4 address class allows a total of 16,777,214 hosts per network?  
Class A  
Q: Which IPv4 address class contains a total of 128 networks?  
Class A  

**B**  
Q: Which IPv4 address class allows a total of 65,534 hosts per network?  
Class B  
Q: Which IPv4 address class contains a total of 16,384 networks?  
Class B  

**C**  
Q: Which IPv4 address class allows a total of 254 hosts per network?  
Class C  
Q: Which IPv4 address class contains a total of 2,097,152 networks?  
Class C  

---

### Host Calculation Formula

**Max hosts per subnet = (2^n) - 2**  
Where `n` = number of host bits  
We subtract 2 for:  
- All 0s → Network address  
- All 1s → Broadcast address  

**Examples:**  
- /24 = 8 host bits → (2^8)-2 = 254  
- /16 = 16 host bits → (2^16)-2 = 65,534  

| **Address**                        | **Purpose**                              |
|-----------------------------------|------------------------------------------|
| 127.0.0.1 to 127.255.255.255      | Reserved for loopback (local host testing) |
| 127.0.0.1                         | Most common — used to test a device’s TCP/IP stack |

| **Class** | **First Octet Range** | **Bit Pattern** | **Default Prefix** | **Hosts per Network** | **Networks**  |
|-----------|------------------------|------------------|---------------------|------------------------|----------------|
| A         | 0–127                  | 0xxxxxxx         | /8                  | 16,777,214             | 128            |
| B         | 128–191                | 10xxxxxx         | /16                 | 65,534                 | 16,384         |
| C         | 192–223                | 110xxxxx         | /24                 | 254                    | 2,097,152      |
| D         | 224–239                | 1110xxxx         | Multicast           | N/A                    | N/A            |
| E         | 240–255                | 1111xxxx         | Experimental        | N/A                    | N/A            |

| **CIDR** | **Subnet Mask**   | **Class Default** |
|----------|-------------------|-------------------|
| /8       | 255.0.0.0         | Class A           |
| /16      | 255.255.0.0       | Class B           |
| /24      | 255.255.255.0     | Class C           |

| **Status**           | **Protocol** | **What It Means**                                                                 |
|----------------------|--------------|----------------------------------------------------------------------------------|
| administratively down| down         | Interface has been manually shut down with the `shutdown` command               |
| up                   | down         | Layer 1 is good, but Layer 2 config issue (e.g., encapsulation mismatch)        |
| down                 | down         | No physical connection (cable unplugged, device off, or speed/duplex mismatch)  |
| up                   | up           | Everything is working correctly                                                  |

| **Device Type** | **Default Interface State**      | **Why?**                                                                 |
|------------------|----------------------------------|-------------------------------------------------------------------------|
| Routers          | administratively down (off)      | Routers don’t auto-enable interfaces — you enable and IP them manually |
| Switches         | up (enabled by default)          | Switchports are active by default to support plug-and-play device connections |
