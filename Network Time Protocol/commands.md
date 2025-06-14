## NTP & Clock Configuration Commands

| Action | Command |
|--------|---------|
| Configure NTP symmetric active mode | `ntp peer ip-address` |
| Configure recurring daylight saving time | `clock summer-time name recurring start end [offset]` *(start/end = week, weekday, month, time)* |
| Configure the device to be an NTP server | `ntp master [stratum]` |
| Configure the hardware clock | `calendar set hh:mm:ss day month year` *(day/month order flexible)* |
| Configure the NTP server to sync to | `ntp server ip-address [prefer]` |
| Update the hardware clock using NTP | `ntp update-calendar` |
| Configure the software clock | `clock set hh:mm:ss day month year` *(day/month order flexible)* |
| Set the source interface for NTP messages | `ntp source interface` |
| Configure the timezone | `clock timezone name hours-offset [minutes-offset]` |
| Create an NTP authentication key | `ntp authentication-key key-number md5 key` |
| Enable NTP authentication | `ntp authenticate` |
| Specify a trusted NTP key | `ntp trusted-key key-number` |
| Specify NTP authentication key to use with server | `ntp server ip-address key key-number` |
| Display the hardware clock | `show calendar` |
| Display the software clock | `show clock` |
| Display software clock + time source | `show clock detail` |
| Show NTP status | `show ntp status` |
| Show configured NTP servers | `show ntp associations` |
| Show logs | `show logging` |
| Update hardware clock from software clock | `clock update-calendar` |
| Update software clock from hardware clock | `clock read-calendar` |
