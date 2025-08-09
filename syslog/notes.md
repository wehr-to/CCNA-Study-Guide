# Syslog Notes

- Syslog servers listen for messages on **UDP port 514**.

## Default Syslog Destinations

**Q: Which locations are Syslog messages sent to by default?**  
1. Console Line  
2. Buffer  

## Syslog Message Fields

| Field         | Description                                                  |
|---------------|--------------------------------------------------------------|
| seq           | A number that indicates the order of messages                |
| mnemonic      | A short code for the message, indicating what happened       |
| description   | Detailed information about the event being reported          |
| severity      | Indicates how serious the logged event is                    |
| time stamp    | Indicates the time the message was generated                 |
| facility      | Indicates which process on the device generated the message  |

## Syslog Severity Levels

| Level | Name             |
|-------|------------------|
| 0     | Emergency         |
| 1     | Alert             |
| 2     | Critical          |
| 3     | Error             |
| 4     | Warning           |
| 5     | Notice/Notification |
| 6     | Informational     |
| 7     | Debugging         |

- Game of thrones acronym to remember this: Every Arya Cuts Every Wound, Never Ignoring Death
