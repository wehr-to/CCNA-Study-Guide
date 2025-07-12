## Cisco NAT Terminology

- Inside Local: The IP address of the inside host from the perspective of the inside network.
- Inside Global: The IP address of the inside host from the perspective of the outside network.
- Outside Local: The IP address of the outside host from the perspective of the inside network.
- Outside Global: The IP address of the outside host from the perspective of the outside network.

- Static NAT involves statically configuring one-to-one IP address mappings.
- Private IPv4 addresses are defined in RFC 1918.
- Static Source NAT = Inside Local address is mapped to Inside Global address.
- When only source NAT is used, in the output of `show ip nat translations`, you can expect the Outside Local and Outside Global addresses to be the same.

## Q&A Review

**Q: Can private IPv4 addresses be used over the Internet?**  
- No

**Q: What does NAT stand for?**  
- Network Address Translation

**Q: What is the class A range of private IPv4 addresses?**  
- 10.0.0.0/8

**Q: What is the class B range of private IPv4 addresses?**  
- 172.16.0.0/12

**Q: What is the class C range of private IPv4 addresses?**  
- 192.168.0.0/16

**Q: In dynamic NAT, what is used to identify the range of public IP address that can be used for translations?**  
- A NAT pool

**Q: In dynamic NAT/PAT, what is used to identify traffic that should be translated?**  
- An ACL

**Q: In which form of NAT are multiple inside local addresses translated to a single inside global address at the same time?**  
- PAT / NAT Overload

**Q: In which form of NAT does the router automatically create one-to-one IP address mappings?**  
- Dynamic NAT

**Q: What does a router do if a packet requires NAT but no inside global addresses are available?**  
- It drops the packet

**Q: What does PAT stand for?**  
- Port Address Translation

**Q: What is another name for PAT?**  
- NAT Overload

**Q: When an ACL is used to identify traffic in dynamic NAT/PAT, what happens to traffic denied by the ACL?**  
- It is not translated by the router (but the traffic is not dropped!)

**Q: Which form of NAT is most useful for preserving public IP addresses?**  
- PAT / NAT Overload

