# First Hop Redundancy Protocol (FHRP) Notes

FHRP-activated routers communicate with each other by sending multicast Hello messages.  
GLBP multicast IPv4 address: 224.0.0.102  
GLBP: A single Active Virtual Gateway (AVG) is elected.  
GLBP: The AVG assigns up to four Active Virtual Forwarders (AVFs).  
Gratuitous ARP messages are broadcast.  
HSRP uses Active and Standby routers.  
In Gratuitous ARP, an ARP reply is sent without being requested.  
VRRP multicast IPv4 address: 224.0.0.18  
VRRP uses Master and Backup routers.  
When the HSRP standby router switches to the active role, it will send gratuitous ARP messages.

HSRPv1 multicast IPv4 address: 224.0.0.2  
HSRPv2 multicast IPv4 address: 224.0.0.102

## FHRP Questions & Answers

**Q: Is GLBP Cisco proprietary?**  
Yes

**Q: Is HSRP Cisco proprietary?**  
Yes

**Q: Is preemption enabled on FHRPs by default?**  
No

**Q: Is VRRP Cisco proprietary?**  
No

**Q: What does 'FHRP' stand for?**  
First Hop Redundancy Protocol

**Q: What does 'GLBP' stand for?**  
Gateway Load Balancing Protocol

**Q: What does 'HSRP' stand for?**  
Hot Standby Router Protocol

**Q: What does 'VRRP' stand for?**  
Virtual Router Redundancy Protocol

**Q: What is the default HSRP priority?**  
100

**Q: When using an FHRP, what IP address should be configured as the default gateway for hosts in the subnet?**  
The virtual IP address

**Q: When using an FHRP, what MAC address does the active router use to respond to ARP requests?**  
The virtual MAC address

**Q: Which FHRP load balances among multiple routers within a single subnet?**  
GLBP

## HSRP Active Router Election Order

1. Highest priority  
2. Highest IP address

## Virtual MAC Address Formats

**GLBP virtual MAC address format:**  
`0007.b400.XXYY`  
(XX = GLBP group number, YY = AVF number)

**HSRPv1 virtual MAC address format:**  
`0000.0c07.acXX`  
(XX = HSRP group number)

**HSRPv2 virtual MAC address format:**  
`0000.0c9f.fXXX`  
(XXX = HSRP group number)

**VRRP virtual MAC address format:**  
`0000.5e00.01XX`  
(XX = VRRP group number)
