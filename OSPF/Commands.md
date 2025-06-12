## OSPF Configuration Commands

| Purpose                                                                 | Mode                | Command Syntax                                                  |
|-------------------------------------------------------------------------|---------------------|------------------------------------------------------------------|
| Enter OSPF configuration mode                                           | Global Config       | `router ospf <process-id>`                                       |
| Enable OSPF on interfaces in the specified range                        | OSPF Config         | `network <ip-address> <wildcard-mask> area <area>`              |
| Advertise default route into OSPF domain                                | OSPF Config         | `default-information originate`                                 |
| Configure OSPF router ID manually                                       | OSPF Config         | `router-id <a.b.c.d>`                                           |
| Modify the OSPF administrative distance                                 | OSPF Config         | `distance <value>`                                              |
| Prevent OSPF messages on a specific interface                           | OSPF Config         | `passive-interface <interface-id>`                              |
| Make all interfaces passive by default                                  | OSPF Config         | `passive-interface default`                                     |
| Reset the OSPF process                                                  | Privileged Exec     | `clear ip ospf process`                                         |
| Disable the OSPF process                                                | OSPF Config         | `shutdown`                                                      |
| Configure max ECMP paths                                                | OSPF Config         | `maximum-paths <number>`                                        |
| Configure OSPF reference bandwidth                                      | OSPF Config         | `auto-cost reference-bandwidth <megabits-per-second>`           |

---

## Interface-Level OSPF Commands

| Purpose                                                                 | Mode                | Command Syntax                                                  |
|-------------------------------------------------------------------------|---------------------|------------------------------------------------------------------|
| Enable OSPF directly on interface                                       | Interface Config    | `ip ospf <process-id> area <area-id>`                          |
| Configure OSPF cost                                                     | Interface Config    | `ip ospf cost <cost>`                                          |
| Set OSPF authentication password                                        | Interface Config    | `ip ospf authentication-key <password>`                        |
| Enable OSPF authentication                                              | Interface Config    | `ip ospf authentication`                                       |
| Set interface bandwidth (used in cost calc)                             | Interface Config    | `bandwidth <kilobits-per-second>`                              |
| Set OSPF network type                                                   | Interface Config    | `ip ospf network <type>`                                       |

---

## Other Interface Commands

| Purpose                                                                 | Mode                | Command Syntax                                                  |
|-------------------------------------------------------------------------|---------------------|------------------------------------------------------------------|
| Set clock rate on serial interface (DCE only)                           | Interface Config    | `clock rate <bits-per-second>`                                 |
| Enable PPP encapsulation on serial interface                            | Interface Config    | `encapsulation ppp`                                            |
| Check if serial interface is DCE or DTE                                 | Exec                | `show controllers <interface-id>`                              |
