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

# Spanning Tree Protocol (STP) Protection Commands

| Command                            | Purpose                                                                 | Typical Use Case |
|------------------------------------|-------------------------------------------------------------------------|------------------|
| `spanning-tree guard root`         | Prevents a designated port from becoming a root port. If superior BPDUs are received, the port is put into *inconsistent* state (blocked). | Used on access ports to **enforce root bridge stability** by preventing rogue switches from becoming root. |
| `spanning-tree bpduguard enable`  | Immediately puts the port into *err-disabled* if any BPDU is received. | Used on **access ports** where no switches should be connected (e.g., end-user devices). |
| `spanning-tree bpdufilter enable` | Suppresses sending and receiving BPDUs. Can prevent participation in STP. | Used in **edge** environments but risky, not generally recommended unless you fully trust the connection. |
| `spanning-tree portfast`          | Moves port to forwarding state immediately, skipping listening/learning states. | Used on **access ports** to speed up connection to end devices. Must be used with BPDU Guard to avoid loops. |
| `spanning-tree guard loop`        | Detects unidirectional link failures on point-to-point links. Places port into *inconsistent* state if loop is detected. | Used in **full-duplex links** to detect and prevent logical loops due to unidirectional failures. |

## Example Configuration

```bash
interface FastEthernet0/1
 spanning-tree portfast
 spanning-tree bpduguard enable
 spanning-tree guard root
```
**Q:** What ports does `spanning-tree portfast default` affect?  
**A:** All access ports
