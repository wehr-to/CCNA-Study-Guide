# EtherChannel and LACP Notes

- **LACP** is defined by **IEEE 802.3ad**.
- The EtherChannel `channel-group` number doesn’t have to match on neighboring switches.

## EtherChannel Facts

**Q: How many interfaces can be active in an EtherChannel?**  
A: 8

**Q: What are the 6 EtherChannel load-balancing methods (not including TCP/IP port numbers)?**  
1. Source MAC  
2. Destination MAC  
3. Source/Destination MAC  
4. Source IP  
5. Destination IP  
6. Source/Destination IP

## Acronyms

- **LACP** = Link Aggregation Control Protocol  
- **LAG (EtherChannel)** = Link Aggregation Group  
- **PAgP** = Port Aggregation Protocol

## EtherChannel Protocols

**Q: Which EtherChannel protocol allows up to 8 active interfaces and up to 8 standby interfaces?**  
A: LACP

**Q: Which method of EtherChannel configuration uses a Cisco proprietary protocol?**  
A: PAgP

**Q: Which method of EtherChannel configuration uses an industry standard protocol?**  
A: LACP

**Q: Which two EtherChannel modes does LACP use?**  
1. Active  
2. Passive

**Q: Which two EtherChannel modes does PAgP use?**  
1. Desirable  
2. Auto
