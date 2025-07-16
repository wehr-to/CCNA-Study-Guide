## Ethernet, Duplex, and Interface Behavior

### Ethernet and Duplex Facts

- All devices connected to an Ethernet **hub** are in the same **collision domain**.
- Devices attached to a **switch** can operate in **full duplex** mode.
- Devices attached to an Ethernet **hub** must operate in **half duplex** mode.
- Ethernet devices use **CSMA/CD** to detect and prevent collisions on **half-duplex** interfaces.
- Ethernet hubs operate at **Layer 1** of the OSI model.
- In **full duplex** mode, an interface **can** send and receive data **simultaneously**.
- In **half duplex** mode, an interface **cannot** send and receive data simultaneously.
- In the output of `show ip interface brief`:
  - **Router interfaces** will be in the **administratively down/down** state by default.
  - **Switch interfaces** will be in the **up/up** state by default if connected to another device.
  - **Switch interfaces** will be in the **down/down** state by default if not connected.

---

### Common Questions

| **Question**                                                                 | **Answer**                                 |
|------------------------------------------------------------------------------|---------------------------------------------|
| Are all devices connected to an Ethernet switch in the same collision domain? | No                                          |
| What does CSMA/CD stand for?                                                 | Carrier Sense Multiple Access with Collision Detection |
| What is the default duplex setting of an interface?                          | Auto                                        |
| What is the default speed setting of an interface?                           | Auto                                        |

---

###  `show interfaces` Error Counters

| **Counter**      | **Description**                                                                 |
|------------------|----------------------------------------------------------------------------------|
| **Giants**       | Counts frames that are **larger** than the maximum frame size (1518 bytes)      |
| **Runts**        | Counts frames that are **smaller** than the minimum frame size (64 bytes)       |
| **CRC**          | Counts frames that **failed their error check** in the Ethernet FCS trailer     |
| **Frame**        | Counts frames that have an **incorrect/illegal format**                         |
| **Output errors**| Frames the switch tried to **send**, but failed due to an error                 |
| **Input errors** | **Total** of various counters of errors **received** by the device              |

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
| Half Duplex    |  No, one direction at a time         | Hubs or legacy links   | Uses CSMA/CD to manage collisions           |
| Full Duplex    |  Yes, both directions at once        | Switches               | No collisions can happen                    |
