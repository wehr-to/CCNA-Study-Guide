| Purpose                                                      | Command Example                                                             |
|---------------------------------------------------------------|------------------------------------------------------------------------------|
| Clear all dynamic NAT translation entries                     | `clear ip nat translation *`                                                |
| Configure a static source NAT mapping                         | `ip nat inside source static inside-local-ip inside-global-ip`              |
| Configure the NAT **inside** interface                        | `ip nat inside`                                                             |
| Configure the NAT **outside** interface                       | `ip nat outside`                                                            |
| Show NAT statistics                                           | `show ip nat statistics`                                                   |
| Show the NAT translation table                                | `show ip nat translations`                                                 |
| Configure a pool for dynamic NAT                              | `ip nat pool POOL_NAME START_IP END_IP [prefix-length X | netmask MASK]`   |
| Configure dynamic NAT using an access list and a pool         | `ip nat inside source list ACCESS_LIST pool POOL_NAME`                     |
| Configure dynamic PAT using an address pool                   | `ip nat inside source list ACCESS_LIST pool POOL_NAME overload`            |
| Configure dynamic PAT using the router's interface IP         | `ip nat inside source list ACCESS_LIST interface INTERFACE overload`       |
