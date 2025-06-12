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







## Questions
- Q: To send a packet to a destination, does a router need a route to every network in the path to the destination?
No, (it only needs a route to the destination network)
- Q: If a packet's destination IP is matched by multiple routes, which route will the router select?
The most specific matching route
- Q: What does code C in the routing table mean?
Connected
- Q: What does code L in the routing table mean?
Local
- Q: What prefix length do connected routes use?
The prefix length configured on the interface.
- Q: What will a router do if none of its routes match a packet's destination IP address?
Drop the packet
- Q: Which two routes are automatically added to the routing table when you configure an IP address on an interface?
1) a connected route
2) a local route


