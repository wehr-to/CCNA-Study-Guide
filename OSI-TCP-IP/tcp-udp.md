# Protocol to Transport Layer Mapping (TCP vs UDP)

## TCP-Only Protocols

| Protocol      | Port(s)   | Description                              |
|---------------|-----------|------------------------------------------|
| HTTP          | 80        | Web browsing                             |
| HTTPS         | 443       | Secure web browsing                      |
| FTP           | 20, 21    | File Transfer Protocol                   |
| FTPS          | 990       | Secure FTP                               |
| SSH           | 22        | Secure shell                             |
| Telnet        | 23        | Remote terminal access                   |
| SMTP          | 25        | Simple Mail Transfer Protocol            |
| SMTPS         | 465       | Secure SMTP                              |
| IMAP          | 143       | Internet Message Access Protocol         |
| IMAPS         | 993       | Secure IMAP                              |
| POP3          | 110       | Post Office Protocol                     |
| POP3S         | 995       | Secure POP3                              |
| LDAP (TCP)    | 389       | Lightweight Directory Access Protocol    |
| LDAPS         | 636       | Secure LDAP                              |
| SMB/CIFS      | 445       | Windows file sharing                     |
| SQL Server    | 1433      | Microsoft SQL Server                     |
| RDP           | 3389      | Remote Desktop Protocol                  |
| BGP           | 179       | Border Gateway Protocol                  |
| IRC           | 6667      | Internet Relay Chat                      |
| NFS           | 2049      | Network File System                      |

## UDP-Only Protocols

| Protocol      | Port(s)   | Description                              |
|---------------|-----------|------------------------------------------|
| DNS (queries) | 53        | Domain Name System (typical queries)     |
| DHCP          | 67, 68    | Dynamic Host Configuration Protocol      |
| TFTP          | 69        | Trivial File Transfer Protocol           |
| SNMP          | 161, 162  | Simple Network Management Protocol       |
| RIP           | 520       | Routing Information Protocol             |
| Syslog        | 514       | System logging                           |
| NTP           | 123       | Network Time Protocol                    |
| BOOTP         | 67, 68    | Bootstrap Protocol                       |
| RTP           | Dynamic   | Real-Time Transport Protocol             |
| mDNS          | 5353      | Multicast DNS                            |
| LLMNR         | 5355      | Link-Local Multicast Name Resolution     |
| NetBIOS Name  | 137       | NetBIOS over UDP                         |
| NetBIOS Datagram | 138    | NetBIOS over UDP                         |
| SNMP-Trap     | 162       | SNMP notifications                       |

## Protocols Using Both TCP and UDP

| Protocol      | Port(s)   | Description                              |
|---------------|-----------|------------------------------------------|
| DNS           | 53        | TCP for zone transfers, UDP for queries  |
| LDAP          | 389       | Can operate over TCP or UDP              |
| SIP           | 5060      | Session Initiation Protocol              |
| SNMP          | 161       | Generally UDP, TCP possible              |
| QUIC          | 443       | UDP-based transport for HTTP/3           |
| Kerberos      | 88        | Authentication protocol                  |
| ISAKMP/IKE    | 500       | IPsec key exchange (typically UDP, TCP possible in NAT-T) |
| H.323         | Dynamic   | Multimedia/VoIP                          |

## Notes

- **TCP** is **connection-oriented**, reliable, and ensures ordered delivery.
- **UDP** is **connectionless**, faster, but doesn’t guarantee delivery.
- Some protocols (like **DNS**) use **UDP by default** but **TCP when needed** (e.g., zone transfers or large payloads).
