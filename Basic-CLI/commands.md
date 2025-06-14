## Cisco IOS Basics – Command Reference Table

| **Action / Question**                                              | **Command / Value**                                 |
|-------------------------------------------------------------------|------------------------------------------------------|
| Configure an MD5-encrypted enable password                        | `enable secret password`                             |
| Configure an unencrypted password for privileged EXEC mode        | `enable password password`                           |
| Encrypt current and future passwords on the device                | `service password-encryption`                        |
| Enter global configuration mode                                   | `configure terminal`                                 |
| Enter privileged EXEC mode                                        | `enable`                                             |
| Return to privileged EXEC mode from config                        | `exit`                                               |
| View the available commands                                       | `?`                                                  |
| View the running configuration                                    | `show running-config`                                |
| View the startup configuration                                    | `show startup-config`                                |
| Use the keyword to remove a configured command                    | `no` (e.g., `no service password-encryption`)        |

---

## Default Cisco Console Port Settings

| **Setting**            | **Value**              |
|------------------------|------------------------|
| Data bits              | `8`                    |
| Flow control           | `None`                 |
| Parity                 | `None`                 |
| Speed (baud rate)      | `9600 Bits per second` |
| Stop bits              | `1`                    |

---

## Cisco IOS Mode Prompts

| **Mode**                   | **Prompt**   |
|----------------------------|--------------|
| User EXEC mode             | `Router>`    |
| Privileged EXEC mode       | `Router#`    |
| Global configuration mode  | `Router(config)#` |

---

## Miscellaneous

| **Description**                                     | **Value** |
|-----------------------------------------------------|-----------|
| `enable secret` uses type [...] encryption (MD5)    | `5`       |
****
