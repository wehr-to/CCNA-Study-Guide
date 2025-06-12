## Local Route (L)
Default Behavior:
- Automatically added when an IP address is configured on an interface.
- Represents the specific IP address of the interface with a /32 mask.

## Real-World Insight:
- Used for control-plane traffic (e.g., if you ping the router interface itself).
- Important for management, SSH, SNMP, and troubleshooting.

## Command Output
R1# show ip route
...
L    192.168.1.1/32 is directly connected, GigabitEthernet0/0

## Scenario:
- You ping 192.168.1.1 (the interface IP), and it works.
- If the local route were missing or misconfigured, you'd see ping failures.

## Connected Route (C)
Default Behavior:
- Added when an interface is configured with an IP and brought up (no shutdown).
- Represents the entire subnet the router is directly connected to.

## Real-World Insight:
- Allows routing to all hosts within the subnet.
- Critical for establishing OSPF/EIGRP neighbor relationships.

## Command Output 
C    192.168.1.0/24 is directly connected, GigabitEthernet0/0

## Scenario:
- Your router interface has 192.168.1.1/24 → you now have reachability to 192.168.1.0 - 192.168.1.254.

## Static Route (S)
Default Behavior:
- Manually configured with ip route.
- Can specify next-hop IP, exit interface, or both.

Appears in the table with code S.

Real-World Insight:
- Used in smaller networks or stub networks.
- Also critical in production to override dynamic routes (with administrative distance control).

## Output 
ip route 10.1.1.0 255.255.255.0 192.168.1.2     ← next-hop
ip route 10.1.1.0 255.255.255.0 Gig0/0          ← exit-interface
ip route 10.1.1.0 255.255.255.0 Gig0/0 192.168.1.2  ← both

## Exam Trap:
- If you configure only exit-interface on a multi-access network, the router may ARP for every destination — inefficient and can cause traffic issues.

## Scenario:
- You're connecting a small branch office and don’t want to run a full dynamic protocol. Static routes get the job done.

## Dynamic Route
Default Behavior:
- Learned via a routing protocol (e.g., OSPF, EIGRP).
- The router exchanges routes with neighbors.
- Marked with protocol-specific codes (O, D, etc.).

## Real-World Insight:
- Automatically adapts to topology changes.
- Critical in large-scale environments or redundant designs.

## Command Output example: 
O    10.10.10.0/24 [110/2] via 192.168.1.2, 00:00:32, GigabitEthernet0/1

## Related:
- Routing Protocol Administrative Distance
- Routing Loop Prevention (split horizon, route poisoning)

## Scenario:
- You're configuring OSPF between three routers. Once neighbor relationships form, all subnets are shared automatically.

## Default Route (S*)
Default Behavior:
- The catch-all: 0.0.0.0/0 — matches anything not in the routing table.
- Marked with * in the routing table.

## Real-World Insight:
- Used to send unknown traffic to the Internet or upstream router.
- Often used at the edge of stub networks.

## Default Route (S*)
Default Behavior:
- The catch-all: 0.0.0.0/0 — matches anything not in the routing table.
- Marked with * in the routing table.

## Real-World Insight:
- Used to send unknown traffic to the Internet or upstream router.
- Often used at the edge of stub networks.

## Command Insight
ip route 0.0.0.0 0.0.0.0 192.168.1.254

## Scenario:
- Your branch office sends all traffic to the HQ router which has Internet access.

## Exam Trap:
- If Gateway of last resort is not set is shown, your default route isn’t working or not installed correctly.

## Questions
- Q: To send a packet to a destination, does a router need a route to every network in the path to the destination?
- A: No, (it only needs a route to the destination network)
- Q: If a packet's destination IP is matched by multiple routes, which route will the router select?
- A: The most specific matching route
- Q: What does code C in the routing table mean?
- A: Connected
- Q: What does code L in the routing table mean?
- A: Local
- Q: What prefix length do connected routes use?
- A: The prefix length configured on the interface.
- Q: What will a router do if none of its routes match a packet's destination IP address?
- A: Drop the packet
- Q: Which two routes are automatically added to the routing table when you configure an IP address on an interface?
- 1) a connected route
- 2) a local route
 
| Type            | Prefix Length             | Notes                                    |
| --------------- | ------------------------- | ---------------------------------------- |
| Local Route     | /32                       | Specific to router's IP                  |
| Connected Route | Based on interface config | Typically /24, /30, etc.                 |
| Default Route   | /0                        | Least specific — matches any destination |
| Static Routes   | Custom                    | Set by the admin                         |

| Code | Meaning                     |
| ---- | --------------------------- |
| L    | Local (interface IP /32)    |
| C    | Connected (direct subnet)   |
| S    | Static                      |
| S\*  | Static default (candidate)  |
| O    | OSPF                        |
| D    | EIGRP                       |
| R    | RIP                         |
| \*   | Candidate for default route |

| Term               | Meaning                                                         | Real-World Insight                                                                 |
|--------------------|------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| Local Route (L)    | Route to the exact IP address configured on a router’s interface | Used for checking if a packet is destined for the router itself (e.g., pings)      |
| Connected Route (C)| Route to the entire subnet that the interface is connected to    | Auto-added when an interface is assigned an IP and is brought up (`no shutdown`)   |
| Dynamic Route      | Learned via a routing protocol (e.g., OSPF, EIGRP, RIP)          | Routers communicate automatically to exchange routes                               |
| Static Route (S)   | Manually configured by a network admin                          | Predictable, simple — often used for stub networks or default routes               |

| Concept                      | Explanation                                                                 |
|------------------------------|------------------------------------------------------------------------------|
| Local Route Prefix Length    | Always /32 — because it targets a single host (the router’s own IP address) |
| Connected Route Prefix Length| Matches the subnet mask configured on the interface                         |
| Most Specific Match          | Router uses the route with the longest prefix match                         |
| Default Route                | 0.0.0.0/0 — matches everything but is the least specific                    |
| No Match in Routing Table    | The router drops the packet (unless a default route is set)                 |

| Router Behavior                  | Explanation                                              |
|----------------------------------|----------------------------------------------------------|
| Needs only a route to the destination subnet | Not to every hop in between                     |
| Uses most specific route         | Longest prefix match takes priority                      |
| Drops packets with no match      | Unless a default route is configured                     |
| Adds C and L routes automatically| When you assign an IP and use `no shutdown`              |

A connected route is a route to the network the interface is connected to.
A Dynamic route is added to the routing table by a protocol (ie. OSPF) that allows routers to communicate with each other and share routing information.
A Static route is manually configured by a network engineer/admin.

- Local routes use a prefix length of /32
- Most specific matching route = the matching route with the longest prefix length
- Routers store routes to all of their known destinations in the Routing Table
- The next router in the path to the destination is called the next hop 
- When routers receive packets, they look in the routing table to find the best route to forward that packet.
- A default route is often used to direct traffic to the Internet.
- A default route is a route to [network]/[netmask] = 0.0.0.0/0
- For an end host like a PC to send packets outside of its local network, it will send the packets to its default gateway
- In the routing table, the output "Gateway of last resort is not set" means a default has not been configured
- Static routes in which you specify only the exit-interface appear as directly-connected in the routing table.
- The default route is the least specific route possible.
- Code * in the routing table indicates a candidate default route.
- Code S in the routing table indicates a static route.

## Troubleshooting
Real-World Issues and Use Cases

## 1. Missing Routes
- Symptom: Router drops packets or returns "destination unreachable"
- Cause: No matching route in the table
- Fix: Add a static or dynamic route, or a default route

## 2. Incorrect Static Route
- Symptom: Traffic doesn't reach the destination
- Cause: Wrong exit interface or next-hop IP
- Fix: Verify topology and use show ip route + traceroute

## 3. Recursive Lookup Issues
- Symptom: Static route uses next-hop IP that itself is unreachable
- Fix: Ensure there's a connected route to reach the next-hop

## 4. Local Route Blocking Forwarding
- Symptom: Packet intended for remote host is interpreted as local
- Fix: Check for incorrect IP assignments on router interfaces


