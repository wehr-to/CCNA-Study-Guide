## Ethernet Standards and Cable Lengths
| Standard         | Cable Type      | Max Length       | IEEE Standard |
|------------------|------------------|------------------|----------------|
| 1000BASE-LX      | Multimode Fiber  | 550 meters       | 802.3z         |
| 1000BASE-LX      | Single-mode Fiber| 5 kilometers     | 802.3z         |
| 10GBASE-SR       | Multimode Fiber  | 400 meters       | 802.3ae        |
| 10GBASE-LR       | Single-mode Fiber| 10 kilometers    | 802.3ae        |
| 10GBASE-ER       | Single-mode Fiber| 30 kilometers    | 802.3ae        |

## IEEE Standards for Ethernet Speeds
| IEEE Standard | Speed       | Name            |
|----------------|-------------|------------------|
| 802.3i         | 10 Mbps     | 10BASE-T         |
| 802.3u         | 100 Mbps    | 100BASE-T        |
| 802.3ab        | 1 Gbps      | 1000BASE-T       |
| 802.3an        | 10 Gbps     | 10GBASE-T        |

## Wire Pair Usage by Ethernet Standard
| Ethernet Standard | Pin Pairs Used             | Total Wires |
|-------------------|----------------------------|-------------|
| 10BASE-T          | 1–2, 3–6                    | 2 pairs (4 wires) |
| 100BASE-T         | 1–2, 3–6                    | 2 pairs (4 wires) |
| 1000BASE-T        | 1–2, 3–6, 4–5, 7–8          | 4 pairs (8 wires) |
| 10GBASE-T         | 1–2, 3–6, 4–5, 7–8          | 4 pairs (8 wires) |

## Cable Types & Usage
| Cable Type         | Use Case                                  |
|--------------------|--------------------------------------------|
| Straight-through   | Different device types (PC ↔ switch)       |
| Crossover          | Same device types (router ↔ router)        |
| Rollover           | Console access (PC ↔ router/switch console)|

## RJ45 Connector and Auto MDI-X
| Feature                | Value/Description                        |
|------------------------|------------------------------------------|
| RJ45 Pin Count         | 8 pins                                   |
| Auto MDI-X             | Automatically switches transmit/receive pairs |
| Max UTP Cable Length   | 100 meters                               |
| UTP Security Risk      | Emits faint signal; susceptible to sniffing |

## Cable Theory
| Question                                              | Answer                  |
|--------------------------------------------------------|-------------------------|
| Why are UTP wires twisted?                             | To protect against EMI  |
| Which is cheaper: single-mode or multimode fiber?      | Multimode               |
| Which supports longer distances: single-mode or multimode? | Single-mode         |
| How does light travel in single-mode fiber?            | One straight path       |
| How does light travel in multimode fiber?              | Multiple angles (modes) |
| What kind of power do electronic devices use?          | DC                      |

## Auto MDI-X and Cable Type Rules
| Connection Type        | Cable Needed (if Auto MDI-X is disabled) |
|------------------------|-------------------------------------------|
| PC ↔ Switch            | Straight-through                         |
| Router ↔ Switch        | Straight-through                         |
| Router ↔ Router        | Crossover                                 |
| Switch ↔ Switch        | Crossover                                 |

## Bits and Bytes
| Unit         | Bits                 |
|--------------|----------------------|
| Byte         | 8                    |
| Kilobit      | 1,000                |
| Megabit      | 1,000,000            |
| Gigabit      | 1,000,000,000        |
| Terabit      | 1,000,000,000,000    |

## Ethernet Speeds
| Ethernet Type   | Speed     |
|------------------|-----------|
| Ethernet         | 10 Mbps   |
| Fast Ethernet    | 100 Mbps  |
| Gigabit Ethernet | 1 Gbps    |
| 10 Gig Ethernet  | 10 Gbps   |

## Common Console Ports on Cisco Devices
| Type | Connector |
|------|-----------|
| 1    | USB       |
| 2    | RJ45      |

## FastEthernet Tx/Rx Pins by Device
| Device     | Transmit Pins | Receive Pins |
|------------|----------------|----------------|
| PC         | 1–2            | 3–6            |
| Router     | 1–2            | 3–6            |
| Firewall   | 1–2            | 3–6            |
| Switch     | 3–6            | 1–2            |

## Fiber Cable Types
| Fiber Type     | Description                                           |
|----------------|-------------------------------------------------------|
| Single-mode    | Light travels straight through narrow core           |
| Multimode      | Light enters at multiple angles (wider core)         |









