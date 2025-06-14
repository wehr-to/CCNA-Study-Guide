# EIGRP Terms

| Term                  | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| Feasible Successor    | An alternate route to the destination which meets the feasibility condition |
| Reported Distance     | The neighbor's metric value to the route's destination                      |
| Successor             | The route with the lowest metric to the destination (the best route)        |
| Feasible Distance     | This router's metric value to the route's destination                       |

# EIGRP Default K-values

| K-value | Default |
|---------|---------|
| K1      | 1       |
| K2      | 0       |
| K3      | 1       |
| K4      | 0       |
| K5      | 0       |

# Cisco Administrative Distances (AD)

| Route Source              | AD Value | Notes                                                    |
|---------------------------|----------|----------------------------------------------------------|
| Directly Connected        | 0        | Most trusted; interface must be up and assigned an IP    |
| Static Route              | 1        | Manually configured next hop or exit interface           |
| EIGRP Summary Route       | 5        | Locally originated summary route                         |
| External BGP (eBGP)       | 20       | Routes received from an external BGP peer                |
| Internal EIGRP            | 90       | Routes learned within the same EIGRP AS                  |
| IGRP                     | 100      | Obsolete; Interior Gateway Routing Protocol (Cisco-only) |
| OSPF                     | 110      | Includes OSPFv2 and OSPFv3                               |
| IS-IS                    | 115      | Intermediate System to Intermediate System               |
| RIP                      | 120      | Includes RIPv1 and RIPv2                                 |
| External EIGRP           | 170      | Routes redistributed into EIGRP                          |
| Internal BGP (iBGP)      | 200      | Routes exchanged between routers in the same AS          |
| Unknown / Untrusted      | 255      | Route will never be used                                 |

# RIP and EIGRP Summary Notes

## RIP

- **RIP uses two message types:**
  - Request
  - Response

- **RIP Versions:**
  - **RIPv1:** Uses broadcast; only advertises classful addresses; does **not** support VLSM or CIDR.
  - **RIPv2:** Uses multicast to `224.0.0.9`; supports **VLSM** and **CIDR**.

- **RIP Limitations:**
  - Maximum hop count: **15**
  - **Does not** support unequal-cost load balancing

## EIGRP

- **Router ID Selection Priority:**
  1. Manually configured Router ID
  2. Highest IP address on a **loopback** interface
  3. Highest IP address on a **physical** interface

- **EIGRP Features:**
  - Supports **unequal-cost load balancing** using the `variance` command
  - Multicasts to `224.0.0.10`
  - Metric is calculated using:
    - **Bandwidth of the slowest link**
    - **Sum of the delays on all links**

- **Feasibility Condition:**
  - A route is considered a **feasible successor** if its **reported distance** is **less than** the **feasible distance** of the current successor route.
  - Only **feasible successor** routes can be used for **unequal-cost load balancing**.

## Questions and Answers

- **Q:** Does the EIGRP AS number have to match between neighbors?  
  **A:** Yes

- **Q:** Which versions of RIP are used for IPv4?  
  **A:** RIPv1 and RIPv2

- **Q:** Which version of RIP is used for IPv6?  
  **A:** RIPng (RIP Next Generation)

- **Q:** If an EIGRP route doesn't meet the feasibility condition, can it be used for unequal-cost load balancing?  
  **A:** No

- **Q:** Can OSPF perform unequal-cost load balancing?  
  **A:** No
