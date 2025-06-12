## EtherChannel Configuration Commands

| Command Purpose                                                  | Mode           | Command                                              |
|------------------------------------------------------------------|----------------|-------------------------------------------------------|
| Configure a Layer 3 EtherChannel                                 | Interface      | `no switchport`                                      |
|                                                                  | Interface      | `channel-group <group> mode <mode>`                  |
| Configure an interface to join an EtherChannel                   | Interface      | `channel-group <number> mode <mode>`                 |
| Configure static EtherChannel                                    | Interface      | `channel-group 1 mode on`                            |
| Configure EtherChannel load-balancing method on the switch       | Global Config  | `port-channel load-balance <method>`                 |
| Manually configure EtherChannel protocol on an interface         | Interface      | `channel-protocol [lacp | pagp]`                     |
| View current EtherChannel load-balancing method                  | Privileged     | `show etherchannel load-balance`                     |
