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

# Standard ACL Command Reference (Cisco IOS)

| Purpose                                                    | Mode               | Command Syntax                                                                |
|------------------------------------------------------------|--------------------|--------------------------------------------------------------------------------|
| Apply an ACL to an interface                               | `config-if`        | `ip access-group <acl-number-or-name> {in | out}`                             |
| Configure a permit or deny entry (standard named ACL)      | `config-std-nacl`  | `[sequence-number] {permit | deny} <ip> <wildcard-mask>`                      |
| Configure a remark for a standard numbered ACL             | `config`           | `access-list <number> remark <remark>`                                        |
| Permit or deny all source IPs in a standard numbered ACL   | `config`           | `access-list <number> {permit | deny} any`                                    |
| Specify IP/wildcard in a standard numbered ACL entry       | `config`           | `access-list <number> {permit | deny} <ip> <wildcard-mask>`                   |
| Enter standard named ACL configuration mode                | `config`           | `ip access-list standard <acl-name>`                                          |
| View all ACLs on the router                                | `exec`             | `show access-lists`                                                           |
| View all IP ACLs on the router                             | `exec`             | `show ip access-lists`                                                        |


# Extended ACL Commands Table

| Purpose                                                 | Mode                        | Command                                                                                  |
|---------------------------------------------------------|-----------------------------|-------------------------------------------------------------------------------------------|
| Configure numbered extended ACL entry                   | Global Config               | `access-list <number> {permit | deny} <protocol> <src-ip wildcard> <dest-ip wildcard>`  |
| Configure numbered extended ACL with ports              | Global Config               | `access-list <number> {permit | deny} <protocol> <src-ip wildcard> eq <src-port> <dest-ip wildcard> eq <dest-port>` |
| Enter named extended ACL configuration mode             | Global Config               | `ip access-list extended <name>`                                                         |
| Configure named extended ACL entry                      | Named ACL Config (`config-ext-nacl`) | `{permit | deny} <protocol> <src-ip wildcard> [operator <src-port>] <dest-ip wildcard> [operator <dst-port>]` |
| Permit or deny all IP traffic                           | Any ACL Config Mode         | `{permit | deny} ip any any`                                                             |
| Add remark to a named extended ACL                      | Named ACL Config            | `remark <text>`                                                                          |
| Delete an entry by sequence number                      | Named ACL Config            | `no <sequence-number>`                                                                   |
| Resequence ACL entries                                  | Global Config               | `ip access-list resequence <acl-name-or-number> <start> <increment>`                    |
| Apply ACL to an interface                               | Interface Config (`config-if`) | `ip access-group <acl-name-or-number> {in | out}`                                      |
| View ACLs applied to interface                          | Exec Mode                   | `show ip interface <interface-id>`                                                       |
| View all ACLs on the device                             | Exec Mode                   | `show access-lists`                                                                      |
| View all IP ACLs specifically                           | Exec Mode                   | `show ip access-lists`                                                                   |
