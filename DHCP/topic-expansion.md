## What is DHCP?
- DHCP (Dynamic Host Configuration Protocol) is used to automatically assign IP addresses and other networking parameters (default gateway, DNS, domain name, etc.) to devices on a network.

## DHCP Message Flow: The DORA Process
| Step | Message  | Direction          | Transport Type                    | Description                                            |
| ---- | -------- | ------------------ | --------------------------------- | ------------------------------------------------------ |
| 1    | Discover | Client → Broadcast | **Broadcast (UDP/67)**            | Client is looking for any available DHCP server        |
| 2    | Offer    | Server → Client    | **Unicast or Broadcast (UDP/68)** | DHCP server offers an IP address                       |
| 3    | Request  | Client → Broadcast | **Broadcast (UDP/67)**            | Client requests the offered IP (also used for renewal) |
| 4    | ACK      | Server → Client    | **Unicast or Broadcast (UDP/68)** | Server confirms IP lease and settings                  |

## DHCP Message Behavior Summary
| Message      | Sent By | Direction        | Transport Type           | Notes                                                 |
| ------------ | ------- | ---------------- | ------------------------ | ----------------------------------------------------- |
| **Discover** | Client  | Client → Network | **Always Broadcast**     | Finds available DHCP servers                          |
| **Offer**    | Server  | Server → Client  | **Unicast or Broadcast** | Offers IP and config info                             |
| **Request**  | Client  | Client → Network | **Always Broadcast**     | Accepts one Offer; informs others                     |
| **ACK**      | Server  | Server → Client  | **Unicast or Broadcast** | Confirms IP assignment and configuration              |
| **Release**  | Client  | Client → Server  | **Unicast**              | Client gives up its IP address                        |
| **Decline**  | Client  | Client → Server  | **Unicast**              | Sent if client finds the offered IP is already in use |

## DHCP Relay Agent
- What It Does: Forwards broadcast DHCP messages from clients to a DHCP server on a different subnet using unicast.
- Command: ip helper-address DHCP_SERVER_IP
- Use Case: Allows central DHCP server to serve multiple subnets across routers.
- Relay uses unicast to forward DHCP broadcasts because routers do not forward broadcasts by default.

## Windows DHCP Interaction
| Command             | Action Taken                                                  |
| ------------------- | ------------------------------------------------------------- |
| `ipconfig /release` | Sends a **DHCP Release** message (unicast) to the DHCP server |
| `ipconfig /renew`   | Sends a new **DHCP Discover** to request a new IP             |

- Q&A Review
- Q: What does DHCP stand for?
- A: Dynamic Host Configuration Protocol

- Q: What are the 4 DORA messages for getting an IP address?
- A: Discover → Offer → Request → Ack

- Q: Which DORA messages are sent by the client?
- A: Discover, Request

- Q: Which DORA messages are sent by the server?
- A: Offer, Ack

- Q: Which DHCP messages are always broadcast?
- A: Discover, Request

- Q: Which DHCP messages are unicast or broadcast depending on context?
- A: Offer, Ack

- Q: Which DHCP message is unicast only and sent by the client to end the lease?
- A: Release


