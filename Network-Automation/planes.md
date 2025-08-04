## Data Plane: 
- All tasks involved in forwarding user data/traffic from one interface to another are part of the data plane
- A router receives a messgae, looks for the most specific matching route in its routing table, and forwards it out of the appropriate interface to the next hop
- It also de encapsulates the original layer 2 header, and re encapsulates with a new header destined for the next hop's MAC address
- A switch receives a message, looks at the destination mac address, and forwards it out of the appropriate interface or floods it
- That includes functions like adding or removing 802.1q VLAN tags
- NAT (changing the src/dst addresses before forwarding), is part of the data plane
- Deciding to forward or discard messgaes due to ACLs, port security, etc is part of the data plane
- The data plane is also called the forwarding plane

## Control Plane

- How does a device's data plane make its forwarding decisons? Routing table, MAC address table, ARP table, STP, etc
- Functions that build these tables (and other functions that influence the data plane) are part of the control plane
- The control plane controls what the data plane does, for example by building the routers routing table
- The control plane performs overhead work
- OSPF itself doesnt forward user packets, but it informs the data plane how packets should be forwarded
- STP itself isnt directly involved in the process of forwarding frames, but it informs the data plane about which interfaces should and shouldnt be used to forward frames
- ARP messages aren't user data, but they are used to build an ARP table which is used in the process of forwarding data

## Management plane: 
- management plane performs overhead work
- However the management plane does not directly affect the forwarding of messages in the data plane

- The management plane consists of protocols that are used to manage devices,
- SSH/telnet used to connect to the CLI of a device to configure/manage it
- Syslog used to keep logs of events that occur on the device
- SNMP, used to monitor the operations of the device
- NTP, used to maintain accurate time on the device

## Logical Planes
- Operations of the management plane and control plane are ususally managed by the CPU
- However this is not desirable for data plane operations because CPU processing is slow
- Instead a specialized hardware (ASIC. not the CPU) is responsible for the switching logic
- The mac address table, is stored in a kind of memory called TCAM, Ternary Content Addressable Memory
- Another common name for MAC address table is called CAM table
- The asic Feeds the destination MAC address of the frame into the TCAM, which returns the matching MAC address table entry
- The frame is then forwarded out of the appropriate interface

- Modern routers also use a similar hardware data plane, an ASIC, designed for forwarding logic, and tables stored in TCAM
