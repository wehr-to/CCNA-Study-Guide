# OSPF

# 🧠 OSPF Key Concepts

## General Concepts
- An autonomous system boundary router (ASBR) is an OSPF router that connects the OSPF network to an external network.
- OSPF LSAs are organized in a structure called the LSDB.
- OSPF can divide networks into separate areas.
- OSPF LSAs have a default aging timer of 30 minutes.
- An area is a set of routers and links that share the same LSDB.
- An interarea route is a route to a destination in a different OSPF area.
- An intra-area route is a route to a destination inside the same OSPF area.
- It is recommended that you connect an ABR to a maximum of 2 areas.
- Routers connected to the backbone area (area 0) are called backbone routers.
- Routers with all interfaces in the same area are called internal routers.
- Routers with interfaces in multiple areas are called ABRs (Area Border Routers).
- The backbone area (area 0) is an area that all other areas must connect to.
- The Shortest Path First algorithm is also known as Dijkstra's algorithm.
- The default OSPF reference bandwidth is 100 Mbps.
- Formula to calculate cost: `reference bandwidth / interface bandwidth = cost`

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
- Hello messages are sent to `224.0.0.5`
- Messages to the DR/BDR are sent to `224.0.0.6`
- DROthers only form Full state with DR and BDR, not each other
- If a router receives a Hello packet without seeing its own Router ID in it → `Init`
- If no Hello messages have been received → `Down`
- When a router sees its own Router ID in a Hello packet → `2-Way`
- DR/BDR are elected in the `2-Way` state
- In `Exchange` → Routers exchange DBDs
- In `Loading` → Routers send LSRs for needed LSAs
- In `Full` → LSDBs are synchronized

## OSPF Router ID Selection Priority
1. Manually configured Router ID
2. Highest IP on a loopback interface
3. Highest IP on a physical interface

## OSPF Cost Examples (Default Reference BW = 100 Mbps)

| Interface Type     | Cost |
|--------------------|------|
| Ethernet (10 Mbps) | 10   |
| FastEthernet (100 Mbps) | 1 |
| Gigabit Ethernet   | 1    |
| 10 Gig Ethernet    | 1    |
| Loopback           | 1    |

## Special Notes
- OSPF cost is affected by the `bandwidth` command (for metric), but not interface speed — the `speed` command affects real interface performance.
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
