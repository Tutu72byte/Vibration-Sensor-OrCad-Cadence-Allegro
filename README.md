## 📋 Description & Functionality

The project consists of a low-power impact and vibration detector optimized for monitoring the security of fixed structures (doors, windows, display cases).

### Working Principle:
1. **Transducer (Piezoelectric Sensor):** Upon a mechanical shock or vibration, the ceramic piezoelectric transducer generates an electric
   voltage directly proportional to the impact acceleration (typical sensitivity: ~40 mV/g; for a 60 g impact, the peak voltage can reach up to ~2 V).
2. **Biasing & Filtering:** High-impedance resistors (R1,R2, 4.7MOhm) form a biasing stage that prevents rapid signal discharge, while capacitor C1
   acts as a first-order low-pass filter to attenuate high-frequency noise and prevent false triggers.
3. **Timing Stage (M74HC123):** A valid signal triggers the `M74HC123` (IC1) dual retriggerable monostable multivibrator.
    The active pulse duration at output pin 13 is set by the external RC timing group consisting of resistor R3 and electrolytic capacitor C2
4. **Output Stage:** During activation, output pin 13 drives NPN transistor `BC547` (T1) into saturation via base resistor
   R4. The transistor operates as an Open Collector switch across connector J1, enabling easy interfacing with external alarm modules, relays, or microcontroller interrupt pins.
5. **Power Supply:** The entire circuit runs on a low 3V supply powered by a compact CR2032 button cell, drawing a minimal current of 5 - 6 mA during operation.

---

## 📐 Technological Parameters & Design Rules (DRC)

* **PCB Stackup:** Double-Sided PCB using FR-4 substrate (0.203 mm dielectric layer, 0.263 mm total thickness).
* **Board Dimensions:** Rectangular shape, fixed at 70mm x 55mm.
* **Mounting Holes:** 4 mechanical mounting holes (3.2mm) positioned in the board corners.
* **Component Placement:** Placed exclusively on the **TOP Layer** using Through-Hole Technology.
* **Signal Traces:** Standard width configured to 0.3mm for control and low-power lines.
* **Power Traces (VDD/VCC):** Increased width of 1.1mm to minimize parasitic resistance and voltage drops.
* **Minimum Clearance:** Defined strictly at 0.35mm between any two conductive elements (trace-trace, trace-pad, pad-pad).
* **Ground Plane (GND):** Implemented as a continuous, extended copper pour across the entire **BOTTOM Layer** to reduce return path impedance and provide EM shielding.
