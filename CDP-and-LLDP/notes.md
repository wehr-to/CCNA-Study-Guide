# Default CDP and LLDP Timers

| Feature                     | Protocol | Default Value       |
|----------------------------|----------|---------------------|
| Holdtime                   | CDP      | 180 seconds         |
| Message Timer              | CDP      | 60 seconds          |
| Version                    | CDP      | Version 2           |
| Holdtime                   | LLDP     | 120 seconds         |
| Message Timer              | LLDP     | 30 seconds          |
| Reinitialization Timer     | LLDP     | 2 seconds           |

# LLDP Interface Commands

| Function  | Command         | Explanation                                      |
|-----------|-----------------|--------------------------------------------------|
| Transmit  | `lldp transmit` | Interface will send out LLDP advertisements      |
| Receive   | `lldp receive`  | Interface will accept LLDP advertisements from neighbors |

# LLDP vs CDP Notes

## Key Behaviors

- **LLDP is unidirectional per function**: devices independently send (`lldp transmit`) and receive (`lldp receive`) advertisements.
- **Transmit and receive are configured separately** per interface in LLDP.
- **A device can run both CDP and LLDP simultaneously.**

---

## Protocol Overview

| Feature                         | CDP                            | LLDP                                 |
|---------------------------------|--------------------------------|---------------------------------------|
| Full Name                       | Cisco Discovery Protocol       | Link Layer Discovery Protocol         |
| Vendor                          | Cisco proprietary              | Industry standard                     |
| Default State on Cisco Devices  | Enabled                        | Disabled                              |
| Supports VTP Info Sharing       | Yes                            | No                                    |
| Destination MAC Address         | `0100.0CCC.CCCC`               | `0180.C200.000E`                      |

---

## Quiz Q&A

**Q: What does CDP stand for?**  
A: Cisco Discovery Protocol

**Q: What does LLDP stand for?**  
A: Link Layer Discovery Protocol

**Q: Which Layer 2 discovery protocol is an industry standard?**  
A: LLDP

**Q: Which Layer 2 discovery protocol is Cisco proprietary?**  
A: CDP
