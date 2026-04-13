
## Last updated
| Version | Date       | Author | Commit | Change description |
| ------- | ---------- | ------ | ------ | ------------------ |
| v1.0.0  | 2026-04-13 | Tycho  |        | Initial version    |

## Asana DVBID-123
Example, has no link

---

## Status
- Proposed

## Context

The Gravimix relies on a loadcell to accurately measure material weight during batching and mixing operations. Accurate weight measurement is critical for maintaining product quality and consistency.
Currently, there is no standardized calibration strategy for the loadcell. Calibration is either done manually through low-level firmware adjustments or not performed consistently across machines.

This leads to:
- Inconsistent measurement accuracy between machines
- Increased maintenance effort
- Difficulty in field servicing and recalibration
- Lack of traceability for calibration changes

A robust and user-accessible calibration mechanism is required.

## Decision
Implement a guided, software-driven loadcell calibration feature accessible via the touchscreen UI, with the following characteristics:

- **Two-point calibration method**:
    - Zero calibration (no load)
    - Span calibration (known reference weight)
- **User workflow on touchscreen**:
    1. Prompt user to remove all load; to capture zero offset
    2. Prompt user to place a known calibration weight; to capture span
    3. Validate input and compute calibration coefficients
    4. Display success/failure feedback
- **Data storage**:
    - Calibration parameters stored in non-volatile memory (internal flash or external storage)
    - Optional export/import via USB/SD card for backup and transfer
- **Traceability**:
    - Store timestamp and calibration metadata
    - Optional logging accessible via Ethernet interface
- **Safety and validation**:
    - Reject unrealistic calibration values
    - Require confirmation before overwriting existing calibration

## Alternatives

1. **Factory-only calibration (no user access)**
    - Pros: Controlled environment, potentially higher accuracy
    - Cons: Not scalable, requires service intervention for recalibration, impractical for field conditions
2. **Single-point calibration (offset only)**
    - Pros: Simpler implementation
    - Cons: Does not correct gain errors, insufficient for accurate weight measurement across full range
3. **Automatic continuous calibration**
    - Pros: Minimal user involvement
    - Cons: Complex to implement, unreliable without controlled reference weights, risk of drift and incorrect calibration
4. **Manual calibration via firmware configuration (no UI)**
    - Pros: Minimal UI effort
    - Cons: Error-prone, inaccessible to non-technical users, poor UX, no traceability

The selected two-point guided calibration provides the best balance between accuracy, usability, and implementation complexity.

## Consequences

**Positive:**
- Improved measurement accuracy and consistency across machines
- Reduced need for specialized service personnel
- Better user experience through guided touchscreen workflow
- Calibration data becomes traceable and portable
- Easier diagnostics and remote support via Ethernet

**Negative:**
- Increased firmware complexity (UI flow, validation, storage handling)
- Requires careful UX design to avoid user errors
- Additional testing needed to ensure robustness across edge cases
- Slight increase in development time and maintenance overhead

---

### Tags:
#feature/calibration
#DVBID-123
