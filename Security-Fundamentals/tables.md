## Cisco Password Types Table

| **Password Type** | **Command / Location**           | **Encryption Method**        | **Config Output Example**             | **Notes**                                        |
|-------------------|----------------------------------|------------------------------|----------------------------------------|--------------------------------------------------|
| Type 0            | `enable password`, line vty/console | Plaintext                   | `password 0 cisco`                      | Insecure — never use in production               |
| Type 7            | `service password-encryption`    | Reversible Vigenère cipher   | `password 7 0822455D0A16`              | Weak — can be decrypted                         |
| Type 5            | `enable secret`                  | MD5 Hash                     | `secret 5 $1$Abcd$WXYZ...`             | Much better — industry standard for a long time |
| Type 4            | Deprecated                       | SHA-256, bad salt impl.      | `secret 4 ...`                         | Not used anymore — flawed design                |
| Type 8            | `username X secret 8`            | PBKDF2 (SHA-256)             | `secret 8 $8$...`                      | Strong, modern standard                         |
| Type 9            | `username X secret 9`            | Scrypt (very strong)         | `secret 9 $9$...`                      | Strongest current encryption                    |
| None (default)    | Not set                          | —                            | No entry in config                     | Login not possible until password is set        |

## Cisco Password Feature Summary

| **Feature**               | **Password Type**           | **Notes**                                      |
|---------------------------|-----------------------------|------------------------------------------------|
| enable password           | Type 0 (plaintext)          | Deprecated                                     |
| enable secret             | Type 5 (MD5 hash)           | Preferred                                      |
| line vty / console passwords | Type 0 or 7 (if encryption enabled) | Use with `login` keyword             
| username X secret Y       | Type 8 or 9                 | Very strong; newer IOS versions                |

## AAA Authentication Command Reference

| **Command**                                        | **Use Case**                            | **Meaning**                               | **Where You Use It**              |
|----------------------------------------------------|------------------------------------------|--------------------------------------------|-----------------------------------|
| `aaa new-model`                                    | Required before AAA commands             | Enables AAA globally                        | Global config                     |
| `aaa authentication login default local`           | Standard config for local login          | Uses local user database by default         | Applies to all login lines unless overridden |
| `aaa authentication login default group radius local` | First try RADIUS, then fallback to local | Enterprise environments with fallback       | VTY / console                     |
| `aaa authentication login default enable`          | Uses enable password for login           | Not recommended (insecure)                  | For backward compatibility        |
| `aaa authentication login default none`            | No authentication at all                 | Dangerous — no login prompt                 | Lab/test only                     |
| `aaa authentication login CONSOLE_AUTH local`      | Custom method list for console           | Uses local user DB just for console         | Custom use per line               |
| `aaa authentication login VTY_AUTH group tacacs+ local` | Custom method list for vty lines      | Try TACACS+, fallback to local              | SSH/VTY access                    |

| Command | Description |
|--------|-------------|
| `aaa new-model` | Enables AAA on the device (must be entered first) |
| `aaa authentication login default local` | Uses local username database for login authentication |
| `aaa authentication login default group tacacs+ local` | Uses TACACS+ first, falls back to local |
| `aaa authentication login default group radius local` | Uses RADIUS first, then local authentication |
| `aaa authorization exec default local` | Authorizes user to enter exec mode using local database |
| `aaa authorization exec default group tacacs+ if-authenticated` | Uses TACACS+ for exec authorization |
| `aaa accounting exec default start-stop group tacacs+` | Enables exec session accounting via TACACS+ |
| `aaa accounting commands 15 default start-stop group tacacs+` | Accounts for privilege 15 commands |
| `username admin secret password123` | Creates a local user with encrypted password |
| `tacacs-server host <IP>` | Specifies TACACS+ server IP address |
| `tacacs-server key <KEY>` | Sets shared secret key for TACACS+ |
| `radius-server host <IP>` | Specifies RADIUS server IP address |
| `radius-server key <KEY>` | Sets shared secret key for RADIUS |
| `line vty 0 4`<br>` login authentication default` | Applies AAA authentication to VTY lines |
| `enable secret <PASSWORD>` | Sets local enable secret password |
| `show aaa` | Displays current AAA configuration |
| `debug aaa authentication` | Troubleshoots authentication process |
| `debug aaa authorization` | Troubleshoots authorization process |
| `debug aaa accounting` | Troubleshoots accounting process |

