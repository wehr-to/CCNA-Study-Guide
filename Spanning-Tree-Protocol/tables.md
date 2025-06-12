| Interface Speed | 802.1D STP Cost |
|------------------|------------------|
| 10 Mbps          | 100              |
| 100 Mbps         | 19               |
| 1 Gbps           | 4                |
| 10 Gbps          | 2                |

| Role               | Meaning                                                                 |
|--------------------|-------------------------------------------------------------------------|
| Root Bridge        | The central switch in the STP topology. All paths are calculated in relation to it. |
| Root Port          | Each non-root switch chooses one port that leads most directly to the root bridge. |
| Designated Port    | One forwarding port per collision domain (segment).                     |
| Non-Designated Port| Any other port not forwarding — goes into blocking state.               |

| Field               | Length   | Notes                                      |
|---------------------|----------|--------------------------------------------|
| Bridge Priority     | 4 bits   | Default = 32768, increments of 4096        |
| Extended System ID  | 12 bits  | Used to encode VLAN ID (in PVST+)          |
| MAC Address         | 48 bits  | Used as tiebreaker                         |

| Setting              | Default Value                                  |
|----------------------|------------------------------------------------|
| Bridge Priority       | 32768                                          |
| Root Cost (10 Mbps link) | 100                                      |
| STP Protocol          | PVST+ on Cisco switches                       |
| STP Timers (802.1D)   | Hello: 2s, Max Age: 20s, FWD Delay: 15s       |
| Port State on Boot    | Listening → Learning → Forwarding             |

| State      | MAC Learning | Sends/Receives BPDUs | Forwards Traffic |
|------------|--------------|----------------------|------------------|
| Blocking   | No           | Yes (receive only)   | No               |
| Listening  | No           | Yes                  | No               |
| Learning   | Yes          | Yes                  | No               |
| Forwarding | Yes          | Yes                  | Yes              |
| Disabled   | No           | No                   | No               |

| Variant       | Description                          |
|---------------|--------------------------------------|
| 802.1D        | Classic STP                          |
| PVST+         | Cisco Per-VLAN STP                   |
| Rapid PVST+   | Faster convergence (based on 802.1w) |

| Feature     | Use Case                                 | Action                                               |
|-------------|-------------------------------------------|------------------------------------------------------|
| PortFast    | On host-facing ports (access)             | Bypasses Listening/Learning, goes directly to forwarding |
| BPDU Guard  | Protects PortFast ports from receiving BPDUs | Shuts port down if BPDU received                    |
| Root Guard  | Prevents undesired root bridge elections  | Blocks port if superior BPDU received               |
| Loop Guard  | Prevents ports from errantly going into forwarding | Keeps blocking state if BPDUs stop unexpectedly     |



