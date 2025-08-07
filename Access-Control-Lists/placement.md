# ACL Placement Guide

## ACL Types and Placement Rules

| Type       | Filters On                                   | Recommended Placement        |
|------------|----------------------------------------------|------------------------------|
| Standard   | Source IP address only                       | Close to the destination     |
| Extended   | Source, destination, protocol, and ports     | Close to the source          |

## Standard ACL Placement

- Standard ACLs filter only on source IP.
- Lack of granularity can result in overblocking if placed too early.
- **Placement Rule:** Place as close to the destination as possible.

### Example:
To block Host A (192.168.1.100) from accessing Server B (10.0.0.5), apply the ACL on the inbound interface of Server B’s router.

## Extended ACL Placement

- Extended ACLs filter on source and destination IPs, protocols, and ports.
- Allow fine-grained control over traffic.
- **Placement Rule:** Place as close to the source as possible.

### Example:
To block Host A from sending HTTP traffic to Server B:
Apply the ACL on Host A’s outbound interface: access-list 100 deny tcp host 192.168.1.100 host 10.0.0.5 eq 80

## Interface Directions

| Direction | Description                        |
|-----------|------------------------------------|
| in        | Traffic coming into the interface  |
| out       | Traffic going out of the interface |

Apply ACLs in the appropriate direction based on the interface’s role in the packet flow.

## Performance Considerations

- Early ACL placement can block valid traffic or cause routing issues.
- Late ACL placement allows unnecessary traffic to consume resources.
- Extended ACLs placed early reduce network load and conserve bandwidth.

## Summary Table

| ACL Type   | Placement           | Rationale                   |
|------------|---------------------|-----------------------------|
| Standard   | Close to destination| Avoid overblocking          |
| Extended   | Close to source     | Block traffic early         |



