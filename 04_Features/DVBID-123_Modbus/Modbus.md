## Last updated

| Version | Date       | Author | Commit | Change description |
|---------|------------|--------|--------|--------------------|
| v1.0.0  | 2026-04-09 |        |        | Initial version    |

---

## Purpose
Document the Modbus communication feature, including how it is used within the system and its limitations.

## Scope
This document will cover:
- Supported Modbus types  : TCP only
- System role : slave
- Data model and register usage
- Communication flow
- Limitations and constraints

This document will NOT cover:
- Full Modbus protocol specification
- Low-level driver implementation details

## Content

### Overview
Modbus will be used by OEMers, as they prefer this way of interacting with machines.
The machine will only support Modbus over TCP, and will act as the slave

### Data Model

#### Implemented Register Types
- Holding Registers (Read/Write)
- Coils (Read/Write, boolean)

#### Addressing
- 1-based


Example for coils:

| Coil address | Coil name and Description | Read or Write | API Call           | Notes                                                                                                                                                                                                      | Section       | Sub section |
| ------------ | ------------------------- | ------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ----------- |
| 1            | Take or release control   | rw            | 0x07 \| 0x01, 0x02 | Write this coil to 1  in order to take control and perform further actions  <br>Write this coil to 0 in order to release control  <br>Read this coil to see if you are in control (1 if you are, 0 if not) | Control coils | Control     |

### Communication Flow

1. Enable OEM
2. Configure communication parameters: TCP Port
3. Receive and parse requests
4. Send out response
5. Update internal state

### Error Handling
- Timeout handling
- Retry mechanism (limited attempts)
- Invalid request handling
- Unsupported function code handling

### Limitations
- Quite limited in supported function codes

### Configuration
Configurable parameters:
- TCP Port

### Implementation
For a deeper dive into the feature implementation look at [[Implementation]]

---

## References
- [[ExampleADR-123_Modbus]]

---

### Tags:
#feature/modbus
#communication