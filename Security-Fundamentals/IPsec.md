# IPsec – Security Fundamentals

## Overview

IPsec (Internet Protocol Security) is a suite of protocols that secures IP communications by authenticating and encrypting each IP packet in a data stream. It operates at Layer 3 of the OSI model and can protect traffic between:

- Host-to-host
- Gateway-to-gateway
- Host-to-gateway

IPsec provides:
- Authentication
- Integrity
- Confidentiality
- Anti-replay protection

## Key Protocols and Components

| Component | Description |
|----------|-------------|
| Authentication Header (AH) | Provides authentication and integrity, but does not encrypt the payload |
| Encapsulating Security Payload (ESP) | Provides confidentiality, authentication, and integrity |
| Security Association (SA) | A one-way logical connection that defines how traffic is secured |
| Internet Key Exchange (IKE/IKEv2) | Negotiates and establishes Security Associations between peers |

## IPsec Modes

| Mode       | What It Encrypts                           | Use Case                          |
|------------|---------------------------------------------|------------------------------------|
| Transport  | Encrypts only the payload of the IP packet | Used in host-to-host communication |
| Tunnel     | Encrypts the entire original IP packet and adds a new IP header | Commonly used for VPNs and site-to-site tunnels |

## IPsec Operation Phases

1. **IKE Phase 1**
   - Establishes a secure, authenticated channel between peers
   - Forms the ISAKMP SA
   - Uses Main Mode or Aggressive Mode

2. **IKE Phase 2 (Quick Mode)**
   - Negotiates the IPsec SAs
   - Defines the actual data protection parameters (ESP/AH, keys, lifetimes)

3. **Data Transfer**
   - Uses the established IPsec SAs
   - Protects traffic according to policies and transform sets

## Common Algorithms

| Type                | Examples                          |
|---------------------|-----------------------------------|
| Encryption          | AES, 3DES, DES                    |
| Integrity           | SHA-1, SHA-256, MD5               |
| Key Exchange        | Diffie-Hellman Groups 1–21        |
| Authentication      | Pre-shared keys, RSA signatures   |

## Basic IPsec Configuration Example (Cisco IOS)

```bash
crypto isakmp policy 10
 encryption aes
 hash sha256
 authentication pre-share
 group 14

crypto isakmp key MySecretKey address 1.2.3.4

crypto ipsec transform-set TS esp-aes esp-sha-hmac

crypto map CMAP 10 ipsec-isakmp
 set peer 1.2.3.4
 set transform-set TS
 match address 101

interface GigabitEthernet0/0
 crypto map CMAP
```

| Command                 | Purpose                         |
| ----------------------- | ------------------------------- |
| `show crypto isakmp sa` | Displays active IKE Phase 1 SAs |
| `show crypto ipsec sa`  | Displays IPsec Phase 2 SAs      |
| `debug crypto isakmp`   | Debugs IKE negotiations         |
| `debug crypto ipsec`    | Debugs IPsec data flow          |

| Term              | Definition                                                                                                            |
| ----------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Header**        | The portion of the packet that includes routing and control information (e.g., source/destination IP, protocol type). |
| **Payload**       | The actual **data** being carried by the packet — typically the **original IP packet or transport-layer data**.       |
| **Encapsulation** | IPsec can encapsulate the payload and even the original IP header, depending on the mode used.                        |

```
IPsec Modes:
1. Transport Mode
Header: Original IP header is kept.
Payload: Only the payload of the IP packet is encrypted (e.g., TCP/UDP and data).
ESP or AH is inserted after the IP header.

2. Tunnel Mode
Header: A new IP header is added.
Payload: The entire original IP packet (original header + data) becomes the payload and is fully encrypted.
```

