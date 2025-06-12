# IPv6 Configuration Commands

| Task | Command |
|------|---------|
| Configure an IPv6 address on an interface | `R1(config-if)# ipv6 address address/prefix-length` |
| Enable IPv6 routing on the router | `R1(config)# ipv6 unicast-routing` |
| Configure an IPv6 address using EUI-64 | `R1(config-if)# ipv6 address prefix/prefix-length eui-64` |
| Configure an IPv6 anycast address | `R1(config-if)# ipv6 address address/prefix-length anycast` |
| Enable IPv6 on an interface without manually configuring an address | `R1(config-if)# ipv6 enable` |
| Configure an IPv6 directly attached static route | `R1(config)# ipv6 route destination/prefix-length exit-interface` |
| Configure an IPv6 fully specified static route | `R1(config)# ipv6 route destination/prefix-length exit-interface next-hop` |
| Configure an IPv6 recursive static route | `R1(config)# ipv6 route destination/prefix-length next-hop` |
| View the IPv6 equivalent of an ARP table | `R1# show ipv6 neighbor` |

---

**Q: To shorten an IPv6 address, you can replace consecutive quartets of all 0s with a [...].**  
**A:** double colon `(::)`  
*Can only do this once per address*
