# NTP (Network Time Protocol) Notes

---

### Definitions & Facts

- **NTP** stands for **Network Time Protocol**
- NTP uses **UDP port 123**
- NTP uses only the **UTC time zone**
- A device can be an **NTP server and client** at the same time
- When an NTP server peers with another server at the same stratum level, this is called **Symmetric Active mode**
- **Reference clocks** are **stratum 0**
- **Stratum 1** = NTP servers directly connected to reference clocks (**Primary servers**)
- **Stratum 2+** = NTP servers getting time from other NTP servers (**Secondary servers**)
- **Lower stratum = preferred**
- Anything above **stratum 15 is considered unreliable**
- The default **stratum for `ntp master`** is **8**
- The **distance** of an NTP server from the reference clock is called its **stratum**

---

### Cisco-Specific Behavior

- The **default time zone** on Cisco devices is **UTC (Coordinated Universal Time)**
- The **default time source** for the software clock of a Cisco device is the **hardware calendar**
- If there is an asterisk `*` next to the time in the output of `show clock`, it means **the time is not authoritative**

---

### Quick Reference Q&A

**Q:** What does NTP stand for?  
**A:** Network Time Protocol

**Q:** What is the default time source for the software clock of a Cisco device?  
**A:** Hardware calendar

**Q:** What is the default time zone on Cisco devices?  
**A:** UTC (Coordinated Universal Time)

**Q:** What is the meaning of an asterisk `*` next to the time in `show clock`?  
**A:** The time is not authoritative

**Q:** What port does NTP use?  
**A:** UDP port 123

**Q:** What is the default stratum for `ntp master`?  
**A:** 8

# What Does `ntp master` Actually Do?

The `ntp master` command tells the router to act as an authoritative NTP server for other devices on the network.

If no external NTP server is configured, the router will use its own system clock as the time source.

The `ntp master` command sets the stratum level (default: 8, unless you specify otherwise with a command like `ntp master 4`).

Think of it like:
> “I’m not synced to anyone else, but I’ll pretend I am and let others sync to me.”

---

## NTP Stratum Levels

| Stratum | Meaning                                 |
|---------|------------------------------------------|
| 1       | Synced to atomic clock or GPS (best)     |
| 2–15    | Synced to another NTP device             |
| 16      | Unsynchronized (invalid)                 |
