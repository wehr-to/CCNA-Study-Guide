| Purpose                                                       | Command Example                                                         |
|----------------------------------------------------------------|--------------------------------------------------------------------------|
| Configure a read-only community string                         | `snmp-server community COMMUNITY_STRING ro`                              |
| Configure a read-write community string                        | `snmp-server community COMMUNITY_STRING rw`                              |
| Configure SNMP contact information for the device              | `snmp-server contact CONTACT_INFO`                                       |
| Configure SNMP location information for the device             | `snmp-server location LOCATION_INFO`                                     |
| Configure SNMP host (NMS), version 2c, with community string   | `snmp-server host IP_ADDRESS version 2c COMMUNITY_STRING`                |
| Configure which SNMP trap types to send to the NMS             | `snmp-server enable traps [trap-types]`                                  |
