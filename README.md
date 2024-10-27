# Redcraft Fursuit Cylinder Fan

A Simple Rechargeable Cylinder Fan for Fursuit

Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg

## Installation

> **Note**: The BOM.csv is based on the Type-C with finished battery variant, if you choose another variant please read below first.

### PCB

First, solder the components to the PCB, you can refer to the method provided in the [Link](https://www.myredstone.top/archives/5215).

The non-silkscreened 0Ohm resistor next to U3 is used to configure the fan PWM positive and negative.
For DV05028B12U, use the 0Ohm resistor to connect pad closest to **inside** PCB (positive PWM).

The JP2 connector is used to connect the battery level indicator module, so **don't** solder PZ2.54-2X2P.

If you choose the DC version, you only need to solder C21 C22 JP1 JP3 JP4 R23 R24 R25 R26 U2 U3 VR1.

If you choose the Type-C version, You can refer to the following procedure to verify that the PCB is working, and refer FAQ if there is an abnormality.

> **Note**: No abnormally high temperatures in the IC and other components throughout the process.

> **Note**: The following tests are performed with a **good** battery.

> **Note**: If your Type-C PD power supply is unable to detect the current status, you can apply an adjustable power supply directly on the Type-C or C23 (**left** end is positive). But don't forget to test if it still works when connected to a standard Type-C PD power supply.

1. Ensure that there is **no shorts** for C1 C2 C23 and that their resistance is at the MOhm level (C23 is at the kOhm level).
2. Ensure that there are **no false shorts** between the IP2368 and Type-C pins and to GND.
3. Ensure LEDs are oriented and colored correctly.
4. When connected to a standard Type-C PD power supply and **without** battery.
	1. Ensure the red light are **on** and the blue light is **off**.
	2. Ensure the green light are on if the power supply supports 20V.
    3. Ensure the power supply should be around **20V** (or 5V, 9V, 12V, 15V depending on the power supply).
	4. Ensure the power supply should be around **0.6W**.
	5. Ensure the C2 voltage should be around **12.6V**.
5. Insert a battery of less than **50%** capacity, ensure the red light blinks **4** times and then goes out.
6. When connected to a standard Type-C PD power supply with a **50%** capacity battery (**Pay attention to high temperature**).
	1. Ensure the red light **comes on quickly without blinking** and the blue light is **off**.
	2. Ensure the green light are on if the power supply supports 20V.
	3. Within IC protocol negotiation, ensure the power supply should be around **0.6W**.
	4. After IC protocol negotiation, ensure the power supply should be about **24W** (or 12W for 5V, 9V, 12V, 15V).
	5. After IC protocol negotiation, ensure the voltage across R9 should be **10mV** (**right** end is positive).
7. After unplugging the standard Type-C PD power supply, ensure the red and green lights goes off in about 1 second.
8. When the battery is fully charged, ensure the red light will be off and the blue light wull be on.
9. When connected to a fast charging protocol tester.
	1. Ensure the red light **comes on quickly without blinking** and the blue light is **off**.
	2. Ensure the green light are on if you are testing outputs above 15V.
	3. Ensure support PD3.0 30W, APPEL 2.4A, BC1.2DCP, QC3.0 5V-12V, AFC 25W, FCP 24W, SCP 25W, etc.
10. Connect the fan and make sure the fan can rotate and adjust the speed properly.
11. Ensure the battery level meter can correctly display the battery level.

### 3D Printed Parts

> **Note**: The following parts are printed with a 0.4mm nozzle and 0.2mm layer height.

> **Note**: STLs not mentioned here can be printed using the auto-orientation directly

**CylinderFan-Master-Body.stl** - Position the fan upward and add support to the lower **plane** at the lanyard.

**CylinderFan-Master-FanMount.stl** - Add a cylinder to the large center hole, set up layer 0 top, bottom, and walls with 15% honeycomb fill.

**CylinderFan-Nozzle-\*.stl** - Add support to the outer circle below. Pause the print and add the magnet while the magnet hole closes the layer.

**CylinderFan-Electronic-Body-\*.stl** - Select one of the DC and Type-C versions to print.

**CylinderFan-Electronic-Body-Type-C.stl** - Print the LED translucent faces with a white filament. Add support to bottom slide.

**CylinderFan-Electronic-KnobRing.stl** - Print with TPU and controlle damping through fuzzy skin.

**CylinderFan-Battery-\*.stl** - If you select a finished battery, you only need to print the CylinderFan-Battery-Adapter\*.stl part,  otherwise print other STLs.

### Assembly

A total of three to five AWG24 wires are required:

- **Red** - Connect pin 1 of the toggle switch to pin 4 of PCB JP2.
- **Yellow** - Connect pin 2 of the toggle switch to pin 3 of PCB JP2 and the positive of the Li-ion battery level indicator module.
- **Black** - Connect pin 3 of the toggle switch to pin 2 of PCB JP2 and the negative of the Li-ion battery level indicator module.

Be careful to route these wires through CylinderFan-Electronic-KnobTop.stl and CylinderFan-Electronic-Potentiometer.stl and not to impede the rotation of the structure.

The other parts are simply assembled according to the CAD drawings.

Be careful **NOT** to allow parts to run over, wrap around, or rub the wires.

### FAQ

**Q**: Why is the red light always on and not off or higher than a second when I remove the power while charging?

**A**: Major MOSFET G-pin is disconnected. Resolder the main MOSFETs and make sure there is enough tin in the G-pin.

**Q**: Why is there a large number of unsupported protocols during protocol detection?

**A**: Type-C signal pin is disconnected or IP2368 is disconnected. Resolder them reference [Link](https://www.myredstone.top/archives/5215).

**Q**: Why does the protocol detection show that QC3.0 12V is not supported?

**A**: Major MOSFET G-pin is disconnected. Resolder the main MOSFETs and make sure there is enough tin in the G-pin.

**Q**: Why does the red light not go out and the blue light not come on after a full charge?

**A**: If the red light does not flash when the battery is inserted, the capacitor was charged when the battery was replaced and did not recognize the new battery correctly. Just disconnect the battery and wait for the capacitor to discharge and reinsert it. If the red light blinks four times when the battery is inserted, it means that the MOSFET G-pin is disconnected, so re-solder them.

**Q**: Why does Type-C not make good contact when plugged in?

**A**: Presence of flux in Type-C causing isolated contacts or the temperature or time spent soldering the Type-C is excessive, clean the Type-C or use a new Type-C connector.

**Q**: Why is the input normal but the output blinks red and blue at the same time and the blue blinks for a shorter time than the red?

**A**: Major circuits such as inductors have false soldering, re-solder them.
