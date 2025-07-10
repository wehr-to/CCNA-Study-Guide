# DNS Detailed CCNA Notes

## Overview

The **Domain Name System (DNS)** translates **human-readable domain names** (e.g., `www.cisco.com`) into **IP addresses** (e.g., `192.0.2.1` for IPv4, `2001:db8::1` for IPv6) so devices can communicate across networks. DNS operates as a **distributed, hierarchical system** ensuring scalable name resolution across the Internet and enterprise networks.

## Transport Protocols: UDP vs TCP

### UDP

* Standard DNS **queries and responses use UDP port 53**.
* UDP is chosen because it is **connectionless, low-overhead, and faster**.
* Originally limited to **512 bytes per DNS message** (RFC 1035).
* EDNS0 (RFC 6891) allows DNS to use larger UDP packets (up to 4096 bytes typically) while maintaining UDP for efficiency.

### TCP

* DNS uses **TCP port 53** when:

  * DNS responses exceed the UDP 512-byte limit (when `TC` truncation flag is set).
  * **Zone Transfers (AXFR and IXFR) occur between DNS servers**.
  * DNSSEC and large query/response operations require reliable transport.
* TCP ensures reliable delivery, ordered segments, and error checking, essential for zone transfers and large data sets.

## DNS Record Types

* **A Record (Address Record)**:

  * Maps **hostname to IPv4 address**.
  * Example: `www.example.com` -> `192.0.2.1`.

* **AAAA Record (IPv6 Address Record)**:

  * Maps **hostname to IPv6 address**.
  * Example: `www.example.com` -> `2001:db8::1`.

* **PTR Record (Pointer Record)**:

  * Used for **reverse DNS lookup (IP to hostname resolution)**.
  * For IPv4, uses `in-addr.arpa` domain.
  * For IPv6, uses `ip6.arpa` domain.

* **CNAME Record (Canonical Name Record)**:

  * Provides **aliasing of one domain to another**.
  * Example: `mail.example.com` can alias to `server1.example.com`.

* **NS Record (Name Server Record)**:

  * Indicates the **authoritative DNS servers for a domain**.

* **MX Record (Mail Exchange Record)**:

  * Specifies **mail servers responsible for receiving emails** for the domain.

* **SOA Record (Start of Authority Record)**:

  * Contains administrative information about the zone (e.g., primary nameserver, email of admin, serial number, timers).

* **TXT Record**:

  * Allows the storage of **human-readable text or key-value data** in DNS, commonly used for SPF, DKIM, DMARC.

## DNS Hierarchy and Operation

DNS uses a **hierarchical structure**:

* **Root Servers:** Top of the hierarchy, represented by `.`.
* **Top-Level Domains (TLDs):** e.g., `.com`, `.org`, `.net`, country codes like `.us`, `.uk`.
* **Second-Level Domains:** e.g., `example.com`.
* **Subdomains:** e.g., `www.example.com`, `mail.example.com`.

**DNS Resolver Flow:**

1. Client queries its configured DNS resolver (usually from DHCP).
2. If the resolver does not have the answer, it performs a **recursive query**, starting from the root, then TLD, then authoritative servers.
3. The resolver caches the response based on the **TTL (Time to Live)** in the record.

## DNS Server Address via DHCP

* **Clients automatically learn DNS server addresses through DHCP:**

  * **DHCPv4 Option 6** provides the DNS server IP addresses.
  * **DHCPv6 Option 23** provides DNS server IP addresses for IPv6 clients.
  * Alternatively, **Router Advertisements with RDNSS** can provide DNS information in IPv6 networks.

This allows clients to automatically and dynamically configure DNS without manual settings.

## DNS Caching

DNS resolvers and clients **cache responses** to reduce query time and unnecessary upstream traffic. The **TTL** value in DNS records determines how long a record can be cached.

Benefits of caching:

* Faster response to repeated queries.
* Reduced DNS query traffic.
* Improved user experience in networks.

## DNS Zone Transfers

Used for synchronizing DNS data between **primary and secondary DNS servers**.

* **AXFR (Full Zone Transfer):** Transfers the entire DNS zone.
* **IXFR (Incremental Zone Transfer):** Transfers only changes since the last update.
* Always uses **TCP for reliable delivery**.

## DNS Security Considerations

* DNS is susceptible to **spoofing and poisoning attacks**.
* **DNSSEC (Domain Name System Security Extensions):** Adds digital signatures to DNS data to ensure data integrity and authenticity.
* Uses additional DNS record types such as **RRSIG, DNSKEY, DS, NSEC**.
* DNSSEC can increase the size of DNS responses, often triggering the need for TCP fallback.


## Summary Table

| Aspect                  | Details                                                        |
| ----------------------- | -------------------------------------------------------------- |
| **Transport Protocols** | UDP (queries < 512 bytes), TCP (zone transfers, large queries) |
| **Port**                | 53                                                             |
| **Key Record Types**    | A, AAAA, PTR, CNAME, NS, MX, SOA, TXT                          |
| **Reverse DNS**         | Uses PTR records, `in-addr.arpa` (IPv4), `ip6.arpa` (IPv6)     |
| **Zone Transfers**      | AXFR (full), IXFR (incremental), always TCP                    |
| **Caching**             | TTL determines cache validity                                  |
| **Security**            | DNSSEC for data integrity/authenticity                         |
| **DNS via DHCP**        | Option 6 (IPv4), Option 23/RDNSS (IPv6)                        |


