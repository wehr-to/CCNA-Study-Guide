# Network Planes and SDN

- Functions that are used to manage devices are part of the management plane.
- Functions that control the actions of the data plane are part of the control plane.
- SDN is an approach to networking that centralizes the Control plane into an application called a controller.
- Tasks involved in forwarding user traffic from one interface to another are part of the data plane.
- The Northbound interface is used for communications between the SDN controller and applications.
- The Southbound interface is used for communications between the SDN controller and the network devices it controls.
- The Data plane is also known as the Forwarding plane.
- The MAC address table is also known as the CAM table.

## What are the three logical planes of network functions?

- Management plane
- Control plane
- Data plane

## Southbound Interfaces

- NETCONF is a southbound interface.
- onePK is a southbound interface.
- OpenFlow is a southbound interface.
- OpFlex is a southbound interface.

## Northbound Interfaces

- REST APIs are used for Northbound interfaces.

## Acronyms

**Q: What does API stand for?**  
Application Programming Interface

**Q: What does ASIC stand for?**  
Application-Specific Integrated Circuit

**Q: What does NBI stand for?**  
Northbound Interface

**Q: What does REST stand for?**  
Representational State Transfer

**Q: What does SBI stand for?**  
Southbound Interface

**Q: What does SDA stand for?**  
Software-Defined Architecture

**Q: What does SDN stand for?**  
Software-Defined Networking

**Q: What does TCAM stand for?**  
Ternary Content-Addressable Memory

# AI and Machine Learning

- Predictive AI analyzes historical data to predict future outcomes or trends.
- Generative AI learns patterns from existing data to create new content.
- ML is a subset of AI that enables computers to learn from data and improve without explicit programming.
- AI uses computers to simulate intelligence, allowing them to exhibit behaviors typically associated with humans.

## Catalyst Center AI Features

- Catalyst Center AI Endpoint Analytics uses AI to automatically identify and classify devices connected to the network.
- Catalyst Center AI Network Analytics uses AI to establish the baseline behavior of the network and provide recommendations for optimizing the network.
- Catalyst Center AI-enhanced Radio Resource Management (RRM) uses AI to optimize wireless network performance by dynamically adjusting radio settings.
- Catalyst Center Machine Reasoning Engine (MRE) uses AI to perform root-cause analysis and take corrective actions when network issues arise.

## Machine Learning Types

- ML: Reinforcement learning trains the model by rewarding or penalizing its actions in a given environment.
- ML: Supervised learning trains the model on a labeled dataset.
- ML: Unsupervised learning trains the model on an unlabeled dataset.
- ML: Deep learning uses artificial neural networks to process and learn from large and complex datasets.

## Additional Acronyms

**Q: What does AI stand for?**  
Artificial Intelligence

**Q: What does Catalyst Center MRE stand for?**  
Machine Reasoning Engine

**Q: What does ML stand for?**  
Machine Learning

**Q: What does RRM stand for?**  
Radio Resource Management

## HTTP Methods
```
GET - Retrieves data from object / Read
PUT - Adds information to an object / Update
POST - Creates an object / Create
DELETE - Removes an object / Delete
PATCH - Applies partial modifications to an object / Update
```

# Cisco Management Solutions Overview

| **Solution**                    | **Type**                    | **Description**                                                                                      | **Key Use Cases**                                                              |
| ------------------------------- | --------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Cisco IOS 15                    | Network OS (CLI-based)      | The traditional operating system for Cisco routers and switches; CLI-driven configuration model.     | Device-level configuration, routing, switching, CLI management.                |
| Cisco DNA Center                | Centralized controller      | Intent-based network management platform with automation, assurance, and analytics.                  | SD-Access, policy automation, AI-driven insights, software-defined networking, SDA |
| Cisco Network Assistant         | GUI-based desktop tool      | Lightweight management tool for small to medium-sized LANs; uses GUI to configure Cisco devices.     | VLANs, port status, topology maps, configuration backup for SMB.               |
| Cisco Prime Infrastructure (PI) | Network management platform | Legacy NMS for managing wired/wireless devices; integrates monitoring, configuration, and inventory. | Lifecycle management, wireless control, reports, device tracking.              |


