| Purpose                                                                                     | Command Example                                      |
|---------------------------------------------------------------------------------------------|------------------------------------------------------|
| Configure the voice VLAN on an interface                                                    | `switchport voice vlan VLAN_NUMBER`                 |
| Power policing: Disable the interface and log if device draws too much power (default)      | `power inline police` **or** `power inline police action errdisable` |
| Power policing: Log the violation and restart the interface automatically                   | `power inline police action log`                    |
