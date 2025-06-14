# Virtualization, Cloud Models, and Containers

## Hypervisors

- A **hypervisor** is used to manage and allocate the hardware resources to each VM.
- Another name for a hypervisor is **VMM** (Virtual Machine Monitor).

### Type 1 Hypervisor (Bare-Metal / Native)

- Runs **directly on hardware**
- Examples: VMware ESXi, Microsoft Hyper-V (bare-metal install)

### Type 2 Hypervisor (Hosted)

- Runs **as a program on an operating system**
- The OS running directly on the hardware is called the **Host OS**
- The OS running in a VM is called the **Guest OS**
- Examples: VMware Workstation, VirtualBox

---

## Cloud Computing Models (NIST)

### Three Service Models

- **SaaS (Software as a Service)**: End-user applications delivered via the cloud  
  - Example: Microsoft Office 365  
- **PaaS (Platform as a Service)**: Developer platforms and environments  
  - Example: AWS Lambda, Google App Engine  
- **IaaS (Infrastructure as a Service)**: Virtualized computing resources  
  - Example: Amazon EC2, Google Compute Engine  

### Four Deployment Models

- **Private Cloud** – Used by a single organization
- **Public Cloud** – Open to the general public
- **Hybrid Cloud** – Mix of public and private
- **Community Cloud** – Shared by multiple organizations with common concerns

### Five Essential Characteristics of Cloud

1. On-demand self-service  
2. Broad network access  
3. Resource pooling  
4. Rapid elasticity  
5. Measured service  

---

## Key Definitions

- **VM (Virtual Machine)**: An emulation of a physical computer
- **VMM (Virtual Machine Monitor)**: Another name for a hypervisor
- **Cisco UCS**: Unified Computing System

---

## Containers

- **Containers** are software packages that contain an app and all dependencies needed to run it.
- **Containers** do **not** run their own OS — they share the host OS.
- A **container engine** runs on the host OS (e.g., Docker Engine).
- A **container orchestrator** automates deployment, scaling, and management of containers.

### Examples

- **Container Engines**: Docker Engine  
- **Orchestrators**: Docker Swarm, Kubernetes  

---

## Containers vs Virtual Machines

| Characteristic       | Container         | Virtual Machine |
|----------------------|-------------------|-----------------|
| Boot Time            | Faster            | Slower          |
| Isolation Level      | Lower             | Higher          |
| OS Overhead          | Shared OS         | Own OS per VM   |
| Disk Usage           | Less              | More            |
| CPU/RAM Usage        | Less              | More            |

---

## Q&A

- **Q: What does IaaS stand for?**  
  A: Infrastructure as a Service

- **Q: What does PaaS stand for?**  
  A: Platform as a Service

- **Q: What does SaaS stand for?**  
  A: Software as a Service

- **Q: What does VM stand for?**  
  A: Virtual Machine

- **Q: What does VMM stand for?**  
  A: Virtual Machine Monitor

- **Q: Which boots faster: a VM or a container?**  
  A: Container

- **Q: Which is more isolated: a VM or a container?**  
  A: VM (each runs its own OS)

- **Q: Which takes up more disk space: a VM or a container?**  
  A: VM

- **Q: Which uses more CPU/RAM: a VM or a container?**  
  A: VM
