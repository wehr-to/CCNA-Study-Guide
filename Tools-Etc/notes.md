# Infrastructure as Code (IaC)

## Definition
- **Q: What does IaC stand for?**  
  Infrastructure as Code

## Approaches
- A **procedural approach** defines explicit steps in a specific order to achieve the desired outcome.
- A **declarative approach** defines the desired end state, and lets the tool figure out the steps needed to achieve that state.

## Infrastructure as Code Tools
- Ansible
- Puppet
- Chef
- Terraform

## Mutable vs Immutable
- Configuration management tools typically use a(n) **mutable infrastructure** approach.
- Provisioning tools typically use a(n) **immutable infrastructure** approach.

# Terraform

## Overview
- Terraform is **primarily a provisioning tool**.
- Terraform uses a **declarative approach**.
- Terraform uses a **push model**.
- Terraform uses a(n) **immutable infrastructure** approach.
- Terraform uses an **agentless architecture**.

## Terraform Configuration
- Terraform configuration files **define the desired end state of the infrastructure**.
- Terraform configuration files are written in **Hashicorp Configuration Language (HCL)**.
- Terraform Core is written in **Go**.
- Terraform provisions infrastructure resources on platforms called **providers**.
- Terraform Core is the central software that analyzes configurations and interacts with providers.
- The **Terraform state file** tracks the status of the deployed infrastructure.

## Terraform Workflow
**Q: What the the three main steps in the basic Terraform workflow?**  
1. Write  
2. Plan  
3. Apply

# Ansible

## Overview
- Ansible is **primarily a configuration management tool**.
- Ansible uses a **procedural approach**.
- Ansible uses a(n) **mutable infrastructure** approach.
- Ansible is **agentless**.
- Ansible uses a **push model**.
- Ansible is written in **Python**.
- Ansible uses **SSH** to connect to devices.

## Configuration
- Ansible files are written in **YAML** (templates in **Jinja2**).
- Ansible **playbook files define the actions to be taken**.
- The Ansible server is called the **Control Node**.

# Chef

## Overview
- Chef is **primarily a configuration management tool**.
- Chef uses a **procedural approach**.
- Chef uses a(n) **mutable infrastructure** approach.
- Chef is **agent-based**.
- Chef is written in **Ruby**.
- Chef uses a **pull model**.
- Chef uses **HTTPS** to connect to devices.
- Chef uses **TCP port 10002** to send configurations to clients.

## Configuration
- Chef files are written in a **proprietary language** based on **Ruby**.
- Chef **recipe / run-list files define the actions to be taken**.

# Puppet

## Overview
- Puppet is **primarily a configuration management tool**.
- Puppet uses a **declarative approach**.
- Puppet uses a(n) **mutable infrastructure** approach.
- Puppet is **agent-based** (*with an external agent, the managed devices can be agentless).
- Puppet is written in **Ruby**.
- Puppet uses a **pull model**.
- Puppet uses **HTTPS** to connect to devices.
- Puppet clients use **TCP port 8140** to communicate with the server.

## Configuration
- Puppet **manifest files define the actions to be taken**.
- Puppet files are written in a **proprietary language** (known as **Puppet DSL**).
- A Puppet server is called a **puppet master**.
