# Port Security and Errdisable Recovery Commands

| **Function** | **Mode** | **Command** |
|--------------|----------|-------------|
| Configure the errdisable recovery interval | Global config | `errdisable recovery interval seconds` |
| Enable errdisable recovery for port security violations | Global config | `errdisable recovery cause psecure-violation` |
| Configure the port security aging time | Interface config | `switchport port-security aging time minutes` |
| Configure the port security aging type | Interface config | `switchport port-security aging type {absolute | inactivity}` |
| Enable aging of static secure MAC addresses | Interface config | `switchport port-security aging static` |
| Configure the port security violation mode | Interface config | `switchport port-security violation {shutdown | restrict | protect}` |
| Enable port security on an interface | Interface config | `switchport port-security` |
| Enable sticky secure MAC address learning | Interface config | `switchport port-security mac-address sticky` |
| Manually configure a secure MAC address | Interface config | `switchport port-security mac-address mac-address` |
| Manually re-enable a disabled port | Interface config | `shutdown` → `no shutdown` |
| Show a summary of errdisable recovery info | Exec | `show errdisable recovery` |
| Show all port-security-enabled ports | Exec | `show port-security` |
| Show secure MAC addresses | Exec | `show mac address-table secure` |
| Show port security info for a specific interface | Exec | `show port-security interface interface` |
| No more than two devices can send traffic into a port | Exec | `switchport port-security maximum 2` |
