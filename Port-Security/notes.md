# Port Security Notes

## Port Security Configuration

- Port security can be enabled on an interface configured as:
  - `switchport mode access`
  - `switchport mode trunk`
- Port security **cannot** be enabled on an interface configured as:
  - `switchport mode dynamic auto`
  - `switchport mode dynamic desirable`
- A combination of **statically-configured** and **dynamically-learned** secure MAC addresses can exist on a switchport.

## Default Behavior

- The **default port security violation mode** is: `Shutdown`
- The **default port security aging type** is: `Absolute`
- **Port security secure static address aging** is **disabled** by default.
- The **default errdisable recovery timer** is `300 seconds (5 minutes)`
- **Errdisable recovery is disabled by default** for all causes.
- When an interface is shutdown by port security, its status in the output of `show interfaces status` will be `err-disabled`

## Violation Modes

### **Protect Mode**
- Syslog/SNMP messages **are not** generated.
- The interface **is not** disabled.
- The violation counter **is not** incremented.

### **Restrict Mode**
- Syslog/SNMP messages **are** generated.
- The interface **is not** disabled.
- The violation counter **is** incremented.

### **Shutdown Mode**
- Syslog/SNMP messages **are** generated.
- The interface **is** disabled.
- The violation counter **is** incremented.

## Q&A

**Q:** What is the default port security violation mode?  
**A:** Shutdown
