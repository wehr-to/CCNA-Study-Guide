| Purpose                                                                 | Command Example                                              |
|-------------------------------------------------------------------------|--------------------------------------------------------------|
| Create a DHCP pool                                                      | `ip dhcp pool POOL_NAME`                                     |
| Configure a DNS server for the DHCP pool                               | `dns-server IP_ADDRESS`                                      |
| Configure a range of addresses to exclude from the DHCP pool           | `ip dhcp excluded-address LOW_IP HIGH_IP`                    |
| Configure the default gateway (router) for the DHCP pool               | `default-router IP_ADDRESS`                                  |
| Configure the domain name for the DHCP pool                            | `domain-name YOUR_DOMAIN.com`                                |
| Configure the lease time for the DHCP pool                             | `lease DAYS HOURS MINUTES` or `lease infinite`               |
| Configure the address range/subnet for the DHCP pool                   | `network IP_ADDRESS SUBNET_MASK` or `network IP_ADDRESS /CIDR`|
| Configure a router interface to get its IP via DHCP (DHCP client)      | `ip address dhcp`                                            |
| Configure a router interface as a DHCP relay agent                     | `ip helper-address IP_ADDRESS`                               |
| Display current DHCP bindings (leased IPs)                             | `show ip dhcp binding`                                       |
| Windows: Renew DHCP IP address                                         | `ipconfig /renew`                                            |
| Windows: Release DHCP IP address                                       | `ipconfig /release`                                          |
