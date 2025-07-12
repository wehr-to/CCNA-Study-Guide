# Network Media and Cabling Notes (CCNA)

## Fiber Ethernet Standards and Maximum Cable Lengths

### 1000BASE-LX (IEEE 802.3z)

* **Multimode:** 550 meters
* **Single-mode:** 5 kilometers

### 10GBASE-ER (IEEE 802.3ae)

* **Single-mode:** 30 kilometers

### 10GBASE-LR (IEEE 802.3ae)

* **Single-mode:** 10 kilometers

### 10GBASE-SR (IEEE 802.3ae)

* **Multimode:** 400 meters

### Recap:

* `1000BASE-LX` → IEEE 802.3z
* `10GBASE-SR`, `10GBASE-LR`, `10GBASE-ER` → IEEE 802.3ae

## Cable Types

### UTP (Unshielded Twisted Pair)

* Vulnerable to electromagnetic interference (EMI)
* Emits faint signals that can be intercepted (security risk)

### Multimode Fiber

* Allows multiple angles (modes) of light to enter the fiber core
* Wider core than single-mode

### Single-mode Fiber

* Light travels straight through at a single angle
* Supports longer distances than multimode

### Fiber-Optic

* Fiber cables are connected to SFP transceivers in routers/switches

### Ethernet Definition

* Defined in IEEE 802.3 (1983)

### Full-Duplex

* Allows simultaneous send and receive on both devices

## Bits & Bytes

| Question                     | Answer            |
| ---------------------------- | ----------------- |
| How many bits are in 1 byte? | 8                 |
| How many bits in 1 kilobit?  | 1,000             |
| How many bits in 1 megabit?  | 1,000,000         |
| How many bits in 1 gigabit?  | 1,000,000,000     |
| How many bits in 1 terabit?  | 1,000,000,000,000 |

## Cables and Wires

| Question                                      | Answer                   |
| --------------------------------------------- | ------------------------ |
| How many pairs in 1000BASE-T?                 | 4 pairs (8 wires)        |
| How many pairs in 100BASE-T?                  | 2 pairs (4 wires)        |
| How many pairs in 10BASE-T?                   | 2 pairs (4 wires)        |
| How many pairs in 10GBASE-T?                  | 4 pairs (8 wires)        |
| How many pins in RJ45 connector?              | 8                        |
| Maximum Ethernet UTP cable length?            | 100 meters               |
| Ethernet UTP connector type?                  | RJ45                     |
| Feature for automatic pin adjustment?         | Auto MDI-X               |
| Speed of 10G Ethernet?                        | 10 Gbps                  |
| Speed of Fast Ethernet?                       | 100 Mbps                 |
| Speed of Gigabit Ethernet?                    | 1 Gbps                   |
| Speed of standard Ethernet?                   | 10 Mbps                  |
| Cable for opposite pin pairs?                 | Crossover cable          |
| Cable for same pin pairs?                     | Straight-through cable   |
| Longer fiber cable: single-mode or multimode? | Single-mode              |
| Pin pairs in 1000BASE-T / 10GBASE-T?          | Pairs 1-2, 3-6, 4-5, 7-8 |
| Pin pairs in 10BASE-T / 100BASE-T?            | Pairs 1-2, 3-6           |
| Cheaper fiber type?                           | Multimode                |
| Why are UTP pairs twisted?                    | To reduce EMI            |
| Cable used for console (RJ45) port?           | Rollover cable           |
| Two types of console ports on Cisco devices?  | USB and RJ45             |

## IEEE Ethernet Standards

| Standard | Speed / Type         |
| -------- | -------------------- |
| 802.3i   | 10 Mbps (10BASE-T)   |
| 802.3u   | 100 Mbps (100BASE-T) |
| 802.3ab  | 1 Gbps (1000BASE-T)  |
| 802.3an  | 10 Gbps (10GBASE-T)  |

## Cabling Q\&A (Auto MDI-X Disabled)

| Scenario        | Cable Type       |
| --------------- | ---------------- |
| PC ↔ Switch     | Straight-through |
| Router ↔ Switch | Straight-through |
| Router ↔ Router | Crossover        |
| Switch ↔ Switch | Crossover        |

## Fiber Types Summary

* **Single-mode:** Light travels straight through, supports longer distance
* **Multimode:** Wider core, light enters at multiple angles, cheaper
* **Speeds measured in bits per second (bps)**

**Q: What are the two main kinds of fiber-optic cable?**
A: Single-mode and Multimode

## Fast Ethernet Pin Usage by Device

### PC

* Receives: Pins 3, 6
* Transmits: Pins 1, 2

### Router

* Receives: Pins 3, 6
* Transmits: Pins 1, 2

### Firewall

* Receives: Pins 3, 6
* Transmits: Pins 1, 2

### Switch

* Receives: Pins 1, 2
* Transmits: Pins 3, 6

