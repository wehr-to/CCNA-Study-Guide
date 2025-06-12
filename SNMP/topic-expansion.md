## SNMP: Overview
- SNMP (Simple Network Management Protocol) is used by network devices to monitor, report, and manage other network devices through a centralized system.

| Role             | Function                                                                 |
| ---------------- | ------------------------------------------------------------------------ |
| **SNMP Agent**   | Software running on managed devices (switches, routers, firewalls, etc.) |
| **SNMP Manager** | Software running on the NMS (Network Management Station)                 |
| **MIB**          | A structured database of all manageable variables                        |
| **OID**          | A unique identifier (numbered path) for each variable in the MIB         |

## SNMP Communication and Port Usage
| Component                                 | Protocol | Port | Direction       |
| ----------------------------------------- | -------- | ---- | --------------- |
| **SNMP Agent** (receives queries)         | UDP      | 161  | Manager → Agent |
| **SNMP Manager** (receives traps/informs) | UDP      | 162  | Agent → Manager |

- Note: Both SNMPv1/v2c and SNMPv3 use these same ports, unless modified.

## SNMP Structure: MIB and OIDs
- MIB (Management Information Base):
- A collection of standardized variables managed by SNMP
- Hierarchical structure (tree-based)
- Includes data like interface status, CPU load, memory, etc.

- OID (Object Identifier):
- Numeric path to a variable in the MIB
- Example: 1.3.6.1.2.1.2.2.1.8 → interface operational status

## SNMP Versions
| Version | Key Features                                                  | Security                      |
| ------- | ------------------------------------------------------------- | ----------------------------- |
| **v1**  | Basic functionality, no encryption                            | Community strings (cleartext) |
| **v2c** | Improved performance (e.g., **GetBulk**), still no encryption | Community strings (cleartext) |
| **v3**  | Adds **encryption, authentication, user-based control**       | Most secure version           |

- Most common in legacy networks: SNMPv2c
- Best practice for modern networks: SNMPv3

## SNMP Message Types (Operations)
| Message      | Class        | Direction       | Purpose                                                      |
| ------------ | ------------ | --------------- | ------------------------------------------------------------ |
| **Get**      | Read         | Manager → Agent | Retrieve the value of a specific OID                         |
| **GetNext**  | Read         | Manager → Agent | Retrieve the next OID in the MIB (used for walking the tree) |
| **GetBulk**  | Read         | Manager → Agent | Efficiently retrieve blocks of data (v2c and v3 only)        |
| **Set**      | Write        | Manager → Agent | Change the value of an OID on a managed device               |
| **Response** | Response     | Agent → Manager | Sent in reply to Get, Set, GetNext, or GetBulk               |
| **Trap**     | Notification | Agent → Manager | Alert sent **without acknowledgment**                        |
| **Inform**   | Notification | Agent → Manager | Alert sent **with acknowledgment**                           |

## SNMP Message Classes Summary
| Message Class    | Messages Included     |
| ---------------- | --------------------- |
| **Read**         | Get, GetNext, GetBulk |
| **Write**        | Set                   |
| **Response**     | Response              |
| **Notification** | Trap, Inform          |

## SNMP Message Behavior: Direction and Confirmation
| Message  | Direction       | Confirmation | Notes                                     |
| -------- | --------------- | ------------ | ----------------------------------------- |
| Get      | Manager → Agent | Yes          | Request for OID value                     |
| GetNext  | Manager → Agent | Yes          | Auto-traverse MIB tree                    |
| GetBulk  | Manager → Agent | Yes          | Multiple OID values in one message (v2c+) |
| Set      | Manager → Agent | Yes          | Modify a variable                         |
| Trap     | Agent → Manager | No           | Unacknowledged alert                      |
| Inform   | Agent → Manager | Yes          | Acknowledged alert                        |
| Response | Agent → Manager | Yes          | Reply to Get/Set/Next/Bulk                |

## SNMP Key Q&A Review
| Question                                                 | Answer                             |
| -------------------------------------------------------- | ---------------------------------- |
| What does SNMP stand for?                                | Simple Network Management Protocol |
| What does MIB stand for?                                 | Management Information Base        |
| What does OID stand for?                                 | Object Identifier                  |
| What does NMS stand for?                                 | Network Management Station         |
| What are the two SNMP device roles?                      | Managed Devices, NMS               |
| Which version of SNMP is most secure?                    | SNMPv3                             |
| Which version of SNMP is most commonly used (legacy)?    | SNMPv2c                            |
| Which message retrieves a value from the MIB?            | Get                                |
| Which message requests the next variable in the MIB?     | GetNext                            |
| Which message efficiently requests many values (v2c/v3)? | GetBulk                            |
| Which message modifies an MIB value?                     | Set                                |
| Which message is a one-way alert from agent to manager?  | Trap                               |
| Which message is a two-way alert (acknowledged)?         | Inform                             |
| Which messages belong to the notification class?         | Trap, Inform                       |
| Which messages are in the read class?                    | Get, GetNext, GetBulk              |
| Which messages are in the response class?                | Response                           |
| Which message is in the write class?                     | Set                                |
| Which port does the SNMP Agent use?                      | UDP 161                            |
| Which port does the SNMP Manager use?                    | UDP 162                            |


