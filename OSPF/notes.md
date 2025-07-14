# OSPF

# OSPF Key Concepts

## General OSPF Concepts

| **Concept**                              | **Explanation**                                                        |
| ---------------------------------------- | ---------------------------------------------------------------------- |
| ASBR (Autonomous System Boundary Router) | An OSPF router that connects the OSPF domain to external networks      |
| LSDB (Link-State Database)               | Structure where OSPF LSAs are stored                                   |
| OSPF Areas                               | Used to divide OSPF networks into segments for scalability             |
| OSPF LSA Aging Timer                     | Default refresh interval is 30 minutes                                 |
| OSPF Area Definition                     | A group of routers and links sharing the same LSDB                     |
| Interarea Route                          | Route to a destination in a different OSPF area                        |
| Intra-area Route                         | Route to a destination within the same OSPF area                       |
| ABR (Area Border Router) Recommendation  | Recommended to connect an ABR to no more than 2 areas                  |
| Backbone Routers                         | Routers connected to area 0                                            |
| Internal Routers                         | Routers with all interfaces in the same area                           |
| ABRs                                     | Routers with interfaces in multiple areas                              |
| Backbone Area (Area 0)                   | Core OSPF area; all other areas must connect to it                     |
| SPF (Shortest Path First) Algorithm      | OSPF path calculation algorithm, also known as Dijkstra's algorithm    |
| Default OSPF Reference Bandwidth         | 100 Mbps                                                               |
| OSPF Cost Formula                        | Cost = reference bandwidth / interface bandwidth                       |
| Router ID Uniqueness                     | Router IDs **must** be unique (note: original statement was incorrect) |


## Network Types & Timers

| Network Type        | Hello Timer | Dead Timer | DR/BDR? | Neighbor Discovery |
|---------------------|-------------|------------|---------|---------------------|
| Broadcast           | 10 sec      | 40 sec     | Yes     | Yes                 |
| Non-Broadcast (NBMA)| 30 sec      | 120 sec    | Yes     | No (manual config)  |
| Point-to-Point      | 10 sec      | 40 sec     | No      | Yes                 |
| Point-to-Multipoint | 30 sec      | 120 sec    | No      | Yes                 |
| Loopback            | —           | —          | No      | No                  |

## OSPF Message Types

| Type | Name                    |
|------|-------------------------|
| 1    | Hello                   |
| 2    | Database Description (DBD) |
| 3    | Link-State Request (LSR) |
| 4    | Link-State Update (LSU)  |
| 5    | Link-State Acknowledgement (LSAck) |

## Neighbor States (in order)
1. Down  
2. Init  
3. 2-Way  
4. Exstart  
5. Exchange  
6. Loading  
7. Full  

## Neighbor and Adjacency Behavior

| **State / Message**      | **Description**                                                 |
| ------------------------ | --------------------------------------------------------------- |
| Hello Messages           | Sent to `224.0.0.5`                                             |
| DR/BDR Election Messages | Sent to `224.0.0.6`                                             |
| DROthers                 | Form Full state only with DR and BDR, not each other            |
| `Down` State             | No Hello messages received                                      |
| `Init` State             | Hello received without seeing own Router ID                     |
| `2-Way` State            | Hello received that includes own Router ID; DR/BDR elected here |
| `Exchange` State         | Routers exchange Database Description (DBD) packets             |
| `Loading` State          | Routers send Link State Requests (LSRs) for needed LSAs         |
| `Full` State             | LSDBs are fully synchronized between routers                    |


## OSPF Router ID Selection Priority
1. Manually configured Router ID
2. Highest IP on a loopback interface
3. Highest IP on a physical interface

| Step | Method                                                                                  | Notes                                                           |
| ---- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| 1    | Use the **highest IPv4 address on a loopback** interface                                | Loopbacks are preferred because they are logical and always up. |
| 2    | If no loopbacks exist, use the **highest IPv4 address on an active physical interface** | The interface must be **up/up** at the time the process starts. |

# Router ID (RID) Selection in Routing Protocols

## Overview

The **Router ID** is a 32-bit identifier used by routing protocols (e.g., OSPF, EIGRP, BGP) to uniquely identify a router within a routing domain.  
It looks like an IPv4 address but is **not required to be reachable**.

---

## Router ID Selection Order

### Case 1: Router ID is Configured Manually

| Step | Method                             | Notes |
|------|------------------------------------|-------|
| 1    | Use manually configured `router-id` | Highest priority. Overrides all other options. |

```bash
router ospf 1
 router-id 1.1.1.1
```

## OSPF Cost Examples (Default Reference BW = 100 Mbps)

| Interface Type     | Cost |
|--------------------|------|
| Ethernet (10 Mbps) | 10   |
| FastEthernet (100 Mbps) | 1 |
| Gigabit Ethernet   | 1    |
| 10 Gig Ethernet    | 1    |
| Loopback           | 1    |

## Special Notes
- OSPF cost is affected by the `bandwidth` command (for metric), but not interface speed, the `speed` command affects real interface performance.
- OSPF interface priority default = 1
- Serial links use HDLC by default
- DCE (Data Communications Equipment) must define clock rate on serial links
- MTU mismatch prevents Full state (routers may form neighbors but not adjacencies)
- Network type mismatches also prevent route exchange

## LSA Types
- Type 1 = Router LSA
- Type 2 = Network LSA
- Type 5 = AS-External LSA

## OSPF Versions
- OSPFv2 is used for IPv4
- OSPFv3 is used for IPv6

## DR/BDR Election Criteria
1. Highest OSPF Interface Priority
2. Highest Router ID

## Multicast Addresses
- All OSPF routers: `224.0.0.5`
- DR/BDR: `224.0.0.6`

## Key Questions

| Question                                                                 | Answer                                   |
|--------------------------------------------------------------------------|------------------------------------------|
| What is ABR?                                                             | Area Border Router                        |
| What is ASBR?                                                            | Autonomous System Boundary Router         |
| What does LSA stand for?                                                 | Link State Advertisement                  |
| What does LSDB stand for?                                                | Link State Database                       |
| Does single-area OSPF have to use area 0?                                | No                                        |
| Does OSPF process ID have to match to form neighbors?                    | No                                        |
| Do Hello and Dead timers have to match?                                  | Yes                                       |
| Can routers with same Router ID form neighbors?                          | No                                        |
| What is the default Hello timer (Ethernet)?                              | 10 sec                                    |
| What is the default Dead timer (Ethernet)?                               | 40 sec                                    |
| Who becomes Master in Exstart?                                           | Router with higher Router ID              |
| In which state is Master/Slave determined?                               | Exstart                                   |
| Which multicast address is used for all OSPF routers?                    | 224.0.0.5                                 |
| Does bandwidth command affect real speed?                                | No                                        |
| Does bandwidth command affect OSPF cost?                                 | Yes                                       |

| Question                                                  | Answer                                                                                         |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Why switch from OSPF to EIGRP for unequal-cost load balancing? | Because OSPF only uses equal-cost paths, while EIGRP supports unequal-cost load balancing via variance. |
