
## Last updated

| Version | Date       | Author | Commit | Change description |
|---------|------------|--------|--------|--------------------|
| v1.0.0  | 2026-04-09 | Tycho  |        | Initial version    |

## Asana DVBID-5293
[Modbus](https://app.asana.com/1/1205536482887515/project/1210423538377760/task/1212605284759718?focus=true)

---

## Purpose
Document the Modbus communication feature, including how it is architected

## Scope 
This document will dive into the deep end  on the modbus slave device implementation and how it handles requests and responses.

## Content

### Structure
![[ModbusDiagramClasses.svg]]

Above you can see the structure which the separate modbus classes use the talk to each other.

- The TCPEndpoint sends request to the modbusAPI, which uses the Parser to  parse the raw bytes into a structure. 
- Afterwards the ModbusAPI takes this struct and passes it to the Registermapping.
- This will perform the request, in case the data is valid, else return some error value
- This return value is parsed (in the Parser) to generate a response
- Finally the ModbusAPI sends the response back to the TCPEndpoint which will send it back over TCP.

### ModbusTCPEndpoint
This works similar to RemoteTCPEndpoint as it uses the same statemachine.
The part where this differs is with it's port. This should be customizable by the user using the touchscreen.

For this a parameter is used and then linked in `EWBridge` .


### Registermapping 
![[ModbusDiagramArchitecture]]

The structure to implement modbus uses both sections and subsections in order to easily deal with the requests. Each modbus request is assigned to a specific register range, which is coupled to a subsection.
This range is calculated by the amount of data that each call from the backend expects.
This way we can convert a modbus request to useful information and back to make a response.

---

### Tags:
#feature/modbus 