| Purpose                                                        | Mode             | Command                                                                 |
|----------------------------------------------------------------|------------------|-------------------------------------------------------------------------|
| Configure spanning tree in PVST mode                           | Global config     | `spanning-tree mode pvst`                                              |
| Set the primary root bridge for a VLAN                         | Global config     | `spanning-tree vlan <vlan-id> root primary`                            |
| Set the secondary root bridge for a VLAN                       | Global config     | `spanning-tree vlan <vlan-id> root secondary`                          |
| Set STP cost of an interface for a specific VLAN               | Interface config  | `spanning-tree vlan <vlan-id> cost <cost>`                             |
| Set STP port priority of an interface for a specific VLAN      | Interface config  | `spanning-tree vlan <vlan-id> port-priority <priority>`                |
| Enable BPDU Guard on a specific port                           | Interface config  | `spanning-tree bpduguard enable`                                       |
| Enable BPDU Guard on all PortFast-enabled interfaces           | Global config     | `spanning-tree portfast bpduguard default`                             |
| Enable PortFast on a specific interface                        | Interface config  | `spanning-tree portfast`                                               |
| Enable PortFast on all access ports on the switch              | Global config     | `spanning-tree portfast default`                                       |

**Q:** What ports does `spanning-tree portfast default` affect?  
**A:** All access ports
