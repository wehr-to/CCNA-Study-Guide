| Term               | Definition                                                                                | Real-World Meaning                                                              |
| ------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Inside Local**   | IP address of the **inside host**, as seen **within the internal network**                | A private IP like `192.168.1.10` on a PC behind a router                        |
| **Inside Global**  | IP address of the **inside host**, as seen **by the external network (Internet)**         | A public IP (e.g., `203.0.113.5`) mapped to an internal host by NAT             |
| **Outside Local**  | IP address of the **external host**, as seen **from the inside network**                  | The internal router's perspective of a public site (usually the same as global) |
| **Outside Global** | IP address of the **external host**, as seen **on the actual outside network (Internet)** | The real public IP of a website or remote host (e.g., `142.250.72.14`)          |

## Analogy:
- Think of Inside Local → Inside Global as your router giving your laptop a fake passport so it can travel the world.
- Outside Global is the real destination (like Google’s public IP).
- Outside Local is how that address appears from inside your local network (often unchanged in basic NAT).

| Class | Private Address Range         | CIDR             | Notes                                    |
| ----- | ----------------------------- | ---------------- | ---------------------------------------- |
| A     | 10.0.0.0 – 10.255.255.255     | `10.0.0.0/8`     | Often used by enterprises or ISPs        |
| B     | 172.16.0.0 – 172.31.255.255   | `172.16.0.0/12`  | Used in mid-size internal networks       |
| C     | 192.168.0.0 – 192.168.255.255 | `192.168.0.0/16` | Common in home and small office networks |

- Note: These ranges are not routable on the Internet. NAT is required to translate them into public addresses.

## NAT Types & Behaviors
| NAT Type           | Behavior                                                               | Example Use Case                                    |
| ------------------ | ---------------------------------------------------------------------- | --------------------------------------------------- |
| **Static NAT**     | Manually maps a single private IP to a single public IP (1:1)          | Hosting an internal web server with fixed public IP |
| **Dynamic NAT**    | Maps private IPs to public IPs from a pool (1:1 but auto-assigned)     | Internal users temporarily needing internet access  |
| **PAT / Overload** | Maps multiple private IPs to one public IP using port numbers (many:1) | Most common method; home routers, small businesses  |

## NAT Translation Table Expectations
| Field          | Expected Values (Source NAT Only)                        |
| -------------- | -------------------------------------------------------- |
| Inside Local   | Internal host's IP (e.g., 192.168.1.10)                  |
| Inside Global  | Mapped public IP (e.g., 203.0.113.5)                     |
| Outside Local  | Destination IP as seen from inside (e.g., 142.250.72.14) |
| Outside Global | Same as Outside Local (for source NAT only)              |

