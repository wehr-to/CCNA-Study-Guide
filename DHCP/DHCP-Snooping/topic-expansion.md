## DHCP Snooping – Overview
- DHCP Snooping is a Layer 2 security feature that allows a switch to differentiate between trusted and untrusted DHCP messages, protecting the network from rogue DHCP servers and invalid IP allocation.

| Default Behavior                                        | Explanation                                                                   |
| ------------------------------------------------------- | ----------------------------------------------------------------------------- |
| All switch ports are **untrusted**                      | Must manually configure trusted ports (usually uplinks to legit DHCP servers) |
| DHCP messages from **untrusted ports**                  | Inspected and filtered — server replies are dropped                           |
| DHCP Snooping must be **enabled globally and per VLAN** | Only then does filtering begin                                                |

## Option 82 – Relay Agent Information Option
| Feature                     | Description                                                                               |
| --------------------------- | ----------------------------------------------------------------------------------------- |
| **Option 82**               | DHCP Relay Agent Information Option — adds metadata to DHCP messages                      |
| Used in                     | Campus networks or when DHCP relays are present                                           |
| Inserted By                 | Switches acting as relay agents (typically layer 2)                                       |
| Includes                    | Circuit ID (port info), Remote ID (device ID)                                             |
| Behavior on Untrusted Ports | By default, **switches discard DHCP messages with Option 82** received on untrusted ports |
| Disable Option 82 Insertion | `no ip dhcp snooping information option`                                                  |

- Security Note: Option 82 can help prevent man-in-the-middle DHCP attacks but may cause issues in networks with strict server checks unless properly configured.

## DHCP Snooping Trust Model
| Message Source      | Untrusted Port Behavior                              | Trusted Port Behavior |
| ------------------- | ---------------------------------------------------- | --------------------- |
| DHCP Server message | **Dropped immediately** (no validation)              | Allowed               |
| DHCP Client message | Inspected → forwarded or discarded based on bindings | Allowed               |

- Trusted Port = Uplink to known DHCP server
- Untrusted Port = Access ports (PCs, unknown clients)

## DHCP Snooping Binding Table
- Purpose: Tracks legitimate DHCP leases

Contents:
- MAC address
- IP address
- VLAN
- Interface
- Lease time
- Created when: A client receives a valid DHCP ACK from a server on a trusted port
- Command to view: show ip dhcp snooping binding

## DHCP Snooping + Rate Limiting
- Rate limiting protects against DHCP starvation or flood attacks.

| Feature                     | Behavior                                                        |
| --------------------------- | --------------------------------------------------------------- |
| Command                     | `ip dhcp snooping limit rate <pps>`                             |
| Action if limit is exceeded | Interface is **err-disabled** (shut down)                       |
| Recovery                    | Use `errdisable recovery cause dhcp-rate-limit` to auto-recover |

## DHCP Server vs Client Message Mapping
| Message      | Sent By | Description                                             |
| ------------ | ------- | ------------------------------------------------------- |
| **DISCOVER** | Client  | Used to find available DHCP servers                     |
| **OFFER**    | Server  | DHCP server offers an IP address                        |
| **REQUEST**  | Client  | Client requests offered IP or renews lease              |
| **ACK**      | Server  | Server confirms lease and provides IP                   |
| **NAK**      | Server  | Server denies lease request                             |
| **DECLINE**  | Client  | Client refuses offered IP (e.g., IP conflict)           |
| **RELEASE**  | Client  | Client gives up the leased IP before lease time expires |

## Q&A Review
| Question                                                                | Answer                                          |
| ----------------------------------------------------------------------- | ----------------------------------------------- |
| What happens if a DHCP server message is received on an untrusted port? | It is **dropped immediately**                   |
| What happens if a DHCP client message is received on an untrusted port? | It is **inspected and conditionally forwarded** |
| What does Option 82 do?                                                 | Adds relay agent info to DHCP messages          |
| What port behavior is default for Option 82 messages?                   | Dropped on untrusted ports                      |
| What happens when DHCP snooping rate limit is exceeded?                 | Interface is **err-disabled**                   |
| What command recovers from err-disable due to rate-limit?               | `errdisable recovery cause dhcp-rate-limit`     |
| What creates entries in the DHCP Snooping Binding Table?                | A successful **ACK** on a trusted port          |
| How do you view the DHCP Snooping Binding Table?                        | `show ip dhcp snooping binding`                 |







