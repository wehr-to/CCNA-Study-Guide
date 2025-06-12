## Unicast

- A Unicast frame is a frame destined for a single target.  
- A switch will flood an unknown unicast frame.  
- The ARP Reply message is unicast  
- The ARP Request message is broadcast  

**Q: What does a switch do with an unknown unicast frame?**  
- Floods it out all ports (except the one it was received on)

**Unknown Unicast:**  
When a switch receives a unicast frame but doesn't know the destination MAC address, it will flood the frame out all ports (except the one it was received on). This allows the destination device to respond, so the switch can learn its MAC address and add it to the MAC address table.

### Values

**Q: A value of 1536 or greater in the Type/Length field indicates Type.**  
- 1536 / OFTEN USED IN ETHERNET II FRAMES

**Q: A value of 1500 or less in the Type/Length field indicates Length.**  
- 1500 / OFTEN USED IN ETHERNET 802.3 FRAMES

---

## MAC Addresses

**Q: What does MAC stand for?**  
- Media Access Control

**Q: What is another name for a MAC address?**  
- BIA (Burned-In Address)

**Q: A MAC address is written as 12 / TWELVE hexadecimal characters.**

**Q: A MAC address learned by a switch without manual configuration is called a...**  
- Dynamic MAC address (Dynamically learned MAC address)

**Q: By default, a dynamic MAC address will be removed from the MAC address table after 5 Minutes of inactivity.**

**Q: How long is a MAC address?**  
- 48 bits  
- 6 bytes / THINK SIX TIMES EIGHT IS 48

**Q: The first 3 bytes of a MAC address are the OUI (Organizationally Unique Identifier)**

**Q: The process of addresses being cleared from the MAC address table after 5 minutes of inactivity is known as...**  
- Aging

**Q: What is the broadcast MAC address?**  
- FFFF.FFFF.FFFF

**Q: What protocol is used to discover the Layer 2 address of another device?**  
- ARP (Address Resolution Protocol)  
- ARP is used to find a Layer 2 (MAC) address when you only know the Layer 3 (IP) address.

**Q: What two messages are used in ARP?**  
1. ARP Request  
2. ARP Reply  

**ARP (Address Resolution Protocol):**  
- ARP Request: Sent as a broadcast (FFFF.FFFF.FFFF) to all devices in the subnet to ask “Who has this IP address?”  
- ARP Reply: Sent as a unicast to the requester — “I have that IP, here is my MAC address.”  
- This behavior is crucial for understanding how devices learn each other’s MAC addresses dynamically on a LAN.

**Q: What two messages are used in ping?**  
1. ICMP Echo Request  
2. ICMP Echo Reply

---

## Ethernet Headers & Trailers

| Ethernet Field          | Bytes     | Location   |
|-------------------------|-----------|------------|
| Preamble                | 7 bytes   | Header     |
| SFD (Start Frame Delim) | 1 byte    | Header     |
| Destination Address     | 6 bytes   | Header     |
| Source Address          | 6 bytes   | Header     |
| Type/Length             | 2 bytes   | Header     |
| FCS (Frame Check Seq.)  | 4 bytes   | Trailer    |

**Q: What are the 5 fields of an Ethernet header?**  
GOT Acronym for the order: **People Should Defend Strong Thrones**

1. Preamble = Not part of the "Ethernet header" strictly — syncs the receiver  
2. SFD = Marks the start of the actual frame / END OF THE PREAMBLE  
3. Destination = First field of the Ethernet header  
4. Source = Second field of the header  
5. Type/Length = Final field of the header

**Bit Pattern of one byte in the Ethernet preamble?**  
- 10101010

**Bit pattern of the Ethernet SFD?**  
- 10101011

**Q: What does 'FCS' in an Ethernet frame stand for?**  
- Frame Check Sequence

**Q: What does 'SFD' in an Ethernet header stand for?**  
- Start Frame Delimiter

**Q: What is the only field in an Ethernet trailer?**  
- FCS (Frame Check Sequence)

**Q: What kind of algorithm does the Ethernet FCS use?**  
- CRC (Cyclic Redundancy Check)

**Q: Which field of an Ethernet frame does a switch use to learn and populate its MAC address table?**  
- Source MAC Address

---

### Ethernet Frame Properties

| Question                                                  | Answer     |
|-----------------------------------------------------------|------------|
| What is the Ethernet Type code for an ARP packet?         | 0x0806     |
| What is the minimum size of an Ethernet frame?            | 64 Bytes   |
| What is the minimum size of an Ethernet payload?          | 46 Bytes   |
| What is the size of the Ethernet header + trailer?        | 18 Bytes   |
| (no Preamble + SFD)                                       |            |

---

## Example Problem: Convert 197 to Hex

1. 197 / 16 = 12 with a remainder of 5  
2. 12 / 16 = 0, remainder of 12  
Now map remainder 12 to hex → **C**

Your remainders are:
- 12 → C  
- 5 → 5  
- Reverse the remainders: 197 = **C5**

_(With Decimal to Hex, you divide by 16 repeatedly)_

---

### Number System Conversion Table

| Conversion Type       | Method                     |
|------------------------|----------------------------|
| Decimal to Hex         | Divide by 16 repeatedly    |
| Decimal to Binary      | Divide by 2 repeatedly     |
| Decimal to Octal       | Divide by 8 repeatedly     |

---

### Ethernet Type Codes

| Question                                             | Answer   |
|------------------------------------------------------|----------|
| What is the Ethernet Type value for IPv4? (hex)      | 0x0800   |
| What is the Ethernet Type value for IPv6? (hex)      | 0x86DD   |



