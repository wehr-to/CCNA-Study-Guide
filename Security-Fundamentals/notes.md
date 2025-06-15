## Security Fundamentals Notes

### Authentication & Authorization

- **Digital Certificates** are a form of authentication often used to prove the identity of a website.
- **AAA:**
  - **Authentication** is the process of verifying a user's identity.
  - **Authorization** is the process of granting a user the appropriate access and permissions.
  - **Accounting** is the process of recording the user's activities on the system.
- **MFA (Multi-factor Authentication):** 
  1. Something you know
  2. Something you have
  3. Something you are

---

### Malware Types

| Malware Type      | Description                                                    |
|-------------------|----------------------------------------------------------------|
| **Virus**         | Infects other software (host program).                         |
| **Worm**          | Standalone malware that spreads on its own.                    |
| **Trojan Horse**  | Disguised as legitimate software.                              |
| **Malware**       | General term for harmful programs that infect systems.         |

---

### Social Engineering & Phishing

| Type              | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| **Phishing**       | Fraudulent emails that appear legitimate.                                   |
| **Spear Phishing** | Targeted phishing (e.g., aimed at employees of a specific company).         |
| **Whaling**        | Phishing aimed at high-profile individuals.                                 |
| **Vishing**        | Phishing over the phone.                                                    |
| **Smishing**       | Phishing via SMS text messages.                                             |
| **Social Engineering** | Psychological manipulation to reveal confidential information.          |
| **Tailgating**     | Following authorized users into restricted areas.                           |
| **Watering Hole**  | Compromising a site the target often visits.                                |
| **User Awareness Program** | Designed to make employees aware of threats.                        |
| **User Training Program** | Formal education on security policies.                               |

---

### Network & System Attacks

| Attack Type                 | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| **Reconnaissance**          | Gathering information about a target.                                      |
| **Man-in-the-Middle**       | Attacker intercepts communication between two devices.                     |
| **ARP Spoofing (Poisoning)**| Attacker sends fraudulent ARP replies.                                     |
| **Reflection Attack**       | Reflector sends traffic to target due to spoofed source.                   |
| **Amplification Attack**    | More dangerous form of reflection (larger payloads).                       |
| **TCP SYN Flood**           | Exploits TCP 3-way handshake to cause DoS.                                 |
| **DHCP Exhaustion**         | Flooding DHCP Discover messages to exhaust leases.                         |
| **Brute Force Attack**      | Tries every possible combination to guess a password.                      |
| **Dictionary Attack**       | Tries common words or phrases as passwords.                                |

---

### Concepts & Terms

- A **vulnerability** is a potential weakness in a system.
- A **threat** is the potential for a vulnerability to be exploited.
- A **mitigation technique** helps reduce risk from a threat.
- An **exploit** is a method used to take advantage of a vulnerability.
- **To spoof** an address means using a fake source (IP/MAC).
- **Physical Access Control** protects hardware by restricting access.

---

### Security Protocols & Ports

| Protocol       | Port(s)     | Notes                         |
|----------------|-------------|-------------------------------|
| **RADIUS**     | UDP 1812/1813 | Open standard AAA protocol    |
| **TACACS+**    | TCP 49       | Cisco proprietary AAA protocol|

- Cisco's AAA server is called **ISE** (Identity Services Engine)

---

### CIA Triad

| Principle       | Description                                       |
|----------------|---------------------------------------------------|
| **Confidentiality** | Only authorized users can access data         |
| **Integrity**       | Data should not be tampered with              |
| **Availability**    | Systems should remain accessible to authorized users |

---

### Definitions

- **DoS (Denial-of-Service)**: Overwhelms a system to make it unavailable.
- **DDoS (Distributed Denial-of-Service)**: DoS attack from multiple sources.
- **ISE**: Cisco Identity Services Engine.
