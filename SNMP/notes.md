# SNMP 

## SNMP Ports

| Component        | Protocol | Port |
|------------------|----------|------|
| SNMP Agent       | UDP      | 161  |
| SNMP Manager     | UDP      | 162  |

## SNMP Structure and Components

- Each variable in the SNMP MIB is identified with an OID  
- The Management Information Base (MIB) is the structure that contains the variables that are managed by SNMP  
- The SNMP Agent is software on the managed devices  
- The SNMP Manager is software on the NMS  

## SNMP Device Types

**Q: What are the two types of devices in SNMP?**  
- 1: Managed Devices  
- 2: Network Management Station (NMS)  

## SNMP Terminology

| Abbreviation | Stands For                         |
|--------------|------------------------------------|
| MIB          | Management Information Base        |
| NMS          | Network Management Station         |
| OID          | Object ID                          |
| SNMP         | Simple Network Management Protocol |

## SNMP Versions

**Q: What is the most commonly used version of SNMPv2?**  
- SNMPv2c

**Q: Which version of SNMP is most secure?**  
- SNMPv3
  
## SNMP Message Types

| Question                                                                                       | Answer      |
|------------------------------------------------------------------------------------------------|-------------|
| Which SNMP message is a more efficient version of the GetNext message?                        | GetBulk     |
| Which SNMP message is a request sent from the manager to the agent to change values?          | Set         |
| Which SNMP message is a request sent from the manager to discover variables in the MIB?       | GetNext     |
| (also GetBulk, which is a more efficient version)                                             |             |
| Which SNMP message is a request to retrieve the value of a variable (OID), or multiple?       | Get         |
| Which SNMP message is an acknowledged notification from agent to manager?                     | Inform      |
| Which SNMP message is an unacknowledged notification from agent to manager?                   | Trap        |
## SNMP Message Classes

### Notification Message Class
- Trap  
- Inform  

### Read Message Class
- Get  
- GetNext  
- GetBulk  

### Response Message Class
- Response  

### Write Message Class
- Set  
