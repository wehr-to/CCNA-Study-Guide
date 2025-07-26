# RFC 4594 QoS Marking Recommendations

| Traffic Type             | Recommended DSCP Marking |
|--------------------------|--------------------------|
| Best Effort              | DF                       |
| High Priority Data       | AF2x (AF21, AF22, AF23)  |
| Interactive Video        | AF4x (AF41, AF42, AF43)  |
| Streaming Video          | AF3x (AF31, AF32, AF33)  |
| Voice Traffic            | EF                       |

# DSCP, IPP, CoS, and CS Mappings

## DSCP Values

| Name   | DSCP Value |
|--------|------------|
| DF     | 0          |
| EF     | 46         |
| AF11   | 10         |
| AF12   | 12         |
| AF13   | 14         |
| AF21   | 18         |
| AF22   | 20         |
| AF23   | 22         |
| AF31   | 26         |
| AF32   | 28         |
| AF33   | 30         |
| AF41   | 34         |
| AF42   | 36         |
| AF43   | 38         |

## CoS / PCP Values

| PCP / CoS | Traffic Type         |
|-----------|----------------------|
| 0         | Best Effort          |
| 3         | Critical Applications|
| 4         | Video Traffic        |
| 5         | Voice Traffic        |

## Class Selector to DSCP

| CS Name | DSCP Value |
|---------|------------|
| CS0     | 0          |
| CS1     | 8          |
| CS2     | 16         |
| CS3     | 24         |
| CS4     | 32         |
| CS5     | 40         |
| CS6     | 48         |
| CS7     | 56         |

# QoS Concepts and Behavior

- **Shaping**: Buffers traffic in a queue if the traffic rate exceeds the configured rate.
- **Policing**: Drops traffic if the traffic rate exceeds the configured rate.
- **Best Effort**: No guarantee that data will be delivered or meet QoS standards.
- **Tail Drop**: Occurs when a queue is full; leads to TCP global synchronization.
- **LLQ (Low Latency Queuing)**: Designates one or more queues as strict priority queues.
- **FIFO**: Default queue behavior; packets are forwarded First In First Out.
- **Trust Boundary**: If an IP phone is connected, the QoS trust boundary should be at the IP phone.
- **IP Phone Call Signaling**: Marked as PCP/CoS 3.

# PoE and Power Levels

## PoE Standards

| Type     | IEEE Standard | Power (Watts) | Powered Pairs |
|----------|----------------|----------------|----------------|
| PoE      | 802.3af        | 15             | 2              |
| PoE+     | 802.3at        | 30             | 2              |
| UPoE     | 802.3bt (Type 3)| 60            | 4              |
| UPoE+    | 802.3bt (Type 4)| 100           | 4              |

- Cisco ILP offers 7 watts of power.
- Cisco ILP uses 2 powered wire pairs.
- Electronic devices use DC power.
- **PoE Power Policing**: Can be configured to prevent a PD from drawing too much power.

# QoS Definitions

- **Delay**: One-way time from source to destination.
- **Loss**: Percentage of packets that fail to reach the destination.
- **Jitter**: Variation in one-way delay between packets from the same application.
- **Bandwidth**: Overall capacity of a link.

# Acceptable VoIP Performance Metrics

| Metric       | Acceptable Value      |
|--------------|------------------------|
| Jitter       | ≤ 30 ms               |
| Packet Loss  | ≤ 1%                  |
| One-Way Delay| ≤ 150 ms              |

# Voice VLAN Behavior

- `switchport voice vlan` tags **IP phone** traffic.
- **PC traffic** remains untagged as usual for an access port.

# Acronyms and Definitions

| Term   | Definition                            |
|--------|----------------------------------------|
| PD     | Powered Device                        |
| PSE    | Power Sourcing Equipment              |
| ILP    | Cisco Inline Power                    |
| FIFO   | First In First Out                    |
| PoE    | Power over Ethernet                   |
| POTS   | Plain Old Telephone Service           |
| PSTN   | Public Switched Telephone Network     |
| VoIP   | Voice over IP                         |
| RED    | Random Early Detection                |
| WRED   | Weighted Random Early Detection       |
| AF     | Assured Forwarding                    |
| CS     | Class Selector                        |
| DF     | Default Forwarding                    |
| EF     | Expedited Forwarding                  |
| CBWFQ  | Class-Based Weighted Fair Queuing     |
| IPP    | IP Precedence                         |
| LLQ    | Low Latency Queuing                   |
| NBAR   | Network Based Application Recognition |

# QoS Marking Fields

- **Layer 2**: PCP / CoS
- **Layer 3**: DSCP (formerly IPP)

# QoS Algorithms and Scheduling

- **RED / WRED**: Drop random packets as queues reach threshold.
- **CBWFQ**: Uses a weighted round-robin scheduler while guaranteeing minimum bandwidth to each queue.

