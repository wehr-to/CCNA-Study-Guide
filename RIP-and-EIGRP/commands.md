# RIP & EIGRP Command Reference

| Purpose | Command |
|---------|---------|
| Configure a RIP-enabled router to advertise its default route to its RIP neighbors | `default-information originate` |
| Configure the EIGRP router ID | `eigrp router-id a.b.c.d` |
| Prevent RIP advertisements from being sent out a RIP-enabled interface | `passive-interface interface-id` |
| Disable EIGRP auto summarization | `no auto-summary` |
| Disable RIP auto summarization | `no auto-summary` |
| Enable EIGRP on interfaces in the specified range | `network ip-address [ wildcard-mask ]` |
| Enable RIP on all interfaces in the specified range | `network ip-address` |
| Enable RIPv2 | `version 2` |
| Enter EIGRP configuration mode | `router eigrp as-number` |
| Enter RIP configuration mode | `router rip` |
| Modify RIP's Administrative Distance | `distance value` |
| Modify number of ECMP paths RIP will use | `maximum-paths number` |
| Prevent EIGRP messages from being sent out an EIGRP-enabled interface | `passive-interface interface-id` |
