# VLAN and Interface Configuration Commands

| **Function**                                               | **Mode**             | **Command**                                                |
|------------------------------------------------------------|----------------------|-------------------------------------------------------------|
| Configure a switch interface to be an access port          | SW1(config-if)#      | `switchport mode access`                                   |
| Configure the name of a VLAN                               | SW1(config-vlan)#    | `name name`                                                 |
| Configure the VLAN of a switch access port                 | SW1(config-if)#      | `switchport access vlan vlan-number`                       |
| Create a VLAN                                              | SW1(config)#         | `vlan vlan-number`                                          |
| Configure allowed VLANs on a trunk port                    | SW1(config-if)#      | `switchport trunk allowed vlan allowed-vlans`              |
| Configure encapsulation type on a trunk port               | SW1(config-if)#      | `switchport trunk encapsulation encapsulation-type`        |
| Configure the interface as a trunk port                    | SW1(config-if)#      | `switchport mode trunk`                                     |
| Configure the native VLAN on a trunk port                  | SW1(config-if)#      | `switchport trunk native vlan vlan-number`                 |
| Configure the VLAN number on a router subinterface         | R1(config-subif)#    | `encapsulation dot1q vlan-number`                          |
| Display all trunk ports on the switch                      | SW1#                 | `show interfaces trunk`                                     |
| Configure a switch interface as a routed port              | SW1(config-if)#      | `no switchport`                                             |
| Configure the native VLAN on a router subinterface         | R1(config-subif)#    | `encapsulation dot1q vlan-id native`                       |
| Enable Layer 3 routing on a multilayer switch              | SW1(config)#         | `ip routing`                                                |
| Reset an interface to its default configuration            | R1(config)#          | `default interface interface`                               |
| Configure voice traffic and data traffic are separated but dont require unique voice VLAN | `switchport voice vlan 10 |
