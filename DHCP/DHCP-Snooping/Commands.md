| Purpose                                                                 | Command Example                                             |
|-------------------------------------------------------------------------|-------------------------------------------------------------|
| Enable DHCP Snooping globally on the switch                            | `ip dhcp snooping`                                          |
| Enable DHCP Snooping for a specific VLAN                               | `ip dhcp snooping vlan VLAN_NUMBER`                         |
| Configure an interface as a trusted DHCP Snooping port                 | `ip dhcp snooping trust`                                    |
| Limit DHCP message rate on an interface (rate-limiting)                | `ip dhcp snooping limit rate PACKETS_PER_SECOND`            |
| Prevent the switch from inserting option 82 into DHCP packets          | `no ip dhcp snooping information option`                    |
| Enable errdisable recovery for DHCP rate-limit violations              | `errdisable recovery cause dhcp-rate-limit`                 |
| Show the DHCP Snooping binding table                                   | `show ip dhcp snooping binding`                             |
