## SSH and IOS Image Types
- 1. NPE (No Payload Encryption) IOS Images
- Definition: NPE = No Payload Encryption. These IOS images do not include cryptographic modules.

- Effect: Devices running NPE images cannot support SSH, IPSec VPNs, or other security services requiring encryption.
- Use Case: Often used in countries or regions with restrictions on cryptographic exports.
- Exam Trap: If you try to enable SSH on a router running an NPE image, the command crypto key generate rsa will not be available.

## 2. K9 IOS Images
- Definition: K9 = Crypto-enabled. These images do support cryptographic features including:
- SSH
- SSL
- IPSec
- SNMPv3 encryption

- Filename Tip: The image name will contain k9, like:
- c1900-universalk9-mz.SPA.155-3.M4.bin
- Use Case: Required for secure remote management and most enterprise-grade deployments.
- Interview Tip: K9 images are mandatory in production environments that require encrypted management protocols like SSH or SNMPv3.

## SSH Protocol Versions
3. Version 1.99
- Definition: If a Cisco device displays SSH version 1.99, it means it supports both SSHv1 and SSHv2.
- Behavior: The router is in a transitional state. By default, it will use SSHv1 if that's what the client initiates.
- Best Practice: Always explicitly configure the router to use only SSHv2:
ip ssh version 2

## TCP Port Usage
4. SSH: TCP Port 22
- Protocol: Secure Shell (SSH)
- Port: TCP 22
- Purpose: Provides encrypted terminal access to Cisco devices.
- Default Behavior: Once crypto key generate rsa is issued and SSH is enabled, the router will automatically start listening on port 22.
- Security Reminder: Always disable Telnet and use SSH in production environments. Telnet sends credentials in cleartext.

## 5. Telnet: TCP Port 23
- Protocol: Telnet
- Port: TCP 23
- Purpose: Provides terminal access but is unencrypted.
- Risk: Credentials and data are exposed on the wire.
- Exam/Real-World Reminder: Telnet is enabled by default on many older Cisco devices — it's critical to manually disable it:
line vty 0 15
transport input ssh

- Example: Verifying SSH Support
After enabling SSH: 'show ip ssh'
- Sample output:
'SSH Enabled - version 2.0
Authentication timeout: 120 secs; Authentication retries: 3'

## Summary Table
| Feature                    | Description                                                   |
|----------------------------|---------------------------------------------------------------|
| NPE IOS Image              | No encryption support (SSH/IPSec/SSL unavailable)             |
| K9 IOS Image               | Supports cryptographic features like SSH, IPSec               |
| SSH Version 1.99           | Indicates support for both SSHv1 and SSHv2                    |
| SSH Default Port           | TCP 22                                                        |
| Telnet Default Port        | TCP 23                                                        |
| Command to set SSHv2 only  | `ip ssh version 2`                                            |
| Command to generate RSA    | `crypto key generate rsa`                                     |
| Command to disable Telnet  | `transport input ssh` under VTY lines                         |



