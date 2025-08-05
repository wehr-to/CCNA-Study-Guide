## IEEE 802.11 Standards – Frequencies and Max Data Rates

| Standard   | Frequencies (GHz)    | Max Data Rate       |
|------------|----------------------|----------------------|
| 802.11     | 2.4                  | 2 Mbps               |
| 802.11a    | 5                    | 54 Mbps              |
| 802.11b    | 2.4                  | 11 Mbps              |
| 802.11g    | 2.4                  | 54 Mbps              |
| 802.11n    | 2.4 / 5              | 600 Mbps             |
| 802.11ac   | 5                    | 6.93 Gbps            |
| 802.11ax   | 2.4 / 5 / 6          | ~27.72 Gbps (4×802.11ac) |

## IEEE 802.11 Wi-Fi Version Names

| Standard   | Common Wi-Fi Name |
|------------|-------------------|
| 802.11n    | Wi-Fi 4           |
| 802.11ac   | Wi-Fi 5           |
| 802.11ax   | Wi-Fi 6           |

## Wireless Technologies Overview

| Technology             | Description                                      |
|------------------------|--------------------------------------------------|
| WLC (Wireless LAN Controller) | Central controller for managing APs         |
| LWAPP / CAPWAP         | Protocols used by APs to communicate with WLC    |
| Fast Roaming (802.11r) | Reduces time during AP transitions               |
| Beamforming            | Directs signal strength toward clients           |

## Wireless Troubleshooting Table

| Symptom                | Likely Cause                                      | Fix/Considerations                                |
|------------------------|---------------------------------------------------|---------------------------------------------------|
| Dropped VoIP calls     | Overlapping 2.4 GHz channels, CSMA/CA delays      | Use 5 GHz, enable QoS, avoid channel overlap      |
| Wi-Fi not reaching far corners | Attenuation, absorption through walls         | Add APs, use 2.4 GHz, enable mesh                 |
| Intermittent signal    | Reflection/multipath                              | Enable beamforming or adjust AP placement         |
| Slow roaming handoff   | APs on different VLANs or no fast-roam config     | Configure mobility groups or 802.11r              |

## WLC Interface Types

| Interface Type | Purpose                          | Tagged/Untagged        | Notes                                                                 |
|----------------|----------------------------------|-------------------------|-----------------------------------------------------------------------|
| Management     | Main control channel             | Untagged (typically VLAN 0/native) | Used for WLC GUI, CLI, SSH, SNMP, RADIUS                             |
| AP-Manager     | AP join + CAPWAP tunnel terminator | Tagged or untagged     | Older WLCs needed this separate; newer ones combine with management   |
| Dynamic        | Like switchport access VLANs     | Tagged                  | Maps to specific WLANs/SSIDs, used for client traffic                |
| Virtual        | Placeholder IP (loopback-like)   | N/A                     | Used for DHCP relay, guest webauth, mobility anchor                   |
| Service-Port   | Physical out-of-band port        | N/A (untagged)          | Used for recovery, direct console/upgrade if rest of WLC is down     |

## WLC Virtual Interface Functions

| Function                        | Explanation                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| L3 Mobility Anchoring           | WLCs use the Virtual Interface to tunnel client traffic between anchor/foreign controllers |
| Webauth Redirects               | Clients hitting guest SSID get redirected via virtual IP                    |
| DHCP Relay for Roaming Clients | If a client roams to a WLC that’s not their original DHCP handler, virtual IP helps relay |
| Mobility Group Control Messages | Virtual interface used internally for encapsulating and tracking mobility handoffs |

## Wireless Signal Behavior Terms

| Term        | Meaning                                                                 | Real-World Impact                                   |
|-------------|-------------------------------------------------------------------------|-----------------------------------------------------|
| Scattering  | Signal is reflected in multiple directions due to small particles or rough surfaces | Dust, uneven walls cause unstable signal            |
| Reflection  | Signal bounces off a surface (metal, glass, concrete)                   | Creates multipath interference                      |
| Diffraction | Signal bends around edges/objects                                       | Can help signal reach around walls                  |
| Refraction  | Signal bends due to speed change in different medium (e.g., air to glass) | Changes angle of propagation                        |
| Absorption  | Signal is weakened as it's absorbed and turned into heat (e.g., by drywall, wood) | Common cause of low signal indoors                 |

## Wireless Service Set Types

| Type  | Meaning                                        | Example                  |
|-------|------------------------------------------------|--------------------------|
| BSS   | Basic Service Set — AP + clients               | Home router setup        |
| IBSS  | Independent BSS — ad hoc (no AP)               | Laptop-to-laptop direct  |
| ESS   | Extended Service Set — multiple APs with shared SSID | Enterprise Wi-Fi     |
| MBSS  | Mesh BSS — APs relay through each other        | Outdoor mesh, campus wireless |

## 802.11 Wireless Standards

| Standard   | Frequency        | Max Data Rate   | Wi-Fi Name |
|------------|------------------|------------------|------------|
| 802.11     | 2.4 GHz          | 2 Mbps           | -          |
| 802.11a    | 5 GHz            | 54 Mbps          | -          |
| 802.11b    | 2.4 GHz          | 11 Mbps          | -          |
| 802.11g    | 2.4 GHz          | 54 Mbps          | -          |
| 802.11n    | 2.4 / 5 GHz      | 600 Mbps         | Wi-Fi 4    |
| 802.11ac   | 5 GHz            | ~6.93 Gbps       | Wi-Fi 5    |
| 802.11ax   | 2.4 / 5 / 6 GHz  | ~4× 802.11ac     | Wi-Fi 6    |

## Wireless Default Behaviors

| Feature     | Default Behavior          |
|-------------|----------------------------|
| Wireless    | Half-duplex                |
| CSMA/CA     | Always active              |
| SSIDs       | Don’t need to be unique    |
| APs         | Use native VLAN by default |
| Roaming     | Enabled in ESS             |

# Wireless Networking Notes

## Signal Behavior

- Scattering happens when a material causes a signal to scatter in all directions.
- Reflection happens when a signal bounces off of a material, for example metal.
- Diffraction happens when a wave encounters an obstacle and travels around it.
- Refraction happens when a wave is bent when entering a medium where the signal travels at a different speed.
- Absorption happens when a wireless signal passes through a material and is converted into heat, weakening the original signal.
- Amplitude is the maximum strength of the electric and magnetic fields of a wave.
- Frequency measures the number of up/down cycles per a given unit of time.
- The most common measurement of frequency is hertz.
- The term period refers to the amount of time for one cycle of a wave.

## Wireless Infrastructure

- A (Workgroup Bridge) WGB operates as a wireless client of another AP, and can be used to connect wired devices to the wireless network.
- An AP in repeater mode can be used to extend the range of a BSS.
- An AP operating as an outdoor bridge can be used to connect networks over long distances without a physical cable connecting them.
- An IBSS is also called an ad hoc wireless network.
- In 802.11, the upstream wired network is called the DS (Distribution System).
- The SSID is a human-readable name which identifies the service set.
- The BSSID is the MAC address of the AP's radio.
- The Wi-FI Alliance tests and certifies equipment for 802.11 standards compliance interoperability with other devices.
- The area around an AP where its signal is usable is called a BSA (Basic Service Area).
- The Wi-Fi 5 GHz band consists of non-overlapping channels.
- The Wi-Fi 2.4 GHz band consists of overlapping channels.
- The Wi-Fi 2.4 GHz band typically provides further reach.
- To avoid overlapping frequencies, it is recommended to use channels 1, 6, and 11 of the 2.4 GHz band.
- When a client passes between APs in an ESS, it is called roaming.
- Wireless devices that have associated with a BSS are called clients or stations.
- Wireless LANs are defined in IEEE 802.11.
- Wireless networks operate in half-duplex.
- Wireless networks use CSMA/CA to avoid collisions.
- Wireless networks use CSMA/CD to detect and recover from collisions

## Service Set Types

- 802.11 defines three types of service sets:
  - Independent
  - Infrastructure
  - Mesh

## Wireless Bands

- **2.4 GHz**: longer range, more interference, overlapping channels
- **5 GHz**: shorter range, higher speed, non-overlapping channels

## Acronyms

| Acronym     | Stands For                                            |
|-------------|--------------------------------------------------------|
| AP          | Access Point                                           |
| BSA         | Basic Service Area                                     |
| BSS         | Basic Service Set                                      |
| BSSID       | Basic Service Set Identifier                           |
| CSMA/CA     | Carrier Sense Multiple Access with Collision Avoidance |
| DS          | Distribution System                                    |
| ESS         | Extended Service Set                                   |
| GHz         | Gigahertz                                              |
| Hz          | Hertz                                                  |
| IBSS        | Independent Basic Service Set                          |
| kHz         | Kilohertz                                              |
| MBSS        | Mesh Basic Service Set                                 |
| MHz         | Megahertz                                              |
| SSID        | Service Set Identifier                                 |
| THz         | Terahertz                                              |
| WGB         | Workgroup Bridge                                       |


## Common Questions

- **Q: In a BSS, can clients communicate directly with each other?**  
  A: No, they must communicate via the AP

- **Q: Does an SSID have to be unique?**  
  A: No

- **Q: In an MBSS, what does MAP stand for?**  
  A: Mesh Access Point

- **Q: In an MBSS, what does RAP stand for?**  
  A: Root Access Point

- **Q: In an MBSS, which AP is connected to the wired network?**  
  A: RAP (Root Access Point)

- **Q: What are the two main bands used for wireless LAN communications?**  
  1: 2.4GHz  
  2: 5GHz

## Mnemonics and Tips

- **Wi-Fi Bands**: "2 is longer, 5 is faster"
- **Service Set Types**: I'ME = IBSS, Mesh, ESS (skip BSS since it’s base)
- **DORA for DHCP**, **SARD for signal loss** = Scattering, Absorption, Reflection, Diffraction

## Exam Tips

- Trick wording: “Can devices in a BSS talk directly?” (Answer: No, must go through AP)
- Roaming vs. IBSS: “Which topology supports roaming?” (ESS only)
- Data Rate Questions: Watch out for 802.11b (11 Mbps), not 54 Mbps like 802.11g/a
- Channel overlap: 2.4 GHz = only channels 1, 6, 11 are non-overlapping

## Enterprise Deployment

In enterprise environments (like schools, offices, hospitals), deploying a WLC with 20+ APs allows:

- Centralized updates and troubleshooting  
- Unified SSID/roaming experience  
- Role-based access policies  

Cisco’s WLCs include models like:

- Cisco 9800  
- Cisco 2504  
- Embedded WLCs in Catalyst switches  
