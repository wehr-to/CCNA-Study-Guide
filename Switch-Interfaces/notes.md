## Interface Troubleshooting Reference

| **Symptom**                       | **Likely Problem**                  | **Check This**                          |
|----------------------------------|-------------------------------------|-----------------------------------------|
| High CRC or FCS errors           | Duplex mismatch, EMI, bad cable     | Interface stats, cabling, duplex        |
| Low throughput on working link   | Duplex mismatch                     | `show interfaces`                       |
| No link (down/down)              | Bad cable or powered-off device     | Cable, LEDs, device state               |
| Collisions / CSMA/CD messages    | Half duplex link                    | Replace hub, force full duplex          |
| Runts/Giants                     | MTU mismatch or hardware issue      | Interface counters, MTU config          |

## Default Interface States by Device Type

| **Device Type** | **Interface State by Default**                                      |
|------------------|---------------------------------------------------------------------|
| Router           | `administratively down/down` (requires `no shutdown`)              |
| Switch           | `up/up` if connected to another powered-on device                  |
|                  | `down/down` if not connected or device is off                      |

## Duplex Modes Comparison

| **Mode**       | **Can Send & Receive Simultaneously?** | **Used With**         | **Notes**                                  |
|----------------|-----------------------------------------|------------------------|---------------------------------------------|
| Half Duplex    |  No — one direction at a time         | Hubs or legacy links   | Uses CSMA/CD to manage collisions           |
| Full Duplex    |  Yes — both directions at once        | Switches               | No collisions can happen                    |
