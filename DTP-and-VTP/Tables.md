## VTP - VLAN Trunking Protocol Overview
| Feature           | Description                                                                 | Purpose                                                                                 |
|-------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| VTP               | Cisco proprietary protocol for VLAN database synchronization                | Centralizes VLAN management across switches                                            |
| Default Mode      | All Cisco switches default to server mode                                   | Ready to manage VLANs unless changed                                                   |
| Versions          | v1, v2 (no extended VLANs); v3 (supports VLANs 1006–4094)                    | Only v3 supports extended VLANs and client-side storage                                |
| Revision Number   | Tracks changes to VLAN database                                              | Higher revision overrides lower; dangerous if misused                                  |
| Transport Method  | Sent via trunks as VTP advertisements                                       | Syncs VLAN changes automatically                                                       |
| Risk              | A switch with higher rev# but no VLANs can wipe the entire domain           | Always verify `show vtp status` before trunking new switches                           |

## VTP Modes Comparison 
| Mode        | Can Add/Modify VLANs? | Sync VLANs? | Saves to NVRAM?                     | Notes                                  |
|-------------|------------------------|-------------|-------------------------------------|----------------------------------------|
| Server      | Yes                    | Yes         | Yes                                 | Default mode, authoritative             |
| Client      | No                     | Yes         | No (v1/v2), Yes (v3)                | Follows server config                  |
| Transparent | Yes (local only)       | No          | Yes                                 | Does not sync with VTP, but retains locally |

## DTP - Dynamic Trunking Protocol
| Feature             | Description                                                              | Purpose                                                                      |
|---------------------|---------------------------------------------------------------------------|------------------------------------------------------------------------------|
| DTP                 | Cisco-only protocol for trunk negotiation                                | Automatically determines trunk or access mode                               |
| Enabled by Default  | Yes, on most switchports                                                  | Manual disabling recommended in secure environments                         |
| Cisco-Only          | DTP is not supported by Juniper, HP, etc.                                | Won’t work across multi-vendor links                                        |
| Negotiation Types   | dynamic auto, dynamic desirable, trunk, access, nonegotiate              | Used to auto-negotiate or force link types                                  |

## Default Behaviors
| Feature        | Default State                      |
|----------------|------------------------------------|
| VTP Mode       | Server                             |
| VTP Version    | Version 1                          |
| DTP            | Enabled                            |
| DTP (New Switches) | dynamic auto                   |
| DTP (Old Switches) | dynamic desirable              |

## VTP VLAN Wipe Disaster Scenario
| Situation                                 | Result                                                                   |
|-------------------------------------------|--------------------------------------------------------------------------|
| New switch with higher rev# and no VLANs  | All VLANs on the domain get deleted                                     |

| Mitigations                                                                 |
|------------------------------------------------------------------------------|
| Check `show vtp status` before trunking new devices                         |
| Change domain name or switch to transparent to reset revision number        |
| Use VTPv3 for extended VLAN support and improved control                    |

## Exam and Lab Traps
| Question                                               | Answer(s)                                 |
|--------------------------------------------------------|-------------------------------------------|
| How to reset VTP revision number?                      | Change VTP mode to transparent, change domain name |
| Which VTP mode doesn’t sync with others?               | Transparent                               |
| What happens with both ends as dynamic auto?           | Link becomes access, not trunk            |
| DTP prefers which encapsulation first?                 | ISL (deprecated), but 802.1Q is default today |

## VTP Mode Behavior Summary
| Mode        | Add/Edit VLANs | Sync VLANs | Saves to NVRAM       | Syncs From Other Servers |
|-------------|----------------|------------|-----------------------|---------------------------|
| Server      | Yes            | Yes        | Yes                   | Yes (if higher rev)       |
| Client      | No             | Yes        | No (v1/v2), Yes (v3)  | Yes (always)              |
| Transparent | Yes (local)    | No         | Yes                   | No                        |

## DTP Port Mode Outcomes
| Local Mode        | Remote Mode       | Resulting Port Mode |
|-------------------|-------------------|----------------------|
| dynamic auto      | dynamic auto      | Access               |
| dynamic auto      | trunk             | Trunk                |
| dynamic desirable | dynamic auto      | Trunk                |
| dynamic desirable | trunk             | Trunk                |
| trunk             | any               | Trunk                |
| access            | any               | Access               |

## DTP Mode Personalities
| Mode         | Personality    | Behavior Description                             |
|--------------|----------------|--------------------------------------------------|
| Auto         | Shy            | Waits for the other end to initiate              |
| Desirable    | Bold           | Actively initiates trunk negotiation             |
| Trunk        | Pre-decided    | Forces trunk mode, no negotiation                |
| Access       | Passive        | Forces access mode, no negotiation               |
| Nonegotiate  | Silent         | Disables DTP completely                          |

## Mnemonics and Logic Rules
| Mnemonic                                | Meaning                                                         |
|-----------------------------------------|------------------------------------------------------------------|
| Auto + Auto = No Go                     | Two dynamic auto ports won’t form a trunk                       |
| Transparent doesn’t care, but remembers | Transparent mode keeps local VLANs, ignores VTP sync            |
| VTP 3 is VIP                            | Only version supporting extended VLANs and client NVRAM storage |

## Related Technologies
| Feature         | Relationship                                              |
|------------------|-----------------------------------------------------------|
| ISL              | Cisco trunk encapsulation (deprecated)                    |
| 802.1Q           | Industry standard trunking protocol (default today)       |
| EtherChannel     | Must match trunk/access config; affected by negotiation   |
| VLAN database    | Stored in vlan.dat on flash (used by VTP server/transparent) |

## Troubleshooting VTP and DTP
| Issue                     | Symptom or Command Feedback                          |
|---------------------------|------------------------------------------------------|
| VLANs missing after trunk | show vlan brief → only default VLAN shows           |
| Trunks not forming        | show interfaces trunk → empty or no output           |
| VTP status unknown        | show vtp status → domain/mode mismatch               |
| High VTP rev mismatch     | show vtp status → revision number conflict           |


