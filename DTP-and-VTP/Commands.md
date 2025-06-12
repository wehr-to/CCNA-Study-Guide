## DTP Configuration Commands

| Purpose                                             | Command                                   |
|-----------------------------------------------------|-------------------------------------------|
| Configure DTP in auto mode on a switchport          | `switchport mode dynamic auto`            |
| Configure DTP in desirable mode on a switchport     | `switchport mode dynamic desirable`       |
| Disable DTP negotiation (Option 1)                  | `switchport mode access`                  |
| Disable DTP negotiation (Option 2)                  | `switchport nonegotiate`                  |

## DTP Mode Outcomes
| SW1 Mode           | SW2 Mode           | Resulting Operational Mode |
|--------------------|--------------------|-----------------------------|
| dynamic auto       | dynamic auto       | Static access               |
| dynamic auto       | static access      | Static access               |
| dynamic auto       | trunk              | Trunk                       |
| dynamic desirable  | dynamic auto       | Trunk                       |
| dynamic desirable  | dynamic desirable  | Trunk                       |
| dynamic desirable  | static access      | Static access               |
| dynamic desirable  | trunk              | Trunk                       |
