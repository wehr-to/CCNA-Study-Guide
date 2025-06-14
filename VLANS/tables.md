# VLAN Concepts and Terms

| **Term**             | **Explanation**                                                                 |
|----------------------|----------------------------------------------------------------------------------|
| Broadcast Domain      | All devices that receive a Layer 2 broadcast (FFFF.FFFF.FFFF)                   |
| Access Port           | Belongs to one VLAN, connects to PCs, printers, etc.                            |
| Trunk Port            | Carries multiple VLANs, used between switches or routers                        |
| VLAN                  | Virtual LAN — logically groups ports to segment broadcast domains               |
| SVI                   | Switch Virtual Interface — used for Layer 3 communication between VLANs         |
| ROAS                  | Router-on-a-Stick — uses subinterfaces for inter-VLAN routing                   |
| Multilayer Switch     | A switch with Layer 3 capabilities (routing, SVIs, etc.)                         |
| Tagged/Untagged       | Trunk = tagged frames; Access = untagged frames                                 |
| Default VLAN          | VLAN 1 — where all ports reside initially                                       |

# 802.1Q VLAN Tag Fields

| **Field** | **Length** | **Meaning**                                               |
|-----------|------------|------------------------------------------------------------|
| TPID      | 16 bits    | Always 0x8100 — signals frame is tagged                    |
| PCP       | 3 bits     | Priority Code Point — for QoS/CoS                          |
| DEI       | 1 bit      | Drop Eligible Indicator — discard if congested             |
| VID       | 12 bits    | VLAN ID (1–4094)                                           |

# VLAN ID Ranges

| **Range**   | **Purpose**                      |
|-------------|----------------------------------|
| 1–1005      | Normal range                     |
| 1006–4094   | Extended range                   |
| 0, 4095     | Reserved (cannot be used)        |
