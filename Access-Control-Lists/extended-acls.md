# Extended ACL Port Matching Options

| Option                        | Description                                      |
|------------------------------|--------------------------------------------------|
| `eq <port-num>`              | Matches a single port                           |
| `neq <port-num>`             | Matches all ports except the specified number   |
| `gt <port-num>`              | Matches all ports greater than the number       |
| `lt <port-num>`              | Matches all ports less than the number          |
| `range <low> <high>`         | Matches a range of ports from low to high       |

# Extended Numbered ACL Ranges

| Range Type         | Range     |
|--------------------|-----------|
| Standard ACLs      | 1–99      |
| Extended ACLs      | 100–199   |
| Extended ACLs (expanded) | 2000–2699 |

# IP Protocol Numbers

| Protocol | Number |
|----------|--------|
| ICMP     | 1      |
| TCP      | 6      |
| UDP      | 17     |
| EIGRP    | 88     |
| OSPF     | 89     |

- You can’t delete individual ACL entries in global config mode.
- You can delete individual ACL entries in named ACL config mode.
