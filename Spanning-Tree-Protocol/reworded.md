# Spanning Tree Protocol (STP) 

## 1. Purpose of STP
- Prevents Layer 2 loops in a switched network.
- Loops can cause:
  - Broadcast storms
  - MAC table instability
  - Duplicate frames
- STP creates a loop-free logical topology by blocking redundant links.

## 2. How STP Works

### Step 1: Root Bridge Election
- The Root Bridge is the reference point for all path calculations.
- Election criteria:
  1. Lowest Bridge ID (BID) wins.
     - BID = Bridge Priority (default 32768, in multiples of 4096) + MAC address
  2. If priorities tie, lowest MAC wins.
- Force a switch to be Root by lowering its priority: spanning-tree vlan 1 priority 4096

### Step 2: Determine Root Ports (RP)
- On non-root switches, the Root Port is the port with the lowest total path cost to reach the Root Bridge.
- Cost is based on link speed:
- 10 Mbps = 100
- 100 Mbps = 19
- 1 Gbps = 4
- 10 Gbps = 2

### Step 3: Determine Designated Ports (DP)
- For each network segment, the Designated Port is the one with the lowest path cost to the Root Bridge.
- The other port on that segment becomes a Non-Designated Port (blocking state).

### Step 4: Assign Port States
- Root Port (RP) → Forwarding
- Designated Port (DP) → Forwarding
- Non-Designated Port (NDP) → Blocking

## 3. STP Port States (802.1D)
1. Blocking – Listens for BPDUs, no data forwarding.
2. Listening – Preparing to forward, no MAC learning.
3. Learning – Learns MACs but no data forwarding.
4. Forwarding – Sends and receives data.
5. Disabled – Administratively down.

## 4. Key STP Timers
- Hello Time: 2s (BPDU interval from Root Bridge)
- Forward Delay: 15s per Listening/Learning stage
- Max Age: 20s (before BPDU info expires)

## 5. BPDU Basics
- Bridge Protocol Data Units are the STP control messages.
- Types:
- Configuration BPDUs – Sent by Root to maintain topology.
- TCN BPDUs (Topology Change Notification) – Sent when topology changes.
- By default, only the Root Bridge generates Configuration BPDUs.

## 6. STP Variants
- PVST+ (Per-VLAN STP) – Cisco default, runs STP per VLAN.
- RSTP (802.1w) – Rapid STP, faster convergence (~6s).
- MSTP (802.1s) – Multiple Spanning Tree, groups VLANs into instances.
- Rapid PVST+ – Cisco’s RSTP version per VLAN.
  
## 7. STP Convergence Times
- Classic STP: ~30–50 seconds
- Rapid STP: ~6 seconds

## 8. PortFast Best Practices
- PortFast should only be enabled on access ports connected to end hosts (PCs, printers, servers).
- Never enable PortFast on ports connected to other switches, routers, or hubs.
- Reason: PortFast skips Listening and Learning states, immediately placing the port into Forwarding, which can cause loops if connected to another switch.

### Recommended Configuration with BPDU Guard
~~~
interface FastEthernet0/1
switchport mode access
spanning-tree portfast
spanning-tree bpduguard enable
~~~

- BPDU Guard shuts down the port if a BPDU is received, protecting against accidental loops.

### 9. Common Exam Traps
- A new switch with a lower BID can take over as Root Bridge.
- PortFast without BPDU Guard on a trunk or uplink can cause loops.
= Always manually set your Root Bridge priority for stability.

### 10. Memory Aids
- Root > Root Port > Designated Port > Block others
- Lowest wins > Lowest priority, lowest cost, lowest MAC

