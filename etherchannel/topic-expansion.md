| Setup Type                   | Protocol | Command Example                   |
|-----------------------------|----------|-----------------------------------|
| Cisco-to-Cisco (legacy)     | PAgP     | mode desirable + mode auto        |
| Cisco-to-non-Cisco / modern | LACP     | mode active + mode passive        |
| Force without protocol      | None     | mode on (dangerous, no negotiation) |

- PAgP (Port Aggregation Protocol) is a Cisco proprietary protocol used to automatically bundle multiple physical links between switches into a single logical link, called an EtherChannel.
- “EtherChannel groups links together so STP sees them as one. PAgP is Cisco-only. Desirable + auto works, auto + auto doesn’t.

  | Configuration Pair         | Result                                 |
|---------------------------|----------------------------------------|
| Auto + Auto               | No EtherChannel (both wait)            |
| Auto + Desirable          | EtherChannel established               |
| Desirable + Desirable     | EtherChannel established               |
| On + anything else        | No EtherChannel unless both are "on"   |

| Feature       | PAgP              | LACP                  |
|---------------|-------------------|------------------------|
| Vendor        | Cisco Proprietary | IEEE Standard (802.3ad)|
| Modes         | Auto, Desirable   | Passive, Active        |
| Multivendor?  | Cisco only        | Yes                    |

You’d use mode desirable when:
- You’re in a Cisco-only environment.
- You want PAgP-based EtherChannel.
- You’re okay with Cisco proprietary protocols.

| Configuration            | Protocol | Outcome                               |
|--------------------------|----------|----------------------------------------|
| Desirable + Auto         | PAgP     | EtherChannel forms                     |
| Passive + Active         | LACP     | EtherChannel forms                     |
| On + On                  | None     | EtherChannel forms (no negotiation)    |
| Anything else            | Any      | Likely fails (no EtherChannel formed)  |
