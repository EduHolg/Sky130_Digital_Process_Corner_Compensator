## How it works

This design implements a fully–digital process corner classifier using the open-source SkyWater 130 nm PDK. A current-starved Ring Oscillator (RO) is used as a sensing element whose oscillation frequency shifts depending on the silicon process corner. The RO output is digitized through a Frequency-to-Digital Converter (FDC). The resulting 6-bit digital code is then compared against predefined frequency bands for SS, SF, TT, FS and FF. Based on the detected corner, the system asserts dedicated digital control signals that can be used by downstream analog or mixed-signal blocks (e.g. a ramp generator) to adapt and compensate transistor mismatch.

## How to test

1. Provide a 1.2 MHz reference clock to the FDC.
2. Power the chip at nominal VDD.
3. Observe the output of the FDC or the corner classification output bus.
4. Sweep the PVT condition (e.g. select a process corner model or vary temperature in simulation).
5. For each corner, verify that:
   - RO frequency shifts
   - FDC output code changes accordingly
   - Correct corner flag is asserted

For full system validation, connect the corner outputs to the ramp generator and verify that all corners converge to the reference behavior after compensation.

## External hardware

None required.  
All sensing, digitization, comparison and compensation are fully on-chip and fully digital.
