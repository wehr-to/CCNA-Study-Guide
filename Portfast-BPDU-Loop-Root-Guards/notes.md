# STP Protection Features: PortFast, BPDU Guard, BPDU Filter, Root Guard, Loop Guard

---

## BPDU Guard & BPDU Filter

- **BPDU Guard** err-disables a switch port if it receives an STP BPDU.
- **BPDU Filter** prevents a switch port from sending BPDUs.
- Default **ErrDisable Recovery** interval: 300 seconds (5 minutes).

### Behavior Scenarios

| Scenario                                                                 | Result                                                                 |
|--------------------------------------------------------------------------|------------------------------------------------------------------------|
| BPDU Filter enabled (global config), port receives BPDU                  | PortFast & BPDU Filter disabled, port behaves as normal STP            |
| BPDU Filter enabled (interface config), port receives BPDU               | BPDU is ignored                                                        |
| PortFast-enabled port sends BPDUs?                                       | Yes                                                                    |
| BPDU Guard-enabled port receives BPDU                                    | Port is err-disabled                                                   |
| PortFast-enabled port receives BPDU                                      | Reverts to normal STP behavior                                         |
| BPDU Filter enabled by default (global config) is active on:             | All PortFast-enabled ports                                             |
| BPDU Guard enabled by default (global config) is active on:              | All PortFast-enabled ports                                             |
| Feature that can auto-reenable err-disabled ports                        | ErrDisable Recovery                                                    |

---

## PortFast

- A **PortFast**-enabled port immediately enters the **Forwarding** state upon link-up.
- Configuring PortFast globally enables it on **all access ports**.
- PortFast allows skipping **Listening** and **Learning** STP states.
- **Never enable PortFast** on switch-to-switch links.

---

## Root Guard

- If a **Root Guard**-enabled port receives a **superior BPDU**, it:
  - Enters the **Broken (Root Inconsistent)** state.
  - Is **automatically re-enabled** when superior BPDUs stop.
- **Root Guard disables** the port temporarily to maintain topology stability.

### Output Keywords

| Output                    | Meaning                         |
|---------------------------|----------------------------------|
| `BKN`                     | Broken (e.g., disabled by Root Guard) |
| `ROOT_Inc`                | Root Inconsistent               |

---

## Loop Guard

- Protects against loops caused by **unidirectional links**.
- Unidirectional links = **Layer 1 issue** where traffic flows only one way.
- **Mutually exclusive** with Root Guard (only one can be active per port).
- When a Loop Guard-enabled port misses BPDUs until **Max Age = 0**, it:
  - Enters **Broken (Loop Inconsistent)** state.
- Automatically recovers once **BPDUs are received again**.

### Loop Guard Scenarios

| Scenario                                                                 | Result                          |
|--------------------------------------------------------------------------|---------------------------------|
| Loop Guard recovery condition                                            | Starts receiving BPDUs again    |
| `spanning-tree loopguard default` (global config) affects:              | All switch ports                |
| Configured `spanning-tree guard loop`, then `spanning-tree guard root`  | **Root Guard** is active        |
| Configured `spanning-tree loopguard default` globally, then per-port Root Guard | **Root Guard** takes precedence |

