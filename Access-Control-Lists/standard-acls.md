**# Access Control Lists (ACLs) – Notes

### Core Concepts
- **How many ACLs can be applied to a single interface?**  
  Two: one inbound, one outbound.

- **ACLs must be applied to an interface** to take effect.
- **ACLs are an ordered sequence of ACEs** (Access Control Entries).
- **ACLs can be applied** to an interface **inbound or outbound**.
- **Routers process ACEs from top to bottom**, stopping at the first match.
- **The implicit deny** means that **any packet not explicitly permitted is dropped**.
- When a packet **matches an ACE**, the router **ignores the rest** of the ACL.

---

### Standard vs. Extended ACLs

| Type         | Matching Criteria                           | Placement Recommendation                    |
|--------------|---------------------------------------------|---------------------------------------------|
| **Standard** | Source IP address only                      | As close to the **destination** as possible |
| **Extended** | Source & destination IP + L4 port (TCP/UDP) | As close to the **source** as possible      |

---

### Number Ranges

| ACL Type          | Number Range     |
|-------------------|------------------|
| Standard Numbered | 1–99, 1300–1999  |
| Extended Numbered | 100–199, 2000–2699 |

---

### Common Questions

- **Q: In what order do routers check the ACEs of an ACL?**  
  A: Top to bottom

- **Q: What does ACL stand for?**  
  A: Access Control List

- **Q: What happens if a packet doesn’t match any ACE?**  
  A: It is dropped due to the implicit deny.

- **Q: What happens after a packet matches an ACE?**  
  A: All remaining ACEs are ignored.

