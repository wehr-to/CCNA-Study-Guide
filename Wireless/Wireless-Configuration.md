## Cisco WLC & WLAN Security Notes

### Layer 2 Security Mechanisms
- 802.1X is a Layer 2 security mechanism.
- CKIP is a Layer 2 security mechanism. (CKIP = Cisco Key Integrity Protocol)
- None + EAP Passthrough is a Layer 2 security mechanism.
- Static WEP is a Layer 2 security mechanism.
- Static WEP + 802.1X is a Layer 2 security mechanism.
- WPA + WPA2 is a Layer 2 security mechanism.

### Layer 3 Security Mechanisms
- Web Authentication is a Layer 3 security mechanism.
- Web Passthrough is a Layer 3 security mechanism.
- Splash Page Web Redirect is a Layer 3 security mechanism.
- Conditional Web Redirect is a Layer 3 security mechanism.

### WLAN QoS Tiers
| QoS Tier   | Label        | Usage Type     |
|------------|--------------|----------------|
| Bronze     | background   | Low priority   |
| Silver     | best effort  | Default level  |
| Gold       | video        | Multimedia     |
| Platinum   | voice        | Highest priority |

- Silver is the **default QoS** setting of a WLAN.

### WLAN PSK Configuration
- WLAN PSKs in **ASCII format** must be at least **8 characters**.
- WLAN PSKs can be configured in:
  - **ASCII**
  - **HEX**

### WLC Interface Functions

| Interface Type            | Purpose                                                                 |
|---------------------------|-------------------------------------------------------------------------|
| **Service Port**          | Used for out-of-band management; must connect to a switch **access port** |
| **Redundancy Port**       | Used to connect to another WLC to form a **HA (High Availability)** pair |
| **Redundancy Management** | Used to manage the **standby** WLC in a HA pair                          |
| **Virtual Interface**     | Used to **relay DHCP**, perform **web authentication**, etc., with clients |
| **Distribution System**   | Connects WLC to the **switched network** for normal data traffic         |
| **Dynamic Interfaces**    | Map WLANs to VLANs                                                      |

- CAPWAP tunnels are formed to/from the **WLC's management interface**.

### General WLC Notes
- WLCs only support **static LAG** (PAgP and LACP are **not supported**).
- In the context of WLCs:
  - **Port** = physical
  - **Interface** = logical
- DHCP Option 43 can be used to tell APs the IP address of their **WLC**.
- CPU ACLs can be used to limit management traffic destined for the **WLC itself**.

## Security Types by Layer

| **Security Type**         | **Layer** | **Description**                                        |
|---------------------------|-----------|--------------------------------------------------------|
| 802.1X                    | L2        | Auth framework using EAP, often via RADIUS            |
| Static WEP                | L2        | Legacy encryption, fixed key per SSID                 |
| CKIP                      | L2        | Cisco-proprietary enhancement to WEP                  |
| None + EAP Passthrough    | L2        | No encryption, but client initiates EAP               |
| Web Auth                  | L3        | HTTP-based login page (local or external)             |
| Web Passthrough           | L3        | Allows HTTP only, no credentials required             |
| Conditional Redirect      | L3        | Redirect only unauthenticated or failed policy clients|

## WLC and WLAN Feature Defaults

| **Feature**                    | **Default**                        |
|--------------------------------|------------------------------------|
| WLAN QoS Profile               | Silver (Best Effort)               |
| WLC LAG Support                | Static only (no LACP/PAgP)         |
| Web Auth Port Use              | Layer 3 via virtual interface      |
| CAPWAP Control Tunnel Encryption |   Always encrypted               |

## WLC Interface Roles and Purposes

| **WLC Interface**          | **Purpose**                                                                 |
|----------------------------|------------------------------------------------------------------------------|
| Service Port               | For out-of-band mgmt (static IP, connect to switch access port)              |
| Management Interface       | Used for CAPWAP tunnel endpoints, WLC GUI/API access                         |
| Redundancy Port            | Direct cable to peer WLC (HA SSO setup)                                      |
| Redundancy Mgmt Int        | Lets you access the standby WLC during failover                              |
| Virtual Interface          | Used for DHCP relay, web auth, and mobility events with clients              |
| Dynamic Interface          | Maps WLANs to VLANs (similar to SVI on switch)                               |
| Distribution System Ports  | Physical uplink ports on the WLC (carries VLAN-tagged traffic)               |

## WLC Feature Dependencies

| **Feature**          | **Dependency or Impact**                             |
|----------------------|------------------------------------------------------|
| 802.1X               | RADIUS or ISE backend                                |
| Web Auth             | Requires DHCP relay via virtual interface            |
| Conditional Redirect | Depends on ACLs and policy engine (ISE)             |
| Static LAG           | Requires manual config on WLC and switch            |

## Troubleshooting WLC Issues

| **Symptom**                    | **Debug or Log Output**                                      |
|-------------------------------|--------------------------------------------------------------|
| Client stuck at Web Auth screen | `debug client <mac>` / virtual interface issue               |
| DHCP not relayed to client     | Check `debug dhcp packet`, inspect virtual interface          |
| CAPWAP tunnel not forming      | `debug capwap events` / wrong management IP or firewall       |
| AP not joining WLC             | Option 43 missing, or DNS resolution fails                   |

## Exam + Boson Angle

**Q: Which security method uses Layer 3 web authentication?**  
- Web Auth  
- 802.1X > Layer 2

**Q: What interface handles DHCP relay and web authentication?**  
- Virtual interface  
- Management > for control plane traffic

**Q: Can WLCs negotiate EtherChannels with LACP?**  
- No, only static LAG is supported

**Q: How many characters must an ASCII PSK be?**  
- Minimum 8 characters

## Mnemonics

- Redundant Mgmt = "Read-only Mgmt of the Standby"
- CAPWAP = "Control And Provisioning of Wireless Access Points"
- Silver QoS = Safe default (best effort)
- Bronze = Background  
- Gold = Video  
- Platinum = Voice
