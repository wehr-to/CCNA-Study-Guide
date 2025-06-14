# Dynamic ARP Inspection (DAI) Notes

## Purpose
- DAI is designed to prevent **ARP spoofing/poisoning**, which is a classic **MITM (Man-in-the-Middle)** attack.
- It **checks incoming ARP packets** to ensure they match the known **IP–MAC bindings** learned via **DHCP snooping**.

## Trust Model
- **Only trusted interfaces** are allowed to send ARP replies **without being inspected**.
- **All ports are untrusted by default**, just like in DHCP snooping.

## Validation Process
- DAI checks the **sender MAC** and **sender IP** fields of ARP messages against:
  - The **DHCP snooping binding table**
  - Any configured **ARP ACLs**
- **DAI inspects ARP messages received on untrusted ports**.

## Rate Limiting
- DAI **rate limiting is enabled by default** on untrusted ports.
- The **default rate** is **15 packets per second**.

## Quiz
> **Q: Does DAI inspect messages received on trusted ports?**  
> **A:** No
