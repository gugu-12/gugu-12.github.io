# EPIC Dataset Data Dictionary

**Source:** iTrust, Singapore University of Technology and Design (SUTD)  
**Based on:** Scenario 1 — Normal operation, Oct 19 2018, 14:44:42–14:54:32  
**Note:** Only Generation.GIED1 and VSD1/2 are active in Scenario 1. All other subsystems read 0.

---

## 1. Timestamp

| Column | Type | Description |
|--------|------|-------------|
| Timestamp | String → datetime | Recording time, format MM/DD/YYYY HH:MM:SS, ~1 second intervals |

---

## 2. Generation — GIED1 (Generator 1, Active)

Measurements from the Intelligent Electronic Device (IED) monitoring Generator 1.

| Column | Unit | Range | Mean | Description |
|--------|------|-------|------|-------------|
| Apparent | VA | [643, 4977] | 3935 | Total power (√(Real²+Reactive²)) |
| Frequency | Hz | [49.96, 50.02] | 49.99 | Grid frequency, normal = 50Hz |
| L1_Current | A | [2.62, 9.07] | 6.73 | Phase 1 current |
| L2_Current | A | [0.00, 6.30] | 4.49 | Phase 2 current |
| L3_Current | A | [0.00, 6.75] | 4.80 | Phase 3 current |
| Power_Factor | — | [0.89, 0.98] | 0.96 | Efficiency ratio Real/Apparent, closer to 1 is better |
| Reactive | VAR | [-1374, -154] | -979 | Reactive power, negative = inductive load |
| Real | W | [584, 4825] | 3793 | Active power actually doing work |
| V1 | V | [244.39, 246.12] | 245.17 | Phase 1 voltage |
| V2 | V | [242.48, 244.19] | 243.35 | Phase 2 voltage |
| V3 | V | [244.32, 246.19] | 245.24 | Phase 3 voltage |
| VL1_L2 | V | [420.79, 423.74] | 422.08 | Line voltage between Phase 1 and 2 |
| VL2_L3 | V | [423.01, 426.08] | 424.67 | Line voltage between Phase 2 and 3 |
| VL3_VL1 | V | [422.70, 425.53] | 424.15 | Line voltage between Phase 3 and 1 |

---


---

## 3. Generation — Circuit Breakers (Q1, Q1A, Q1_1, Q1_2)

Boolean status columns for each circuit breaker in the generation subsystem.

| Column suffix | Type | Description |
|--------------|------|-------------|
| MODE_CLOSE | Boolean | Command to close the breaker |
| MODE_OPEN | Boolean | Command to open the breaker |
| MODE_STATUS | Boolean | Current mode status |
| STATUS | String | Encoded status [01]=open, [10]=closed |
| STATUS_CLOSE | Boolean | Confirmed closed state |
| STATUS_OPEN | Boolean | Confirmed open state |
| TRIP | Boolean | Breaker tripped (fault condition) |
| MODE_SYNC | Boolean | Synchronization mode active (Q1A only) |
| Q1A_Syncheck | Boolean | Sync check relay active (Q1A only) |

---

## 4. MicroGrid — MIED1 & MIED2

Monitoring points in the microgrid. Partially active in Scenario 1 (voltage present but no current/power).

| Column | Unit | Range | Description |
|--------|------|-------|-------------|
| Frequency | Hz | [0, 50.04] | Grid frequency at microgrid point |
| V1/V2/V3 | V | [0, ~244] | Phase voltages (0 during startup) |
| VL1_L2/VL2_L3/VL3_VL1 | V | [0, ~424] | Line voltages |
| Apparent/Real/Reactive | VA/W/VAR | all 0 | No load connected in Scenario 1 |
| L1/L2/L3_Current | A | all 0 | No current flowing in Scenario 1 |

### Sync Angle

| Column | Unit | Range | Description |
|--------|------|-------|-------------|
| MIED1.Sync.Sync_Neut_Angle_Diff | degrees | [-176, 179] | Angle difference between G1 and grid during synchronization |
| MIED2.Sync.Sync_Neut_Angle_Diff | degrees | [-3, 86] | Angle difference for MIED2 sync point |

---


## 5. Transmission — TIED1, TIED2, TIED4

Transmission line monitoring points. Mostly 0 in Scenario 1 except TIED4 voltage.

| Column | Unit | Range | Description |
|--------|------|-------|-------------|
| TIED1.L1/L2/L3_Current | A | all 0 | Transmission line currents (dual measurement) |
| TIED4.Frequency | Hz | [0, 50.12] | Frequency at transmission point 4 |
| TIED4.V1/V2/V3 | V | [0, ~244] | Voltage at transmission point 4 |
| TIED4.VL1_L2/VL2_L3/VL3_VL1 | V | [0, ~424] | Line voltages at transmission point 4 |

---

## 6. VSD — Variable Speed Drives (VSD1, VSD2, VSD3)

Motor speed controllers. VSD1 and VSD2 are active in Scenario 1.

| Column | Unit | Range | Description |
|--------|------|-------|-------------|
| ActualSpeed (VSD1) | RPM | [0, 1505] | Motor 1 actual rotation speed |
| Current (VSD1) | A | [0, 37.5] | Motor 1 current draw |
| ActualSpeed (VSD2) | RPM | [0, 13107] | Motor 2 actual speed (wider range than VSD1) |
| Current (VSD2) | A | [0, 37.3] | Motor 2 current draw |
| ActualSpeed (VSD3) | RPM | all 0 | Motor 3 not running in Scenario 1 |
| E_Stop | Boolean | — | Emergency stop activated |
| Fault | Boolean | — | Fault condition detected |
| Ready | Boolean | — | Drive ready to operate |
| Reset | Boolean | — | Reset command |
| Start | Boolean | — | Start command |
| Start_Flag | Boolean | — | Start sequence in progress |
| Stop | Boolean | — | Stop command |
| Stop_Flag | Boolean | — | Stop sequence in progress |

---
