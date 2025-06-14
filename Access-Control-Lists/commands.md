# Extended ACL Commands Table

| Purpose | Mode | Command |
|--------|------|---------|
| Configure an extended ACL entry with protocol, source, and destination IP | Global Config | `access-list <number> {permit | deny} <protocol> <src-ip> <dest-ip>` <br> *(Use `host` for /32 or specify wildcard mask)* |
| Configure an extended ACL entry with protocol, source, and destination IP | ACL Config (`config-ext-nacl`) | `{permit | deny} <protocol> <src-ip> <dest-ip>` <br> *(Use `host` for /32 or specify wildcard mask)* |
| Permit or deny all traffic | ACL Config (`config-ext-nacl`) | `{permit | deny} ip any any` |
| Delete an ACL entry by sequence number | ACL Config (`config-std-nacl`) | `no <sequence-number>` |
| Enter extended named ACL configuration mode | Global Config | `ip access-list extended <name or number>` |
| Resequence ACL line numbers | Global Config | `ip access-list resequence <acl-id> <start> <increment>` |
| Create extended ACL entry with protocol, IPs, and ports | ACL Config (`config-ext-nacl`) | `{permit | deny} <protocol> <src-ip> <operator src-port> <dest-ip> <operator dst-port>` <br> *(Use `host` or wildcard for IPs; use `eq`, `range`, etc. for ports)* |
| View ACLs applied to an interface | Exec Mode | `show ip interface <interface-id>` |

