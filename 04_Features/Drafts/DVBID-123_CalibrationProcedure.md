
## Last updated
| Version | Date       | Author | Commit | Change Description |
| ------- | ---------- | ------ | ------ | ------------------ |
| v1.0.0  | 2026-04-09 | Tycho  |        | Initial version    |

## Asana DVBID-X
Place link to tasks here, change X in title to proper ID, also change tag ID

---

## Purpose

This document describes the load cell calibration feature for the plastic mixer machine. It provides implementation details, user interaction flow, and system behavior to ensure consistent and accurate weight measurements across all deployed machines.

## Scope

**Covers:**
- Load cell calibration workflow via touchscreen UI
- Calibration algorithm (two-point calibration)
- Data storage and persistence
- User interaction

**Does NOT cover:**
- Hardware design of the loadcell or amplifier circuitry
- Low-level ADC driver implementation
- Mechanical installation or positioning of the loadcell
- External calibration standards or certification procedures

## Content

### Overview
The calibration feature enables operators to calibrate the load cell directly on the machine using a guided interface. The system uses a **two-point calibration method** to determine both offset and gain.

This ensures accurate weight measurements across the full operating range of the mixer.

### Calibration Workflow

#### Step 1: Start Calibration

- User navigates to:  
    `Settings -> Loadcell -> Calibration`
- System displays instructions and safety warnings

#### Step 2: Zero Calibration
- User is prompted to ensure the scale is empty
- System samples ADC values over a short time window (e.g., 1–2 seconds)
- Average value is stored as **zero offset**

#### Step 3: Span Calibration
- User is prompted to place a known reference weight
- User inputs the weight value via touchscreen
- System samples ADC values and calculates **span factor (gain)**

#### Step 4: Validation
- System checks:
    - Minimum difference between zero and span readings
    - Reasonable gain range
- If validation fails, calibration is rejected with an error message

#### Step 5: Save Calibration
- User confirms calibration results
- Parameters are written to non-volatile memory
- Confirmation message is displayed

### Calibration Algorithm

The calibration uses a linear model:
- Measured weight = (ADC_value - offset) × scale_factor

Where:
- **offset** = ADC value at zero load
- **scale_factor** = calculated using known reference weight

Computation:
- offset = ADC_zero
- scale_factor = (KnownWeight) / (ADC_span - ADC_zero)

### Data Storage

Calibration data is stored persistently:

**Stored parameters:**

- Offset value
- Scale factor
- Calibration timestamp
- Optional: user ID or machine ID

**Storage location:**

- Internal flash (primary)
- Optional backup/export via USB or SD card

**Data integrity:**

- Use checksum or CRC validation
- Fallback to last known valid calibration if corruption detected

### User Interface Considerations

- Clear step-by-step instructions
- Visual indicators (progress, success, failure)
- Numeric input validation for reference weight
- Confirmation dialog before overwriting existing calibration

**Error messages should be actionable**, e.g.:
- "Second weight less than first"
- "First and second weights are too similar"

---

### Tags:

#feature/calibration  
#DVBID-123