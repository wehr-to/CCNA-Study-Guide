# Campus LAN & Network Architecture Notes

---

## Campus LAN Architecture

- A 2-tier campus LAN architecture is also known as a collapsed core architecture.  
- End hosts connect to the access layer of a campus LAN.  
- In a campus LAN, the distribution layer aggregates connections from access layer switches.  
- In a campus LAN, the distribution layer is typically the border between Layer 2 and Layer 3.  
- In a large campus LAN, the core layer connects distribution layers together.  
- The distribution layer of a campus LAN is also known as the aggregation layer.  
- PoE is often used at the access layer of a campus LAN.  
- QoS marking is typically done at the access layer of a campus LAN.  

---

## SOHO Networks

- In SOHO networks, all networking functions are typically provided by a multipurpose network device called a home router / wireless router.  
- Q: What does SOHO stand for?  
  A: Small Office/Home Office  

---

## Spine-Leaf Architecture

- Spine-Leaf architecture is efficient in data centers with lots of east-west traffic.  
- A leaf switch must not connect to a leaf switch  
- A spine switch must not connect to a spine switch  
- End hosts connect to leaf switches  
- Every leaf switch is connected to every spine switch  
- Every spine switch is connected to every leaf switch  

---

## Network Topologies

- When each device connects to all other devices, it is called a full mesh topology.  
- When several devices all connect to one central device, it is called a star topology.  
- When some devices are connected to each other, but not all, it is called a partial mesh topology.  

---

## LAN Layer Summary

### Which three layers are found in a traditional 3-tier campus LAN?
1: Access  
2: Distribution  
3: Core  

### Which two layers are found in a traditional 2-tier campus LAN?
1: Access  
2: Distribution  
