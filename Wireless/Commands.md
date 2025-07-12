## Wireless Debug & Show Commands

| **Command**                                | **Purpose / Description**                                     |
|--------------------------------------------|---------------------------------------------------------------|
| `show wireless interface summary`          | Show status of wireless interfaces                            |
| `show controllers dot11Radio 0`            | View radio-specific configurations                            |
| `show dot11 associations`                  | Show associated clients                                       |
| `debug dot11 mobility`                     | View roaming and association events                           |
| `show run = section dot11`                 | View wireless-specific configuration section                  |
| `show ap summary`                          | Show wireless stats                                           |
| `show capwap client rssi`                  | Show wireless stats                                           |
| `show wireless security mfp`               | View 802.11 management protection                             |
| `show capwap client config`                | Check CAPWAP tunnel status                                    |
| `debug capwap events`                      | Check CAPWAP tunnel status                                    |
| `show ap rogue summary`                    | View rogue devices or passive AP modes                        |
| `show ap mode summary`                     | View rogue devices or passive AP modes                        |
| `show dot11 security`                      | Check WPA settings on AP                                      |
| `show run \| include SSID`                 | Check WPA settings on AP                                      |
| `show wlan summary`                        | View authentication and key types                             |
| `show wlan <id>`                           | View authentication and key types                             |
| `debug client <mac-address>`              | View authentication and key types                             |
| `show wlan <id>`                           | View WLAN settings (security, QoS, VLAN)                      |
| `show interface summary`                   | List WLC interfaces                                           |
| `show interface detailed <int>`            | Inspect CAPWAP, DHCP relay, and VLAN settings                 |
| `show AP summary`                          | View AP to WLC tunnel status                                  |
| `show client detail <mac>`                | Check auth method, state, and assigned VLAN                   |

## WLC Configuration commands: 
# Cisco WLC CLI Configuration Commands for CCNA (Markdown Table Format)

| Function                        | Command                                                             |         |                          |
| ------------------------------- | ------------------------------------------------------------------- | ------- | ------------------------ |
| Show WLC system info            | `show sysinfo`                                                      |         |                          |
| Set hostname                    | `config hostname <name>`                                            |         |                          |
| Set timezone                    | `config timezone <zone> <offset>`                                   |         |                          |
| Set country regulatory domain   | `config country <country-code>`                                     |         |                          |
| Show interfaces summary         | `show interface summary`                                            |         |                          |
| Set management IP               | `config interface address management <IP> <netmask> <gateway>`      |         |                          |
| Set management VLAN             | `config interface vlan management <vlan-id>`                        |         |                          |
| Set management port             | \`config interface port management <1 2>\`                          |         |                          |
| Create WLAN                     | `config wlan create <wlan-id> <ssid> <profile-name>`                |         |                          |
| Enable WLAN                     | `config wlan enable <wlan-id>`                                      |         |                          |
| Disable WLAN                    | `config wlan disable <wlan-id>`                                     |         |                          |
| Delete WLAN                     | `config wlan delete <wlan-id>`                                      |         |                          |
| Bind WLAN to interface          | `config wlan interface <wlan-id> <interface-name>`                  |         |                          |
| Enable WPA2 on WLAN             | `config wlan security wpa2 enable <wlan-id>`                        |         |                          |
| Enable AES on WLAN              | `config wlan security wpa2 aes enable <wlan-id>`                    |         |                          |
| Set WPA2 PSK                    | `config wlan security akm psk set-key ascii <wlan-id> <passphrase>` |         |                          |
| Show AP summary                 | `show ap summary`                                                   |         |                          |
| Show AP config                  | `show ap config general <AP-name>`                                  |         |                          |
| Rename AP                       | `config ap name <AP-name> <MAC>`                                    |         |                          |
| Assign AP to group              | `config ap group-name <AP-name> <group>`                            |         |                          |
| Set AP primary WLC              | `config ap primary-base <WLC-name> <AP-name> <WLC-IP>`              |         |                          |
| Set AP mode                     | \`config ap mode \<local                                            | monitor | flexconnect> <AP-name>\` |
| Set static AP IP address        | `config ap ip address static <IP> <netmask> <gateway> <AP-name>`    |         |                          |
| Show 802.11a RF summary         | `show advanced 802.11a summary`                                     |         |                          |
| Show 802.11b RF summary         | `show advanced 802.11b summary`                                     |         |                          |
| Enable 802.11a radio            | `config 802.11a enable`                                             |         |                          |
| Enable 802.11b radio            | `config 802.11b enable`                                             |         |                          |
| Disable 802.11a radio           | `config 802.11a disable`                                            |         |                          |
| Disable 802.11b radio           | `config 802.11b disable`                                            |         |                          |
| Create VLAN interface           | `config interface create <name> <vlan-id>`                          |         |                          |
| Set interface IP                | `config interface address <name> <IP> <netmask> <gateway>`          |         |                          |
| Assign DHCP server to interface | `config interface dhcp <name> <server-IP>`                          |         |                          |
| Assign DHCP to interface        | `config dhcp interface add <interface-name>`                        |         |                          |
| Enable/disable DHCP proxy       | `config dhcp proxy enable/disable`                                  |         |                          |
| Show DHCP summary               | `show dhcp summary`                                                 |         |                          |
| Show connected clients          | `show client summary`                                               |         |                          |
| Show WLAN summary               | `show wlan summary`                                                 |         |                          |
| Show specific WLAN config       | `show wlan <wlan-id>`                                               |         |                          |
| Show mobility summary           | `show mobility summary`                                             |         |                          |
| Save running configuration      | `save config`                                                       |         |                          |
| Reboot the controller           | `reset system`                                                      |         |                          |
| Ping tool                       | `ping <IP-address>`                                                 |         |                          |
| Traceroute tool                 | `traceroute <IP-address>`                                           |         |                          |
| Show ARP table                  | `show arp`                                                          |         |                          |
| Show CPU stats                  | `show cpu statistics`                                               |         |                          |
| Show license summary            | `show license summary`                                              |         |                          |
| Add license key                 | `config license add <license-key>`                                  |         |                          |


