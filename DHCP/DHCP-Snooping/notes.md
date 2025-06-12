- By default, Cisco switches will drop DHCP messages with Option 82 that are received on an untrusted port.
- DHCP Option 82 is also known as the DHCP Relay Agent InfoDAIrmation Option.
- When DHCP snooping is enabled, all interfaces are untrusted by default.

- Q: If DHCP snooping rate-limiting is configured and the rate is exceeded, what happens?
- The interface is err-disabled

- DHCP Server or DHCP Client message?
- ACK = Server
- DECLINE = Client
- DISCOVER = Client
- NAK = Server
- OFFER = Server
- RELEASE = Client
- REQUEST = Client

- DHCP snooping untrusted port:
- If a DHCP Server message is received, discard it with no further checks.
- If a DHCP client message is received, inspect the message to determine if it should be forwarded or discarded.

- DHCP Snooping: 
- When a client successfully leases an IP address from a server, create a new entry in the DHCP Snooping Binding Table
