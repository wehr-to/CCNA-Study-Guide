# Access Control Lists (ACLs) 

## Inbound vs Outbound ACLs

| Direction | Description |
|-----------|-------------|
| **Inbound** | ACL is applied **before** the router makes a routing decision. Traffic is filtered as it **enters** the interface. |
| **Outbound** | ACL is applied **after** the routing decision has been made. Traffic is filtered as it **leaves** the interface. |

## Key Differences

- **Inbound ACLs**:
  - Filter traffic **entering** the router interface.
  - Efficient if you want to deny packets before any processing occurs.
  - Ideal for **blocking external threats** or limiting incoming access.

- **Outbound ACLs**:
  - Filter traffic **exiting** the router interface.
  - Packets are already routed, so more processing overhead.
  - Useful for **controlling what internal traffic leaves** a network.

## Example
~~~
# Apply ACL 100 inbound on GigabitEthernet0/1
interface GigabitEthernet0/1
 ip access-group 100 in

# Apply ACL 101 outbound on GigabitEthernet0/2
interface GigabitEthernet0/2
 ip access-group 101 out
~~~

### Core Concepts
- **How many ACLs can be applied to a single interface?**  
  Two: one inbound, one outbound.

- **ACLs must be applied to an interface** to take effect.
- **ACLs are an ordered sequence of ACEs** (Access Control Entries).
- **ACLs can be applied** to an interface **inbound or outbound**.
- **Routers process ACEs from top to bottom**, stopping at the first match.
- **The implicit deny** means that **any packet not explicitly permitted is dropped**.
- When a packet **matches an ACE**, the router **ignores the rest** of the ACL.

### Standard vs. Extended ACLs

| Type         | Matching Criteria                           | Placement Recommendation                    |
|--------------|---------------------------------------------|---------------------------------------------|
| **Standard** | Source IP address only                      | As close to the **destination** as possible |
| **Extended** | Source & destination IP + L4 port (TCP/UDP) | As close to the **source** as possible      |

### Number Ranges

| ACL Type          | Number Range     |
|-------------------|------------------|
| Standard Numbered | 1–99, 1300–1999  |
| Extended Numbered | 100–199, 2000–2699 |

### Common Questions

- **Q: In what order do routers check the ACEs of an ACL?**  
  A: Top to bottom

- **Q: What does ACL stand for?**  
  A: Access Control List

- **Q: What happens if a packet doesn’t match any ACE?**  
  A: It is dropped due to the implicit deny.

- **Q: What happens after a packet matches an ACE?**  
  A: All remaining ACEs are ignored.

## Other Notes: 
- Functions as a packet filter
- Filters on source/destination IP and source/destination L4 Port numbers
- configured in global config mode
- ordered sequence of ACEs (access control entries)
- After being created, they are applied inbound or outbound
- Max of one ACL can be applied to a single interface per direction, it will get replaced if another is added
- Use the wildcard mask (inverse of subnet mask) when specifying IPs in ACLs (especially standard ACLs)
- ACL Remarks are like inline comments

| Subnet Mask     | Wildcard Mask |
| --------------- | ------------- |
| 255.255.255.0   | 0.0.0.255     |
| 255.255.255.128 | 0.0.0.127     |
| 255.255.255.252 | 0.0.0.3       |

## References 
- https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html

