# Dynamic ARP Inspection (DAI) Command Reference

| **Function**                                           | **Command**                                                                 |
|--------------------------------------------------------|------------------------------------------------------------------------------|
| Apply an ARP ACL to DAI                                | `ip arp inspection filter arp-acl-name vlan vlan`                            |
| Configure a DAI trusted interface                      | `ip arp inspection trust`                                                   |
| Configure an ARP ACL entry mapping IP to MAC (permit)  | `permit ip host ip-address mac host mac-address`                            |
| Configure DAI rate limiting                            | `ip arp inspection limit rate packets [burst interval seconds]`             |
| Create an ARP ACL                                      | `arp access-list name`                                                      |
| Enable additional DAI validation checks                | `ip arp inspection validate (src-mac | dst-mac | ip)`                        |
| Enable DAI for a VLAN                                  | `ip arp inspection vlan vlan`                                               |
| Enable err-disable recovery for DAI rate limiting      | `errdisable recovery cause arp-inspection`                                  |
| Show a summary of DAI configuration and statistics     | `show ip arp inspection`                                                    |
| Show a summary of DAI interfaces                       | `show ip arp inspection interfaces`                                         |
