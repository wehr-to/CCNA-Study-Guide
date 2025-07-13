# Cisco Wireless LAN Controller (WLC) - Full CCNA Configuration Guide

- Dynamic interfaces are user defined
- Typically used for client data
- WLC contains both static and dynamic interfaces
- Can contain up to four types of static interfaces:

```
Management interface
AP manager interface
Virtual Interface
Service port interface
```

This markdown contains all relevant WLC configuration topics for the CCNA exam, including interface types, switch configurations, WLAN setup, FlexConnect, verification, and official Cisco references. All content is in one block for easy import into your documentation.

## 1. What is a WLC?

A Wireless LAN Controller (WLC) centrally manages Cisco lightweight access points (APs) using the CAPWAP protocol. WLCs simplify enterprise Wi-Fi deployment by handling:

- Authentication & security
- RF management
- VLAN-to-WLAN mappings
- Seamless roaming
- Policy enforcement

**CAPWAP** uses:
- UDP 5246 for control
- UDP 5247 for data

Cisco Reference:  
https://www.cisco.com/c/en/us/products/wireless/8500-series-wireless-controllers/index.html

## 2. WLC Interface & Port Types

### Physical Ports
- **Service Port** – Out-of-band management (untagged)
- **Distribution Ports** – Connect to switch via 802.1Q trunk
- **Console Port** – CLI access (RJ-45 or mini USB)
- **LAG (Link Aggregation Group)** – Combines distribution ports for redundancy and load balancing

### Logical Interface Types

| Interface      | Purpose                                                                 |
|----------------|-------------------------------------------------------------------------|
| **Management** | WLC IP used for SSH, GUI, SNMP, AP registration                         |
| **AP-Manager** | Source/destination for CAPWAP tunnels to APs                            |
| **Dynamic**    | Maps WLAN (SSID) to specific VLAN; carries client data                  |
| **Virtual**    | Used for mobility, web authentication, DHCP relay (e.g. 1.1.1.1 default)|
| **Service**    | Dedicated to OOB management via Service Port                            |

Cisco Reference:  
https://www.cisco.com/c/en/us/td/docs/wireless/controller/7-6/configuration-guide/b_cg76/b_cg76_chapter_011010.pdf

## 3. Initial WLC Setup

### CLI Example:
```bash
# Configure management interface
config interface address management 192.168.10.2 255.255.255.0 192.168.10.1
config interface port management 1

# Create and configure a dynamic interface
config interface create VLAN20 20
config interface address VLAN20 192.168.20.2 255.255.255.0 192.168.20.1
config interface port VLAN20 1

# Add AP-manager functionality if needed
config interface ap-manager add VLAN20
```

```
GUI Path:
Go to Controller > Interfaces > New
Name: VLAN20
VLAN ID: 20
Port: 1
IP: 192.168.20.2, Subnet, Gateway
Enable DHCP relay if needed
Save
```

## 4. Switch Configuration for WLC
- Ensure the switchport connected to the WLC is set as a trunk and allows all necessary VLANs.
```
vlan 10
 name MANAGEMENT
vlan 20
 name CORPORATE

interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```

```
VLAN 10 → Management interface
VLAN 20 → Dynamic interface for WLAN clients
```
Cisco Community:
https://community.cisco.com/t5/wireless/switch-port-configuration-for-wlc/td-p/3265460

## 5. Dynamic Interfaces
- Dynamic interfaces are required to link SSIDs to VLANs. Each SSID should map to a dedicated VLAN using a dynamic interface.

```
config interface create VLAN30 30
config interface address VLAN30 192.168.30.2 255.255.255.0 192.168.30.1
config interface port VLAN30 1
```

```
GUI:
Go to Controller > Interfaces > New
Name: VLAN30
VLAN ID: 30
Port: 1
IP: 192.168.30.2 /24, Gateway: 192.168.30.1
Save
```

Cisco Guide:
https://www.cisco.com/c/en/us/td/docs/wireless/controller/7-4/configuration/guides/consolidated/b_cg74_CONSOLIDATED/m_configuring_dynamic_interfaces.html

## 6. WLAN/SSID Configuration
- Each SSID must be created and mapped to a dynamic interface to allow clients to associate.

```
CLI Example:
# Create WLAN
config wlan create 10 CorpSSID CorpSSID

# Enable it
config wlan enable 10

# Bind to VLAN30 dynamic interface
config wlan interface 10 VLAN30

# Set WPA2 PSK
config wlan security wpa akm psk set-key ascii 10 SecurePass123
```
```
GUI:
Go to WLANs > Create New
Profile Name: CorpSSID
SSID: CorpSSID
Enable Status
Interface: VLAN30
Security > Layer 2: WPA2 PSK
Set PSK: SecurePass123
Save
```

## 7. FlexConnect (for remote sites)
- Allows APs to forward traffic locally instead of tunneling to WLC. Useful in branch deployments.

```
CLI Example:
config wlan flexconnect local-switching 10 enable
config wlan flexconnect local-authentication 10 enable
config wlan flexconnect central-dhcp 10 disable
```
```
GUI Path:
Wireless > AP > FlexConnect
Enable FlexConnect
Enable Local Switching and Local Authentication (optional)
```

## Commands:
```
show interface summary
show interface detailed VLAN30
show wlan summary
show wlan 10
show ap summary
show ap config general <ap-name>
show run-config
```

### Cisco Guide:
https://www.cisco.com/c/en/us/td/docs/wireless/controller/8-5/config-guide/b_cg85/flexconnect.html

```
9. Best Practices
Use separate VLANs for management and client data
Never assign WLANs to the management interface
Use strong PSKs or 802.1X for secure WLANs
Disable HTTP access to WLC GUI (use HTTPS only)
Enable LAG if multiple distribution ports are in use
Use DNS and DHCP options to simplify AP join process
Backup configurations regularly
Use FlexConnect in remote sites with WAN constraints
```

| Task                           | CLI Command                                      |
| ------------------------------ | ------------------------------------------------ |
| Create dynamic interface       | `config interface create VLANXX XX`              |
| Set interface IP/gateway       | `config interface address VLANXX IP MASK GW`     |
| Assign interface to port       | `config interface port VLANXX 1`                 |
| Enable AP-Manager on interface | `config interface ap-manager add VLANXX`         |
| Create WLAN                    | `config wlan create <ID> <Name> <SSID>`          |
| Enable WLAN                    | `config wlan enable <ID>`                        |
| Assign WLAN to interface       | `config wlan interface <ID> VLANXX`              |
| Set WPA2 PSK                   | `config wlan security wpa akm psk set-key ascii` |
| Enable FlexConnect             | `config wlan flexconnect local-switching`        |
| View interfaces                | `show interface summary`                         |
| Save config                    | `save config`                                    |

📚 Cisco Best Practices:
https://www.cisco.com/c/en/us/td/docs/wireless/controller/technotes/8-6/b_Cisco_Wireless_LAN_Controller_Configuration_Best_Practices.html


