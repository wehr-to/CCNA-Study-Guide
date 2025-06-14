# Static Route Command Reference (Cisco IOS)

| Purpose                                   | Mode     | Command Syntax                                                                 |
|-------------------------------------------|----------|--------------------------------------------------------------------------------|
| Configure a static route and specify AD   | config   | `ip route <destination> <mask> <next-hop> <administrative-distance>`          |

### Example:
```bash
ip route 10.0.0.0 255.0.0.0 10.0.13.2 115
```
This sets a static route to `10.0.0.0/8` via `10.0.13.2` with an Administrative Distance of `115`.
