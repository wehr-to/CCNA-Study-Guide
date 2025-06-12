## Load Balancing Support by Routing Protocol

| Protocol | Equal-Cost Load Balancing | Unequal-Cost Load Balancing             |
|----------|----------------------------|------------------------------------------|
| OSPF     | Yes                        | No                                       |
| EIGRP    | Yes                        | Yes (using variance)                     |
| RIP      | Yes                        | No                                       |
| BGP      | Technically                | Yes (but complex and policy-based)       |

## OSPF Network Types and Timers

| OSPF Network Type     | Hello Timer | Dead Timer | Description                                                        |
|-----------------------|-------------|------------|--------------------------------------------------------------------|
| Broadcast             | 10 sec      | 40 sec     | Default on Ethernet; uses DR/BDR                                   |
| Non-Broadcast (NBMA)  | 30 sec      | 120 sec    | Frame Relay, ATM; uses DR/BDR; manual neighbor config              |
| Point-to-Point        | 10 sec      | 40 sec     | Links between two routers (serial, etc); no DR/BDR                 |
| Point-to-Multipoint   | 30 sec      | 120 sec    | One-to-many setup; no DR/BDR                                       |
| Loopback              | —           | —          | Treated as stub with /32; no hello/dead timers used                |
