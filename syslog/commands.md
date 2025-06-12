# Syslog and Logging Commands

| Purpose                                                                 | Command                                                      |
|-------------------------------------------------------------------------|--------------------------------------------------------------|
| Configure synchronous logging on the device                             | `R1(config-line)# logging synchronous`                       |
| Configure Syslog monitoring to an external server                       | `R1(config)# logging ip-address` OR `logging host ip-address`|
| Configure Syslog monitoring to the buffer, specifying the size/level    | `R1(config)# logging buffered [size] level`                  |
| Configure Syslog monitoring to the console line, specifying the level   | `R1(config)# logging console level`                          |
| Configure Syslog monitoring to the VTY lines, specifying the level      | `R1(config)# logging monitor level`                          |
| Configure the level of Syslog messages sent to an external server       | `R1(config)# logging trap level`                             |
| Enable sequence numbers for Syslog messages                             | `R1(config)# service sequence-numbers`                       |
| Enable timestamps for Syslog log messages, displaying the date and time | `R1(config)# service timestamps log datetime`                |
| Display Syslog messages for the current Telnet/SSH session              | `R1# terminal monitor`                                       |

---

# Syslog Message Format

- `[...]`:timestamp: `%facility-severity-mnemonic:description`  
- `seq:[...]`: `%facility-severity-mnemonic:description`  
- `seq:timestamp:` `%[facility]-severity-mnemonic:description`  
- `seq:timestamp:` `%facility-[severity]-mnemonic:description`  
- `seq:timestamp:` `%facility-severity-[mnemonic]:description`  
- `seq:timestamp:` `%facility-severity-mnemonic:` **description**
