# Cisco WLC CLI Commands

| **Command**                                                         | **Purpose / Description**                         |                                  |                          |
| ------------------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------------ |
| `show sysinfo`                                                      | Show WLC system information                       |                                  |                          |
| `config hostname <name>`                                            | Set WLC hostname                                  |                                  |                          |
| `config timezone <zone> <offset>`                                   | Set system timezone                               |                                  |                          |
| `config country <country-code>`                                     | Set regulatory domain for RF compliance           |                                  |                          |
| `show interface summary`                                            | List WLC interfaces                               |                                  |                          |
| `config interface address management <IP> <netmask> <gateway>`      | Set management interface IP, mask, and gateway    |                                  |                          |
| `config interface vlan management <vlan-id>`                        | Set management VLAN ID                            |                                  |                          |
| \`config interface port management <1                               | 2>\`                                              | Bind management to physical port |                          |
| `config network secureweb enable`                                   | Enable HTTPS GUI access                           |                                  |                          |
| `config network secureweb disable`                                  | Disable HTTPS access                              |                                  |                          |
| `config network webmode enable`                                     | Enable HTTP access                                |                                  |                          |
| `config network webmode disable`                                    | Disable HTTP access                               |                                  |                          |
| `config network secureweb port <port>`                              | Set HTTPS access port                             |                                  |                          |
| `show network summary`                                              | Show web access configuration                     |                                  |                          |
| `config wlan create <wlan-id> <ssid> <profile-name>`                | Create a new WLAN (SSID) configuration            |                                  |                          |
| `config wlan enable <wlan-id>`                                      | Enable WLAN                                       |                                  |                          |
| `config wlan disable <wlan-id>`                                     | Disable WLAN                                      |                                  |                          |
| `config wlan delete <wlan-id>`                                      | Delete a WLAN                                     |                                  |                          |
| `config wlan interface <wlan-id> <interface-name>`                  | Bind WLAN to interface                            |                                  |                          |
| `config wlan security wpa2 enable <wlan-id>`                        | Enable WPA2 security for WLAN                     |                                  |                          |
| `config wlan security wpa2 aes enable <wlan-id>`                    | Enable AES encryption for WLAN                    |                                  |                          |
| `config wlan security akm psk set-key ascii <wlan-id> <passphrase>` | Set WPA2-PSK passphrase for WLAN                  |                                  |                          |
| `show wlan summary`                                                 | Show WLANs summary                                |                                  |                          |
| `show wlan <id>`                                                    | Show specific WLAN configuration                  |                                  |                          |
| \`show run                                                          | include SSID\`                                    | Filter config for SSID lines     |                          |
| `show run = section dot11`                                          | View wireless-specific configuration section      |                                  |                          |
| `show ap summary`                                                   | List APs registered to the WLC                    |                                  |                          |
| `show ap config general <AP-name>`                                  | Show detailed AP configuration                    |                                  |                          |
| `config ap name <AP-name> <MAC>`                                    | Rename an AP using its MAC address                |                                  |                          |
| `config ap group-name <AP-name> <group>`                            | Assign AP to an AP group                          |                                  |                          |
| `config ap primary-base <WLC-name> <AP-name> <WLC-IP>`              | Set WLC as primary for AP                         |                                  |                          |
| \`config ap mode \<local                                            | monitor                                           | flexconnect> <AP-name>\`         | Change AP operation mode |
| `config ap ip address static <IP> <netmask> <gateway> <AP-name>`    | Set static IP on AP                               |                                  |                          |
| `show advanced 802.11a summary`                                     | Show RF settings for 5 GHz band                   |                                  |                          |
| `show advanced 802.11b summary`                                     | Show RF settings for 2.4 GHz band                 |                                  |                          |
| `config 802.11a enable`                                             | Enable 802.11a (5 GHz) radios                     |                                  |                          |
| `config 802.11a disable`                                            | Disable 802.11a radios                            |                                  |                          |
| `config 802.11b enable`                                             | Enable 802.11b (2.4 GHz) radios                   |                                  |                          |
| `config 802.11b disable`                                            | Disable 802.11b radios                            |                                  |                          |
| `show wireless interface summary`                                   | Show status of wireless interfaces                |                                  |                          |
| `show controllers dot11Radio 0`                                     | Show radio-specific configs for dot11Radio 0      |                                  |                          |
| `show dot11 associations`                                           | Show associated wireless clients                  |                                  |                          |
| `debug dot11 mobility`                                              | Monitor wireless mobility/roaming events          |                                  |                          |
| `debug client <mac-address>`                                        | Debug specific client traffic and auth            |                                  |                          |
| `show client summary`                                               | Show all connected wireless clients               |                                  |                          |
| `show client detail <mac>`                                          | Show specific client details, including VLAN/auth |                                  |                          |
| `show capwap client rssi`                                           | Show CAPWAP signal strength for clients           |                                  |                          |
| `show capwap client config`                                         | Show CAPWAP config and tunnel state               |                                  |                          |
| `debug capwap events`                                               | Debug CAPWAP control and join processes           |                                  |                          |
| `show ap rogue summary`                                             | Show detected rogue APs                           |                                  |                          |
| `show ap mode summary`                                              | Show AP mode summary                              |                                  |                          |
| `show dot11 security`                                               | Show current wireless security settings           |                                  |                          |
| `show mobility summary`                                             | Show WLC mobility group members                   |                                  |                          |
| `config interface create <name> <vlan-id>`                          | Create new interface bound to VLAN                |                                  |                          |
| `config interface address <name> <IP> <netmask> <gateway>`          | Set interface IP configuration                    |                                  |                          |
| `config interface dhcp <name> <server-IP>`                          | Assign DHCP server to interface                   |                                  |                          |
| `config dhcp interface add <interface-name>`                        | Enable DHCP for interface                         |                                  |                          |
| `config dhcp proxy enable`                                          | Enable DHCP proxy on WLC                          |                                  |                          |
| `config dhcp proxy disable`                                         | Disable DHCP proxy                                |                                  |                          |
| `show dhcp summary`                                                 | Show DHCP statistics                              |                                  |                          |
| `ping <IP-address>`                                                 | Test connectivity to remote IP                    |                                  |                          |
| `traceroute <IP-address>`                                           | Trace packet path to destination                  |                                  |                          |
| `show arp`                                                          | Show ARP table on WLC                             |                                  |                          |
| `show cpu statistics`                                               | Display WLC CPU usage and stats                   |                                  |                          |
| `save config`                                                       | Save current running configuration to memory      |                                  |                          |
| `reset system`                                                      | Reboot the WLC                                    |                                  |                          |
| `show license summary`                                              | Show license usage and status                     |                                  |                          |
| `config license add <license-key>`                                  | Apply a new license to the controller             |                                  |                          |




                 |


