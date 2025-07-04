# SSH and Telnet Notes

## SSH vs. Telnet

- **NPE (No Payload Encryption)** IOS images do **not** support cryptographic features like SSH.
- **K9 IOS images** support **SSH**.
- Devices supporting both **SSHv1 and SSHv2** are labeled as **version 1.99**.
- **SSH servers** listen on **TCP port 22**.
- **Telnet servers** listen on **TCP port 23**.

## Q&A Quick Reference

### CLI Access
- **Q:** By default, is a password required to access the CLI via the console port?  
  **A:** No.

### Encryption
- **Q:** Does SSH encrypt traffic?  
  **A:** Yes.

- **Q:** Does Telnet encrypt data?  
  **A:** No.

### Terminology
- **Q:** What does FQDN stand for?  
  **A:** Fully Qualified Domain Name.

- **Q:** What does SSH stand for?  
  **A:** Secure Shell.

- **Q:** What does Telnet stand for?  
  **A:** Teletype Network.

### FQDN Components
- **Q:** What makes up the FQDN of a device?  
  **A:** `hostname.domainname`

### RSA Key Generation
- **Q:** When `crypto key generate rsa` is used, how are the keys named?  
  **A:** The FQDN is used as the name.

## Enable SSH on VTY line

- Step 1: Hostname
- Step 2: IP domain-name
- Step 3: Crypto key generate RSA
- Step 4: Transport input SSH
