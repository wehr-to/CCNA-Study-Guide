# DNS and IP Configuration Commands

| Platform | Action | Command |
|----------|--------|---------|
| Windows | Clear the DNS cache | `ipconfig /flushdns` |
| Windows | Ping the specified address with a custom number of pings | `ping ip-address -n number` |
| Windows | Show basic IP configuration | `ipconfig` |
| Windows | Show detailed IP configuration | `ipconfig /all` |
| Windows | Show the DNS cache | `ipconfig /displaydns` |

---

| Platform | Action | Command |
|----------|--------|---------|
| Cisco IOS | Configure an entry in the host table | `ip host hostname ip-address` |
| Cisco IOS | Configure the DNS server to use | `ip name-server ip-address` |
| Cisco IOS | Configure the domain name | `ip domain name domain-name` *(or older: `ip domain-name domain-name`)* |
| Cisco IOS | Enable the router to act as a DNS server | `ip dns server` |
| Cisco IOS | Display the host table | `show hosts` |
| Cisco IOS | Enable DNS lookup on the router | `ip domain lookup` *(or older: `ip domain-lookup`)* |
| Cisco IOS | `dns-server 10.1.1.1` | Configure DHCP Clients to use server 10.1.1.1 for name resolution |

