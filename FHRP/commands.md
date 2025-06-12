## HSRP Configuration Commands

| Description                                 | Command Format                                                 |
|---------------------------------------------|----------------------------------------------------------------|
| Configure HSRP version 2                    | `R1(config-if)# standby version 2`                             |
| Configure the HSRP priority                 | `R1(config-if)# standby <group-number> priority <priority>`   |
| Configure the HSRP virtual IP on interface  | `R1(config-if)# standby <group-number> ip <ip-address>`       |
| Enable HSRP preemption                      | `R1(config-if)# standby <group-number> preempt`               |
