
## Last updated

| Version | Date       | Author | Commit |
|---------|------------|--------|--------|
| v1.0.0  | 2026-04-09 | Tycho  |        |

---

## Purpose
Explain how the proposal / decision system is supposed to work.
Also contain a list of ADRs.


## Content
The `Drafts/` subdirectory contains all proposals which are not yet (fully) implemented.
The other ADRs are implemented and the documentation should be correct.
The ADRs will be listed below, separated by their status:

### Drafts
- [[ADR-123_CalibrationProcedure]]

### Active
- [[ADR-5293_Modbus]]


---
# Alternative Structure
Asana could also be used to host the ADRs instead of this document containing links to different ADRs which are stored here.
This would mean that this directory contains subdirectories for larger systems and each subdirectory would contain a single or multiple files with a list of links to the ADRs on asana.

Example:
- Frontend/
	- `ADR-EmbeddedWizard.md`:
		1. Itemviews
		2. Enums
		3. etc.
- Backend/
	- `ADR-Testing.md`:
		1. Test framework
		2. Simulation setup
	- `ADR-OS.md`:
		1. OS choice
- Hardware/
	- `ADR-Communication.md`:
		1. TCP driver choice
		2. Bluetooth driver choice
		3. etc
	- `ADR-MCU.md`:
		1. Microcontroller choice

The features directory can be separated in a similar manner to organize it better.