## RFC 4594 Recommended DSCP Markings
| Traffic Type         | Recommended Marking            | DSCP Value(s)      |
|----------------------|---------------------------------|--------------------|
| Best Effort          | DF                              | DSCP 0             |
| High Priority Data   | AF2x (AF21, AF22, AF23)         | DSCP 18, 20, 22    |
| Streaming Video      | AF3x (AF31, AF32, AF33)         | DSCP 26, 28, 30    |
| Interactive Video    | AF4x (AF41, AF42, AF43)         | DSCP 34, 36, 38    |
| Voice                | EF                              | DSCP 46            |

## DSCP / IPP / CoS Mappings
| Marking  | DSCP Value |
|----------|-------------|
| DF       | DSCP 0      |
| EF       | DSCP 46     |
| AF11     | DSCP 10     |
| AF12     | DSCP 12     |
| AF13     | DSCP 14     |
| AF21     | DSCP 18     |
| AF22     | DSCP 20     |
| AF23     | DSCP 22     |
| AF31     | DSCP 26     |
| AF32     | DSCP 28     |
| AF33     | DSCP 30     |
| AF41     | DSCP 34     |
| AF42     | DSCP 36     |
| AF43     | DSCP 38     |
| CS0      | DSCP 0      |
| CS1      | DSCP 8      |
| CS2      | DSCP 16     |
| CS3      | DSCP 24     |
| CS4      | DSCP 32     |
| CS5      | DSCP 40     |
| CS6      | DSCP 48     |
| CS7      | DSCP 56     |

## CoS / PCP Values and Usage
| CoS/PCP Value | Usage                 |
|---------------|------------------------|
| 0             | Best Effort            |
| 3             | Critical Applications  |
| 4             | Video Traffic          |
| 5             | Voice Traffic          |

## Power over Ethernet Standards
| Type             | Power Output | Powered Pairs | Standard           |
|------------------|--------------|----------------|---------------------|
| Cisco ILP        | 7W           | 2 pairs        | Cisco Proprietary   |
| PoE (Type 1)     | 15W          | 2 pairs        | IEEE 802.3af        |
| PoE+ (Type 2)    | 30W          | 2 pairs        | IEEE 802.3at        |
| UPoE (Type 3)    | 60W          | 4 pairs        | IEEE 802.3bt        |
| UPoE+ (Type 4)   | 100W         | 4 pairs        | IEEE 802.3bt        |





