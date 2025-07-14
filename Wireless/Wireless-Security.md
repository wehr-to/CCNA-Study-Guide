## Wireless security

### Boson/Exam Angles
- “Which device requires a certificate in PEAP?”
Authentication Server (only)
- “Which encryption uses RC4?”
WEP
- “Which WPA version uses Simultaneous Authentication of Equals (SAE)?”
WPA3
- “What’s the difference between CCMP and GCMP?”
Encryption and MIC mode
- Trick choice:
"WPA2 uses TKIP " ← only in WPA1 or transitional mode.

### General Facts
- A Group Key is used by a wireless AP to encrypt traffic that it wants to send to all of its clients.
- EAP is integrated with 802.1X, which provides port-based network access control.
- In EAP-FAST, a PAC (Protected Access Credential) is passed from the server to the client.
- In PEAP, the server is authenticated via a certificate.
- LEAP provides mutual authentication by exchanging challenge phrases.
- LEAP uses Dynamic WEP keys that change frequently.
- WEP keys can be 40 bits (+24 = 64) or 104 bits (+24 = 128) in length.
- WEP uses the RC4 algorithm for encryption.
- When using Open authentication, all authentication requests are accepted.
- WPA uses TKIP for encryption/MIC.
- WPA2 uses CCMP for encryption/MIC.
- WPA3 forward secrecy prevents data from being decrypted after it has been transmitted over the air.
- WPA3 SAE (Simultaneous Authentication of Equals) protects the four-way handshake when using personal mode authentication.
- WPA3 uses GCMP for encryption/MIC.

---

### 802.1X Roles
| Entity            | Description                                |
|-------------------|--------------------------------------------|
| Supplicant        | The device that wants to connect to the network |
| Authenticator     | The device that provides access to the network |
| Authentication Server (AS) | The device that receives client credentials and permits/denies access |

---

### EAP-FAST: 3 Phases
1. PAC is passed from server to client  
2. Secure TLS tunnel is established  
3. Client is authenticated via the TLS tunnel

---

### Questions & Answers

- **Q: In EAP-TLS, which device/devices require a certificate?**  
  A: AS and supplicant

- **Q: In PEAP, which device/devices require a certificate?**  
  A: AS Only

- **Q: What are the two WPA authentication modes?**  
  1: Personal  
  2: Enterprise
  
### Acronyms and Definitions

| Acronym  | Stands For                                                  |
|----------|-------------------------------------------------------------|
| CBC-MAC  | Cipher Block Chaining Message Authentication Code           |
| CCMP     | Counter/CBC-MAC Protocol                                    |
| EAP      | Extensible Authentication Protocol                          |
| EAP-FAST | EAP Flexible Authentication via Secure Tunneling            |
| EAP-TLS  | EAP Transport Layer Security                                |
| GCMP     | Galois/Counter Mode Protocol                                |
| GMAC     | Galois Message Authentication Code                          |
| LEAP     | Lightweight EAP                                             |
| MIC      | Message Integrity Check                                     |
| MS-CHAP  | Microsoft Challenge-Handshake Authentication Protocol       |
| PEAP     | Protected EAP                                               |
| PSK      | Pre-Shared Key                                              |
| TKIP     | Temporal Key Integrity Protocol                             |
| WEP      | Wired Equivalent Privacy                                    |


### Protocol Components

| Protocol | Encryption Method         | MIC Method     |
|----------|----------------------------|----------------|
| CCMP     | AES counter mode           | CBC-MAC        |
| GCMP     | AES Counter Mode           | GMAC           |

### Additional Questions

- **Q: Which encryption protocol was developed as an improvement upon WEP?**  
  A: TKIP

- **Q: Which WPA authentication mode uses 802.1X/EAP?**  
  A: Enterprise Mode

- **Q: Which WPA authentication mode uses a PSK?**  
  A: Personal Mode

| Mode             | Auth Mechanism           | Encryption | Secure       | Notes                        |
|------------------|---------------------------|------------|--------------|------------------------------|
| WEP              | Shared key                | RC4        | No           | Dead, cracked                |
| WPA              | TKIP + PSK                | TKIP       | Weak         | Deprecated                   |
| WPA2-Personal    | PSK (4-way handshake)     | AES        | Mostly       | Vulnerable to offline attack |
| WPA2-Enterprise  | RADIUS + EAP              | AES        | Yes          | Per-user auth                |
| WPA3-Personal    | SAE                       | AES/GCMP   | Yes          | Resists dictionary attacks   |
| WPA3-Enterprise  | RADIUS + EAP (192-bit)    | AES/GCMP   | Maximum      | Highest security             |

| Feature                | Default State          |
|------------------------|------------------------|
| WEP support            | Yes (still in old devices) |
| WPA3 forward secrecy   | Enabled                |
| Open auth (no password)| No encryption          |
| Group key rotation     | Optional (configurable)|
| MICs for WPA2/3        | Always on              |

| Role             | Function                                  |
|------------------|-------------------------------------------|
| Supplicant       | Client device (e.g., PC)                  |
| Authenticator    | Network device (e.g., switch, AP)         |
| Auth Server (AS) | Usually a RADIUS server (e.g., ISE, FreeRADIUS) |

| Type     | Server Cert | Client Cert | Notes                                          |
|----------|-------------|-------------|------------------------------------------------|
| EAP-TLS  | Yes         | Yes         | Most secure, mutual authentication             |
| PEAP     | Yes         | No          | Encrypted tunnel, client uses username/password|
| EAP-FAST | No (uses PAC)| No         | Cisco proprietary, lightweight secure tunnel   |
| LEAP     | No          | No          | Cisco legacy — uses dynamic WEP, weak          |

| Situation                         | Risk/Impact                          | Solution                                             |
|----------------------------------|--------------------------------------|------------------------------------------------------|
| Public Wi-Fi using Open Authentication | Anyone can connect, sniffing possible | Use WPA3-Open with encryption (OWE)                 |
| Old networks using WEP           | Vulnerable to aircrack-ng, IV replay | Upgrade to WPA2/WPA3                                |
| Clients fall for Evil Twin APs   | Spoofed SSID and BSSID               | Enable 802.11w + use certificate validation         |
| Inconsistent cert management (EAP-TLS) | Clients fail to authenticate   | Use EAP-FAST or PEAP with managed PKI               |

| Technology     | Dependency / Relationship                                      |
|----------------|---------------------------------------------------------------|
| 802.11w        | Adds mgmt frame protection to WPA2/WPA3                        |
| Radius/ISE     | Needed for EAP over 802.1X                                     |
| Group Policy / GPO | Used to push certs for EAP-TLS on Windows                 |
| FlexConnect    | Must be properly configured to support 802.1X                 |

| Issue                   | Log Output / Debug Hint                          |
|-------------------------|--------------------------------------------------|
| Cert missing (EAP-TLS)  | TLS Alert Fatal: Unknown CA                      |
| MFP failures (802.11w)  | Disassoc due to invalid frame                    |
| WPA3 SAE failure        | Unable to complete handshake                     |
| WEP MIC errors          | WEP MIC failure - possible replay attack         |

### Mnemonics 

| Term      | Mnemonic Meaning                                       |
|-----------|--------------------------------------------------------|
| TKIP      | Tinker Key Integrity Protocol (tinkered with WEP, still bad) |
| CCMP      | Counter CBC-MAC Protocol (AES-based, secure)           |
| GCMP      | Galois Counter Mode Protocol (WPA3-level secure)       |
| LEAP      | Legacy Encryption Always Problematic                   |
| PEAP      | "Password in Encrypted PEAPod"                         |
| EAP-FAST  | “Fast, No Certs”                                       |
