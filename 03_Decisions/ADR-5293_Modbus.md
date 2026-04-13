
## Last updated

| Version | Date       | Author | Commit | Change description |
| ------- | ---------- | ------ | ------ | ------------------ |
| v1.0.0  | 2026-04-13 | Tycho  |        | Initial version    |

---

## Status
- Accepted

# Context
OEMers want to interact with the machine using PLC.

The system requires a standardized way for external controllers (PLCs) to:
- Read machine data (e.g. status, measurements)
- Write control parameters or commands

The solution must:
- Be widely supported in industrial environments
- Be simple to integrate with PLCs
- Require minimal custom implementation from OEMers
## Decision
Use **Modbus** as the communication protocol for external PLC interaction.

The system will:
- Act as a **Modbus Slave**
- Expose relevant data via registers (holding/input)
- Support:  Modbus TCP

---

## Alternatives

### OPC UA
- More modern and secure
- More complex to implement
- Less commonly supported on lower-end PLCs

### CAN Bus (custom protocol)
- Efficient and fast
- Requires custom protocol definition
- Not plug-and-play for OEM PLCs

### Proprietary protocol
- Fully customizable
- High integration effort for OEMers
- Poor interoperability

## Consequences

### Positive
- Widely supported by PLCs and industrial tools
- Low integration barrier for OEMers
- Simple and well-understood protocol
- Fast implementation

### Negative
- Limited data modeling
- Requires careful register mapping documentation

---

### Tags:
#adr/modbus
#communication