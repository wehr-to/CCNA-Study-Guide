## VTP (VLAN Trunking Protocol)

- VTP (VLAN Trunk Protocol) allows you to configure VLANs on a central server switch, and other switches (clients) will synchronize their VLAN database to the server.
- Cisco switches operate in VTP server mode by default.
- Cisco switches operate in VTP version 1 by default.
- VTP clients cannot add/modify/delete VLANs.
- VTP clients will synchronize their VLAN database with a VTP server with a higher revision number.
- VTP servers can add/modify/delete VLANs.
- VTP servers will synchronize their VLAN database with a VTP server with a higher revision number.
- VTP servers will increase the revision number every time a VLAN is added/modified/deleted.
- VTP transparents can add/modify/delete VLANs.
- VTP transparents won’t synchronize their VLAN database with a VTP server with a higher revision number.

## DTP (Dynamic Trunking Protocol)

- DTP (Dynamic Trunking Protocol) is a Cisco proprietary protocol that allows Cisco switches to dynamically determine their interface status (access or trunk) without manual configuration.
- DTP is enabled by default on all Cisco switch interfaces.
- A switchport in dynamic desirable mode will actively try to form a trunk with other Cisco switches.
- A switchport in dynamic auto mode will NOT actively try to form a trunk with other Cisco switches.
- Interfaces on newer Cisco switches default to switchport mode dynamic auto
- Interfaces on older Cisco switches default to switchport mode dynamic desirable

## Q&A

### VTP Storage Behavior

- Q: Does a VTP server maintain its VLAN database in NVRAM?  
  A: Yes  
- Q: Does a VTP transparent maintain its VLAN database in NVRAM?  
  A: Yes  
- Q: Does a VTPv1/v2 client maintain its VLAN database in NVRAM?  
  A: No  
- Q: Does a VTPv3 client maintain its VLAN database in NVRAM?  
  A: Yes  

### VTP Version Support

- Q: Does VTPv1 support the extended VLAN range (1006–4094)?  
  A: No  
- Q: Does VTPv2 support the extended VLAN range (1006–4094)?  
  A: No  
- Q: Does VTPv3 support the extended VLAN range (1006–4094)?  
  A: Yes  

### VTP/DTP Basics

- Q: How many versions of VTP are there?  
  A: 3  
- Q: In DTP trunk encapsulation negotiation, which encapsulation type is favored?  
  A: ISL  

### Modes

- Q: What are the three VTP modes?  
  A:  
  1: Server  
  2: Client  
  3: Transparent  

- Q: What are the two DTP interface modes?  
  A:  
  1: switchport mode dynamic auto  
  2: switchport mode dynamic desirable  

- “What happens when both sides of a link are dynamic auto?”
Access port results — no trunk is formed

- “Which encapsulation does DTP prefer when negotiating trunking?”
ISL, but it's deprecated; 802.1Q is standard today


## Why It Feels Weird
Because “auto + auto” doesn’t make a trunk, even though you’re using "dynamic" on both ends. You expect it to just work, but:
- Auto waits for the other side.
- If both are waiting (auto + auto), nobody ever speaks up.
It’s a classic "both ends are passive" scenario.

| **Feature**       | **Relationship**                                                |
|-------------------|------------------------------------------------------------------|
| ISL               | Cisco trunk encapsulation (deprecated)                          |
| 802.1Q            | Industry standard trunk encapsulation                           |
| EtherChannel      | Requires mode matching, can be impacted by trunking mode        |
| VLAN database     | Stored in vlan.dat (flash) on server/transparent mode           |

| **Issue**                 | **Symptom or Command Feedback**                          |
|---------------------------|-----------------------------------------------------------|
| VLANs missing after trunk | `show vlan brief` → only default VLAN                    |
| Trunks not forming        | `show interfaces trunk` → empty output                   |
| VTP status unknown        | `show vtp status` → incorrect domain or mode             |
| High VTP revision mismatch| `show vtp status` → reveals mismatched rev              |

| **Mnemonic**                                | **Meaning**                                                                 |
|--------------------------------------------|------------------------------------------------------------------------------|
| "Auto + Auto = No Go"                      | `dynamic auto` on both sides means no trunk will form                       |
| "Transparent doesn’t care, but remembers"  | VTP transparent mode stores VLANs locally but ignores VTP synchronization   |
| "VTP 3 is VIP"                             | Only VTP version supporting extended VLANs and client-side VLAN storage     |

| **Question**                                                     | **Answer**                                      |
|------------------------------------------------------------------|--------------------------------------------------|
| What are two methods to reset the VTP revision number to 0?     | 1. Change the VTP domain to an unused domain     |
|                                                                  | 2. Change the VTP mode to transparent            |
| When using 802.1Q, which VLAN are DTP frames sent in?            | The native VLAN                                  |
| When using ISL, which VLAN are DTP frames sent in?               | VLAN1                                            |
