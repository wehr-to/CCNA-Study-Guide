## RSTP (Rapid Spanning Tree Protocol) Key Concepts

- In RSTP, a switch considers a neighbor lost if it misses **3 BPDUs**.
- **Rapid STP** is defined in **IEEE 802.1w**.
- **Multiple STP (MSTP)** is defined in **IEEE 802.1s**.
- **RSTP Point-to-Point** link type is used for **full-duplex** connections.
- **RSTP Shared** link type is used for **half-duplex** connections.
- The **RSTP Alternate Port** role functions as a backup to the **Root Port**.
  - Discarding state; receives a **superior BPDU from another switch**.
- The **RSTP Backup Port** role functions as a backup to the **Designated Port**.
  - Discarding state; receives a **superior BPDU from the same switch**.

# RSTP Port Roles – Reference Table

| Port Role     | Description |
|---------------|-------------|
| **Root Port (RP)** | The single port on a switch that has the **best path to the root bridge**. Only one root port is allowed per switch (except the root bridge, which has none). |
| **Designated Port (DP)** | A port on a segment that is **responsible for forwarding frames toward the segment**. There is one designated port per collision domain (segment). |
| **Alternate Port** | A port that provides an **alternate path to the root bridge** if the root port fails. It is in a **discarding state** until needed. |
| **Backup Port** | A redundant port that exists **on the same switch and segment** as a designated port. It acts as a backup if the designated port fails. Also remains in the **discarding state**. |
| **Disabled Port** | A port that is administratively shut down or not participating in STP. It does not forward or receive BPDUs. |

## RSTP Q&A

**Q:** In RSTP, which switch(es) originate BPDUs?  
**A:** All switches

**Q:** Is RSTP compatible with classic STP?  
**A:** Yes (the interface connected to a switch running classic STP will operate in classic STP mode)

**Q:** What are the four RSTP port roles?  
1. Root  
2. Designated  
3. Alternate  
4. Backup

**Q:** What are the three RSTP link types?  
1. Edge  
2. Point-to-Point  
3. Shared

**Q:** What are the three RSTP port states?  
1. Discarding  
2. Learning  
3. Forwarding

**Q:** What is Cisco's upgrade to 802.1D?  
**A:** PVST+

**Q:** What is Cisco's upgrade to 802.1w?  
**A:** Rapid PVST+

**Q:** What is the protocol version identifier in a classic STP BPDU?  
**A:** 0

**Q:** What is the protocol version identifier in a rapid STP BPDU?  
**A:** 2

**Q:** Which STP optional features were built in to RSTP to allow ports to move directly to a forwarding state (in certain circumstances)?  
- UplinkFast  
- BackboneFast  
- PortFast
