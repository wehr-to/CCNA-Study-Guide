| **Class** | **CIDR Range**                                 | **# of IPs**     | **Typical Use**             |
|-----------|------------------------------------------------|------------------|-----------------------------|
| A         | 10.0.0.0/8                                     | 16.7 million     | Enterprises, ISPs           |
| B         | 172.16.0.0 – 172.31.255.255 (/12)              | 1 million        | Mid-size corps              |
| C         | 192.168.0.0 – 192.168.255.255 (/16)            | 65,536           | Home networks, SOHO         |

| **Class** | **First Octet Range** | **Notes**                  |
|-----------|------------------------|-----------------------------|
| A         | 0–127                  | Unicast                    |
| B         | 128–191                | Unicast                    |
| C         | 192–223                | Unicast                    |
| D         | 224–239                | Multicast                  |
| E         | 240–255                | Experimental / Reserved    |

| **Class** | **Binary Bit Pattern (First Octet)** |
|-----------|--------------------------------------|
| A         | 0xxxxxxx                             |
| B         | 10xxxxxx                             |
| C         | 110xxxxx                             |
| D         | 1110xxxx                             |
| E         | 1111xxxx                             |

| **Question**                                         | **Answer**         |
|------------------------------------------------------|--------------------|
| What is the netmask for a /8 prefix length?          | 255.0.0.0          |
| What is the netmask for a /16 prefix length?         | 255.255.0.0        |
| What is the netmask for a /24 prefix length?         | 255.255.255.0      |
| What is the prefix length of a class A IPv4 address? | /8                 |
| What is the prefix length of a class B IPv4 address? | /16                |
| What is the prefix length of a class C IPv4 address? | /24                |
