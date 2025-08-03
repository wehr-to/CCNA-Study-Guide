# Cisco SDN and ACI/DNA Study Notes

## Acronyms

- **Q: What does Cisco ACI stand for?**  
  - Application-Centric Infrastructure

- **Q: What does Cisco DNA stand for?**  
  - Digital Network Architecture

- **Q: What does CTS stand for?**  
  - Cisco TrustSec

- **Q: What does IBN stand for?**  
  - Intent-Based Networking

- **Q: What does LISP stand for?**  
  - Locator ID Separation Protocol

- **Q: What does VXLAN stand for?**  
  - Virtual Extensible LAN

## Cisco SDN Solutions

- SD-Access is Cisco's SDN solution for automating campus LANs.  
- ACI is Cisco's SDN solution for automating data center networks.  
- SD-WAN is Cisco's SDN solution for automating WANs.  

## Cisco SD-Access Architecture

- Cisco TrustSec provides policy control in Cisco SD-Access.  
- LISP provides the control plane of Cisco SD-Access.  
- VXLAN provides the data plane of Cisco SD-Access.

## SDN Fabric Concepts

- In SDN, the fabric is the combination of the overlay and underlay.  
- In SDN, the underlay is the physical network of devices and connections.  
- In SDN, the overlay is the virtual network built on top of the physical network.  

## SDN Architecture Layers

- The Application layer of SDN architecture contains scripts and applications that interact with the SDN controller.  
- The Infrastructure layer of SDN architecture contains the network devices.  
- The Control layer of SDN architecture contains the SDN controller.  

## Cisco SD-Access Switch Types

**Q: What are the three switch types in Cisco SD-Access?**
- Edge Node = End hosts 
- Border Node = connect to devices outside of SD access domain 
- Control Node

- New deplotment / greenfield
- all switches are L3 and use IS IS as routing protocol
- Edge notes (access switches) act as default gateway

- Cisco trust sec (CTS) provides policy control, QOS, sec policy, etc
- VXlan provides the data plane of SD access

- DNA center (SDN controller, Network manager in a traditional network)
- DNA center installed on Cisco UCS server hardware
- Has a REST API which can interact with DNA center
- SBI supports protocols such as NETCONF and RESTCONF, as well as traditional protocols like telnet, ssh, and SNMP
- Allows engineers to specify intent of policies
