# Wireless architectures

**“Which frames are protected under 802.11w?”**  
- Beacon
- Disassociation, Deauthentication, Action  

**“What does 802.11w protect?”**  
- Control frames  
- Management frames  

Cisco exam may call it: **Management Frame Protection (MFP)**

## Management Frame Vulnerabilities

By default, management frames (like deauthentication, disassociation, beacon frames) are unencrypted — meaning attackers can:
- Spoof fake deauth frames
- Kick users off a network
- Set up evil twin APs

802.11w encrypts and authenticates certain management frames, preventing spoofing and forging of:
- Deauthentication
- Disassociation
- Action frames

This blocks one of the most common Wi-Fi attack vectors.

## Quick Memory Hooks

- **w = wall** > Builds a wall around management frames (protection)  
- **k = know** > Helps devices "know" nearby APs  
- **r = run** > Helps clients run (roam) fast between APs  
- **v = vote** > APs "vote" and suggest where a client should roam / POWER SAVINGS TOO

## 802.11 Message Types

**What 802.11 message type?**
- ACK = Control  
- Association request = Management  
- Association response = Management  
- Authentication = Management  
- Beacon = Management  
- CTS = Control  
- Probe request = Management  
- Probe response = Management  
- RTS = Control  

**What are the three 802.11 message types?**
1. Management  
2. Control  
3. Data  

## Wireless AP Deployment Methods (Architectures)

**What are the three main wireless AP deployment methods?**
1. Autonomous  
2. Lightweight  
3. Cloud-based  

## 802.11 Connection States

There are three 802.11 connection states:
1. Not Authenticated, not Associated  
2. Authenticated, not Associated  
3. Authenticated and Associated  

## CAPWAP Facts

- CAPWAP Control tunnels use **UDP port 5246**
- CAPWAP Data tunnels use **UDP port 5247**
- CAPWAP control tunnel is **encrypted by default**
- CAPWAP data tunnel is **not encrypted by default**

## AP Deployment Characteristics

- Cloud-based AP architecture is between autonomous AP and split-MAC architecture in terms of functionality.
- Autonomous APs are self-contained systems that don't rely on a WLC.
- A Unified WLC is a hardware appliance in a central location of the network.
- A Cloud-based WLC is a VM running on a server, usually in a private cloud in a data center.
- A Mobility Express WLC is integrated within an AP.
- The use of lightweight APs and WLCs is also known as split-MAC architecture.

## WLC Capacity

- A Cloud-based WLC can support about **3000 APs**
- A Mobility Express WLC can support about **100 APs**
- A Unified WLC can support about **6000 APs**
- An Embedded WLC can support about **200 APs**

## Connectivity

- Autonomous APs connect to a switch via **trunk ports**
- Lightweight APs connect to a switch via **access ports**
- An Embedded WLC is integrated within a switch.
- Cisco Meraki is a popular cloud-based AP solution

## Key Questions

**Q: How many CAPWAP tunnels does a lightweight AP form with the WLC?**  
A: 2 (control and data)  

**Q: What does CAPWAP stand for?**  
A: Control and Provisioning of Wireless Access Points  

**Q: What does LWAPP stand for?**  
A: Lightweight Access Point Protocol  

**Q: What does WLC stand for?**  
A: Wireless LAN Controller  

**Q: What is the default operating mode of a lightweight AP, in which it offers a BSS for clients?**  
A: Local  

## AP Operating Modes

**Q: Which feature allows a lightweight AP to locally switch traffic if the tunnels to the WLC go down?**  
A: FlexConnect  

**Q: Which lightweight AP operating mode adds FlexConnect functionality to the Bridge/Mesh mode?**  
A: Flex plus Bridge  

**Q: Which lightweight AP operating mode can form a dedicated bridge between sites?**  
A: Bridge/Mesh (a mesh can be formed between the APs)  

**Q: Which lightweight AP operating mode is dedicated to capturing 802.11 frames and sending them to a device running software such as Wireshark?**  
A: Sniffer  

**Q: Which lightweight AP operating mode is dedicated to listening to traffic on the wired network to detect rogue devices? (it does not use its radio)**  
A: Rogue Detector  

**Q: Which lightweight AP operating mode is dedicated to receiving 802.11 frames to detect rogue devices?**  
A: Monitor  

**Q: Which lightweight AP operating mode is dedicated to RF spectrum analysis on all channels?**  
A: SE-Connect  

## Scanning Behavior

**Q: Which messages does a wireless station listen for when doing 802.11 passive scanning?**  
A: Beacon  

**Q: Which two messages are used for 802.11 active scanning?**  
1. Probe request  
2. Probe response  

| Protocol  | Name                        | Purpose / What it Improves                                     | Exam Focus            |
|-----------|-----------------------------|----------------------------------------------------------------|------------------------|
| 802.11w   | Protected Management Frames | Protects management frames from being spoofed/deauth attacks   | Spoofing protection    |
| 802.11k   | Radio Resource Management   | Helps clients quickly discover nearby APs (site reports)       | Fast roaming prep      |
| 802.11r   | Fast BSS Transition         | Speeds up handoffs when roaming between APs                    | Fast roaming           |
| 802.11v   | Wireless Network Management | Lets APs influence roaming decisions (suggest better APs)      | Roaming optimization   |

| Feature                                | Default State     |
|----------------------------------------|-------------------|
| Mgmt frame encryption (pre-802.11w)    | Unencrypted       |
| 802.11w on WPA2-Enterprise             | Required          |
| 802.11w on WPA2-PSK                    | Optional (config-dependent) |

| Problem                                | Result                                        | 802.11w Fix?            |
|----------------------------------------|-----------------------------------------------|--------------------------|
| Rogue AP fakes disassociation          | Devices get kicked off legit network          | Yes                      |
| Evil twin mimics a real AP             | User joins attacker AP instead of legit one   | Not directly (but helps detect mismatch) |
| VoIP or medical devices disconnect     | High impact from spoofed deauth               | Yes                      |

| Type       | Examples                                                                 |
|------------|--------------------------------------------------------------------------|
| Management | Beacon, Association/Disassociation, Authentication, Probe Req/Resp       |
| Control    | ACK, RTS/CTS                                                             |
| Data       | Client → Server traffic                                                  |

| Architecture        | Description                                 | Real-World Use                       |
|---------------------|---------------------------------------------|--------------------------------------|
| Autonomous          | Standalone APs (no central controller)      | Small offices, legacy networks       |
| Lightweight (Split-MAC) | Control plane on WLC, AP handles data plane | Large enterprise networks            |
| Cloud-based         | APs managed via cloud portal (e.g., Meraki) | Distributed campuses, modern setups |

| State | Meaning                          |
|-------|----------------------------------|
| 1     | Not authenticated or associated  |
| 2     | Authenticated, not associated    |
| 3     | Authenticated and associated     |

| Mode         | Function                                                       |
|--------------|----------------------------------------------------------------|
| Local        | Default mode: provides client access                           |
| FlexConnect  | APs can switch traffic locally if CAPWAP breaks                |
| Bridge/Mesh  | Connects sites wirelessly over long distance                   |
| Flex+Bridge  | Combines FlexConnect + Mesh                                    |
| Sniffer      | Captures 802.11 frames, sends to analyzer (Wireshark, etc.)    |
| Monitor      | Scans wireless space for rogue APs                             |
| Rogue Detector | Scans wired network for rogue devices                        |
| SE-Connect   | Performs RF spectrum analysis                                  |

| Type    | Port     | Encrypted |
|---------|----------|-----------|
| Control | UDP 5246 | Yes       |
| Data    | UDP 5247 | No (optional) |

| Related Feature | Depends On                        |
|------------------|-----------------------------------|
| 802.11w          | WPA2/WPA3 security                |
| CAPWAP           | Reachable WLC + Layer 3           |
| FlexConnect      | Required when WLC link may go down|
| Sniffer Mode     | Controller + Analyzer app         |

| Problem                       | Log Cue or Command                          |
|------------------------------|---------------------------------------------|
| Mgmt frame spoofing attempts | `debug dot11 security`                      |
| CAPWAP tunnel not forming     | `%CAPWAP-3-ERRORLOG` / `%LWAPP-5-CHANGED`   |
| Client can't associate        | `show wireless client summary`             |

| 802.11 Frame Field     | Length     |
|------------------------|------------|
| Address 1/2/3/4        | 6 bytes (each) |
| Duration/ID           | 2 bytes    |
| FCS (Frame Check Seq) | 4 bytes    |
| Frame Control         | 2 bytes    |
| HT Control            | 4 bytes    |
| QoS Control           | 2 bytes    |
| Sequence Control      | 2 bytes    |

