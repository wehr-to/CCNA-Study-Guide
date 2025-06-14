# CDP & LLDP Commands Table

| Task | Mode | Command |
|------|------|---------|
| Configure CDP hold time | global config | `cdp holdtime <seconds>` |
| Configure CDP message timer | global config | `cdp timer <seconds>` |
| Configure LLDP hold time | global config | `lldp holdtime <seconds>` |
| Configure LLDP message timer | global config | `lldp timer <seconds>` |
| Configure LLDP reinitialization timer | global config | `lldp reinit <seconds>` |
| Enable CDP globally | global config | `cdp run` |
| Enable CDP on an interface | interface config | `cdp enable` |
| Enable CDPv2 | global config | `cdp advertise-v2` |
| Enable LLDP globally | global config | `lldp run` |
| Enable LLDP receive on interface | interface config | `lldp receive` |
| Enable LLDP transmit on interface | interface config | `lldp transmit` |

---

### CDP Show Commands

| Purpose | Exec Command |
|---------|---------------|
| Show detailed info for a specific CDP neighbor | `show cdp entry <host-name>` |
| Show detailed info for all CDP neighbors | `show cdp neighbors detail` |
| Show global CDP info | `show cdp` |
| Show CDP neighbor table | `show cdp neighbors` |
| Show interfaces CDP is enabled on | `show cdp interface` |
| Show CDP packets sent/received | `show cdp traffic` |

---

### LLDP Show Commands

| Purpose | Exec Command |
|---------|---------------|
| Show detailed info for a specific LLDP neighbor | `show lldp entry <host-name>` |
| Show detailed info for all LLDP neighbors | `show lldp neighbors detail` |
| Show global LLDP info | `show lldp` |
| Show LLDP neighbor table | `show lldp neighbors` |
| Show interfaces LLDP is enabled on | `show lldp interface` |
| Show LLDP packets sent/received | `show lldp traffic` |
