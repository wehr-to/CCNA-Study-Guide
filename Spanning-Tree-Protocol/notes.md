## STP Root Port Selection

- Spanning Tree Protocol (STP) prevents Layer 2 loops by placing switch ports into forwarding or blocking states, ensuring there's only one active path between any two network devices.

1. Lowest root cost  
2. Lowest neighbor bridge ID  
3. Lowest neighbor port ID  

---

## Three Fields of the STP Bridge ID

- Bridge Priority (4 bits)  
- Extended System ID (VLAN ID) (12 bits)  
- MAC Address (48 bits)  

---

- The STP bridge priority can be changed in units of **4096**  
- 'Classic' Spanning Tree Protocol is **IEEE 802.1D**  
- Cisco switches use a version of STP called **PVST (Per-VLAN Spanning Tree)**, which runs a separate spanning tree instance in each VLAN  
- **STP Designated ports** are in a forwarding state  
- **STP Non-Designated ports** are in a blocking state  
- **STP Root ports** are in a forwarding state  
- STP: All ports on the root bridge are designated ports (forwarding state)  
- STP: The default bridge priority is **32768** (not including Extended System ID)  
- STP: The switch with the lowest Bridge ID becomes the root bridge  
- STP: There must be **one designated port per collision domain**  
- STP: When a switch is powered on, it assumes the role of root bridge  
- When a switch rapidly and continuously updates a MAC address in its MAC address table, alternating between different interfaces, this is known as **MAC Address Flapping**  
- **Portfast** allows an STP port to move immediately to the forwarding state  
- If an interface with **BPDU Guard** enabled receives a BPDU from another switch, the interface will be shut down  
- **PVST+ BPDUs** are sent to destination MAC address: `0100.0ccc.cccd`  
- `spanning-tree vlan vlan-id root secondary` sets the STP priority to **28672**  
- `spanning-tree vlan vlan-id root primary` sets the STP priority to **24576**, or 4096 less than the current root's priority  
- Standard STP (NOT PVST) BPDUs are sent to destination MAC address: `0180.c200.0000`  
- STP BPDUs are only forwarded on **designated ports**  
- STP: A **blocking interface** can’t move directly to a forwarding state  
- STP: A **forwarding interface** can move directly to a blocking state  
- STP: **Non-designated ports** are in a blocking state  
- The STP timers on the root bridge determine the timers used for all switches in the network  

---

## STP Default Timers

- **Forward delay**: 15 seconds  
- **Hello timer**: 2 seconds  
- **Max age**: 20 seconds (10 × hello timer)  

---

## Common Questions

- **Q: Do all switches run STP by default?**  
  Yes  
- **Q: How many root bridges are elected in STP?**  
  One  
- **Q: If looped Layer 2 broadcast messages accumulate and congest a network, this is called a [...].**  
  Broadcast storm  
- **Q: In an 802.1D STP network, which switch(es) send BPDUs?**  
  Root Bridge Only  
- **Q: The messages sent by STP switches are called:**  
  BPDUs (Bridge Protocol Data Units)  
- **Q: Which field in the STP BPDU is used to elect the root bridge?**  
  Bridge ID Field  

---

## Port Behavior by STP State

| STP State     | Learns MACs | Sends/Receives BPDUs | Forwards Traffic |
|---------------|-------------|-----------------------|------------------|
| Blocking      | No          | Receives Only         | No               |
| Listening     | No          | Yes                   | No               |
| Learning      | Yes         | Yes                   | No               |
| Forwarding    | Yes         | Yes                   | Yes              |

---

## Stable vs Transitional States

- **Stable States:**
  1. Blocking  
  2. Forwarding  

- **Transitional States:**
  1. Listening  
  2. Learning  

---

## STP Optional Features

- **Root Guard**: Prevents a newly connected switch from becoming the root bridge  
- **Loop Guard**: Shuts down an interface if it stops receiving BPDUs  
