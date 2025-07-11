| Purpose                             | Command Example                                      |
| ----------------------------------- | ---------------------------------------------------- |
| Show routing table                  | `show ip route`                                      |
| Configure default route (next-hop)  | `ip route 0.0.0.0 0.0.0.0 192.168.1.254`             |
| Static route (next-hop only)        | `ip route 10.0.0.0 255.255.255.0 192.168.1.2`        |
| Static route (exit-interface)       | `ip route 10.0.0.0 255.255.255.0 GigabitEthernet0/0` |
| Static route (next-hop + interface) | `ip route 10.0.0.0 255.255.255.0 Gig0/0 192.168.1.2` |
| Identify intermittent connectivity | `show interface status` |

`show interface status` is primarily looking for speed and duplex mismatches
