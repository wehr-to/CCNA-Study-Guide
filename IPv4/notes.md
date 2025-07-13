# IPv4 Addressing and Interface Notes (CCNA)

---

## Address Types

| **Question**                                                | **Answer**            |
| ----------------------------------------------------------- | --------------------- |
| Host portion all 0s                                         | Network Address       |
| Host portion all 1s                                         | Broadcast Address     |
| What kind of address is used to test local device software? | Loopback Address      |
| IPv4 addresses beginning with 127                           | Loopback range        |
| Groups of 8 bits in an IP address                           | Octets                |
| What is class D reserved for?                               | Multicast Addresses   |
| What is class E reserved for?                               | Experimental Purposes |
| Length of IP address (bits)                                 | 32 Bits               |
| Length of IP address (bytes)                                | 4 Bytes               |
| Maximum value of a binary octet                             | 255                   |

---

## Loopback Range

| **Address**                  | **Purpose**                                 |
| ---------------------------- | ------------------------------------------- |
| 127.0.0.1 to 127.255.255.255 | Reserved for loopback (local host testing)  |
| 127.0.0.1                    | Most common — tests a device’s TCP/IP stack |

---

## IP Address Classes

| **Class** | **First Octet Range** | **Bit Pattern** | **Default Prefix** | **Hosts per Network** | **Networks** |
| --------- | --------------------- | --------------- | ------------------ | --------------------- | ------------ |
| A         | 0–127                 | 0xxxxxxx        | /8                 | 16,777,214            | 128          |
| B         | 128–191               | 10xxxxxx        | /16                | 65,534                | 16,384       |
| C         | 192–223               | 110xxxxx        | /24                | 254                   | 2,097,152    |
| D         | 224–239               | 1110xxxx        | Multicast          | N/A                   | N/A          |
| E         | 240–255               | 1111xxxx        | Experimental       | N/A                   | N/A          |

---

## CIDR and Subnet Masks

| **CIDR** | **Subnet Mask** | **Class Default** |
| -------- | --------------- | ----------------- |
| /8       | 255.0.0.0       | Class A           |
| /16      | 255.255.0.0     | Class B           |
| /24      | 255.255.255.0   | Class C           |

---

## Subnetting and Host Formula

**Formula to calculate max hosts:**
`(2^n) - 2`, where `n` is the number of host bits.

* Subtract 2 for:

  * All 0s → Network address
  * All 1s → Broadcast address

**Examples:**

* /24 = 8 host bits → (2^8)-2 = 254
* /16 = 16 host bits → (2^16)-2 = 65,534

---

## Interface Status and Protocol

| **Status**            | **Protocol** | **What It Means**                                                      |
| --------------------- | ------------ | ---------------------------------------------------------------------- |
| administratively down | down         | Interface is manually shut down via `shutdown` command                 |
| up                    | down         | Layer 1 is up, but Layer 2 has an issue (e.g., encapsulation mismatch) |
| down                  | down         | No physical connection (e.g., unplugged cable, disabled port)          |
| up                    | up           | Interface is functioning correctly                                     |

---

## Device Interface Defaults

| **Device Type** | **Default Interface State** | **Reason**                                                       |
| --------------- | --------------------------- | ---------------------------------------------------------------- |
| Routers         | administratively down (off) | Interfaces must be manually enabled and IP addressed             |
| Switches        | up (enabled by default)     | Switchports are active by default for plug-and-play connectivity |

---

## Useful Show Command Clarifications

* `show ip interface brief` →

  * **Status column**: reflects Layer 1 (physical link)
  * **Protocol column**: reflects Layer 2 (data link/encapsulation)

---
