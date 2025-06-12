# File Management and Boot Configuration Commands

| Description | Mode | Command |
|------------|------|---------|
| Configure the FTP password of the device | config | `ip ftp password password` |
| Configure the FTP username of the device | config | `ip ftp username username` |
| Copy a file from a TFTP server to the router's flash | exec | `copy tftp: flash:` |
| Copy a file from an FTP server to the router's flash | exec | `copy ftp: flash:` |
| Display the contents of flash memory | exec | `show flash` |
| Display the file systems of the device | exec | `show file systems` |
| Specify the OS file the device should use next time it boots | config | `boot system filepath` |
