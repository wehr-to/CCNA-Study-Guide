# Dynamic Routing Protocols & Route Selection

---

## Core Concepts

- **EGPs** are used to share routes between different autonomous systems (AS).
- **IGPs** are used to share routes within a single autonomous system (AS).
- **AD (Administrative Distance)** is used to compare routes learned via different routing protocols.
- **Metric** is used to compare routes learned via the same routing protocol.
- A route to a `/32` destination is known as a **host route**.
- A route to a network/subnet is known as a **network route**.
- Routers can use **Dynamic Routing Protocols** to advertise information about the routes they know to other routers.
- When using a **link-state** routing protocol, every router creates a **connectivity map** of the network.
- **Distance Vector** routing protocols send the following information to their connected neighbors:
  - Their known destination networks
  - Their metric to reach their known destination networks

---

## Protocol Classifications

### IGP Types
1. Distance Vector
2. Link State

### Distance Vector Routing Protocols
1. RIP  
2. EIGRP

### Link State Routing Protocols
1. OSPF  
2. IS-IS

### Path Vector Protocol
- BGP

---

## Route Selection Logic

- **Q:** Does a router prefer a lower or higher AD when selecting routes?  
  **A:** Lower

- **Q:** Does a router prefer a lower or higher metric when selecting routes?  
  **A:** Lower

- **Q:** If R1 learns multiple routes to the same destination from the same routing protocol, what is used to determine which route will be added to R1's routing table?  
  **A:** Metric

- **Q:** If R1 learns multiple routes to the same destination from two different routing protocols, what is used to determine which route will be added to R1's routing table?  
  **A:** AD (Administrative Distance)

- **Q:** R1 learns two routes to the same destination, via the same routing protocol, and both routes have the same metric. Which will be added to the routing table?  
  **A:** Both (traffic will be load-balanced)

---

## Route Example Breakdown

- **Q:** What is the AD value of this route?  
  `O 192.168.4.0/24 [110/3] via 10.0.12.2`  
  **A:** 110

- **Q:** What is the metric value of this route?  
  `O 192.168.4.0/24 [110/3] via 10.0.12.2`  
  **A:** 3

---

## Definitions & Acronyms

| Term | Definition |
|------|------------|
| EGP | Exterior Gateway Protocol |
| IGP | Interior Gateway Protocol |
| ECMP | Equal Cost Multi-Path |
| BGP | Border Gateway Protocol |
| RIP | Routing Information Protocol |
| OSPF | Open Shortest Path First |
| EIGRP | Enhanced Interior Gateway Routing Protocol |
| IS-IS | Intermediate System to Intermediate System |
| Floating Static Route | A static route with higher AD than a dynamic route |

---

## Protocol Behavior

- **Q:** What kind of dynamic routing protocol operates using 'routing by rumor'?  
  **A:** Distance Vector

- **Q:** What metric does RIP use?  
  **A:** Hop count

- **Q:** Which dynamic routing protocol uses a cost calculated based on interface bandwidth as its metric?  
  **A:** OSPF

- **Q:** Which kind of dynamic routing protocol tends to react faster to changes in the network, distance vector or link state?  
  **A:** Link State

- **Q:** Which kind of routing protocol uses more CPU resources on the router, distance vector or link state?  
  **A:** Link State

- **Q:** In which dynamic routing protocol do all links have a metric cost of 10 by default?  
  **A:** IS-IS

- **Q:** What dynamic routing protocol calculates metric using bandwidth and delay (and others, if configured)?  
  **A:** EIGRP

- **Q:** What is the single type of EGP?  
  **A:** Path Vector

---

## Quick Review

- **Host Route:** /32
- **Network Route:** Any subnet (e.g., /24, /30)
- **Metric:** Compared when same protocol
- **AD:** Compared when different protocols
- **EGP = BGP**
- **IGP = RIP, EIGRP, OSPF, IS-IS**

# Route Protocols and Administrative Distances

| Route Protocol / Type     | Administrative Distance (AD) |
|---------------------------|------------------------------|
| Directly Connected        | 0                            |
| Static                    | 1                            |
| eBGP                      | 20                           |
| EIGRP                     | 90                           |
| IGRP                      | 100                          |
| OSPF                      | 110                          |
| IS-IS                     | 115                          |
| RIP                       | 120                          |
| EIGRP (External)          | 170                          |
| iBGP                      | 200                          |
| Unusable Route            | 255                          |

