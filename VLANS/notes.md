# Real-World VLAN Scenarios

## 1. Security Misconfig
- **Symptom:** Unwanted VLAN hopping or rogue DHCP servers  
- **Cause:** Native VLAN left as VLAN 1 across trunk links  
- **Fix:** Change native VLAN to unused one (e.g., VLAN 999)

## 2. Inter-VLAN Traffic Fails
- **Symptom:** Devices in different VLANs can’t talk  
- **Cause:** No routing, either no ROAS or SVIs not configured  
- **Fix:** Use ROAS on router or `ip routing` with SVIs on multilayer switch

## 3. Trunk Mismatch
- **Symptom:** Hosts in same VLAN on different switches can’t communicate  
- **Cause:** VLAN not allowed on trunk or encapsulation mismatch  
- **Fix:** Check allowed VLANs with `show interfaces trunk`, ensure dot1q used

## 4. SVI Not Working
- **Symptom:** SVI IP unreachable  
- **Cause:** VLAN doesn’t exist or has no active ports  
- **Fix:** Ensure VLAN is created and assigned to at least one up/up port

# VLAN Key Concepts

- A **broadcast domain** is the group of devices which will receive a frame with the destination MAC address `FFFF.FFFF.FFFF`.
- An **access port** is a switchport which belongs to a single VLAN, and usually connects to end hosts like PCs.
- **Trunk ports** carry multiple VLANs and are used between switches/routers.
- **VLANs** are used to split up broadcast domains and operate at Layer 2 of the OSI model.
- The **default native VLAN** is VLAN 1 on all trunk ports.
- For **security**, it is best to change the native VLAN to an unused VLAN.
- The **802.1Q tag** is inserted after the Source MAC Address field of the Ethernet header.
- **ROAS** involves configuring VLAN tags and IPs on router subinterfaces.
- The **switch does not tag** native VLAN traffic on trunk links.
- **SVIs** are virtual interfaces with IPs used for inter-VLAN routing on multilayer switches.
- **SVIs are shutdown by default.**

# VLAN Ranges

| Range       | Purpose          |
|-------------|------------------|
| 1–1005      | Normal range     |
| 1006–4094   | Extended range   |
| 0, 4095     | Reserved (unused)|

- The total **usable VLAN range** is **1–4094**.

# VLAN Tagging

- Trunk ports = **tagged**
- Access ports = **untagged**
- Switches **tag frames** with a VLAN ID on trunk ports.
- **Untagged frames** on trunk ports are assumed to belong to the **native VLAN**.

# VLAN FAQs

- **Q:** What are the 5 VLANs that exist by default on a Cisco switch?  
  **A:** 1, 1002, 1003, 1004, 1005

- **Q:** What VLAN are Cisco switch interfaces in by default?  
  **A:** VLAN 1

- **Q:** Will a Layer 2 switch forward traffic between VLANs?  
  **A:** No

- **Q:** What does DEI stand for?  
  **A:** Drop Eligible Indicator

- **Q:** What does PCP stand for?  
  **A:** Priority Code Point

- **Q:** What does TPID stand for?  
  **A:** Tag Protocol Identifier

- **Q:** What does VID stand for?  
  **A:** VLAN ID

- **Q:** What is a Cisco proprietary VLAN trunking protocol?  
  **A:** ISL (Inter-Switch Link)

- **Q:** What is an industry standard VLAN trunking protocol?  
  **A:** IEEE 802.1Q (dot1q)

- **Q:** What does SVI stand for?  
  **A:** Switch Virtual Interface

- **Q:** What is another name for a 'Layer 3 switch'?  
  **A:** Multilayer Switch

- **Q:** What is another name for a 'Multilayer Switch’?  
  **A:** Layer 3

# 802.1Q Tag Details

- 802.1Q tag: The **VID** field identifies the VLAN the frame belongs to.
- 802.1Q tag: The **DEI** field indicates that a frame can be dropped if the network is congested.
- 802.1Q tag: The **PCP** field is used for Class of Service (CoS).
- 802.1Q tag: The **DEI** field is **1 bit** in length.
- 802.1Q tag: The **PCP** field is **3 bits** in length.
- 802.1Q tag: The **TPID** field is **16 bits** in length.
- The **802.1Q tag** is **4 bytes** in total length.
- 802.1Q tag: The **TPID** field is always set to a value of **0x8100**.
