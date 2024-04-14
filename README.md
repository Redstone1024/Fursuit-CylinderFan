# Redcraft Fursuit Cylinder Fan

A Simple Rechargeable Cylinder Fan for Fursuit Heads

## Installation

### PCB

First, solder the components to the PCB, you can refer to the method provided in the [Link](https://www.myredstone.top/archives/5215).

The non-silkscreened 0Ohm resistor next to U3 is used to configure the fan PWM positive and negative.
For DV05028B12U, use the 0Ohm resistor to connect pad closest to **inside** PCB (positive PWM).

The JP2 connector is used to connect the battery level indicator module, so **don't** solder XH2.54-2P.

You can refer to the following procedure to verify that the PCB is working, and reproduce the soldering of J1 or U1 if there is an abnormality.

> **Note**: No abnormally high temperatures in the IC and other components throughout the process.

> **Note**: The following tests are performed with a **good** battery.

> **Note**: If your Type-C PD power supply is unable to detect the current status, you can apply an adjustable power supply directly on the Type-C or C23 (**left** end is positive). But don't forget to test if it still works when connected to a standard Type-C PD power supply.

1. Ensure that there is **no shorts** for C1 C2 C23 and that their resistance is at the MOhm level.
2. Ensure that there are **no false shorts** between the IP2368 and Type-C pins and to GND.
3. Ensure LEDs are oriented and colored correctly.
4. When connected to a standard Type-C PD power supply and **without** battery, ensure the power supply should be around **20V** and **0.6W**.
5. Insert a battery of less than **50%** capacity, ensure the red light blinks **4** times and then goes out.
6. When connected to a standard Type-C PD power supply with a **50%** capacity battery.
	1. Ensure the red light comes on quickly and without blinking.
	2. Within IC protocol negotiation, ensure the power supply should be around **0.6W**.
	3. After IC protocol negotiation, ensure the power supply should be about **24W** (12W for 5V, 9V, 12V, 15V).
	4. After IC protocol negotiation, ensure the voltage across R9 should be **10mV** (**right** end is positive).
7. After unplugging the standard Type-C PD power supply, ensure the red light goes off in about 1 second.
8. When the battery is fully charged, ensure the red light will be off and the blue light wull be on.

### 3D Printed Parts

> **Note**: The following parts are printed with a 0.4mm nozzle and 0.2mm layer height.

> **Note**: STLs not mentioned here can be printed using the auto-orientation directly

**CylinderFan-Master-Body.stl** - Position the fan upward and add support to the lower **plane** at the lanyard.

**CylinderFan-Nozzle-\*.stl** - Add support to the outer circle below. Pause the print and add the magnet while the magnet hole closes the layer.

**CylinderFan-Electronic-Body.stl** - Print the LED translucent faces with a white filament.

**CylinderFan-Battery-\*.stl** - If you select a finished battery, you only need to print the CylinderFan-Battery-Adapter\*.stl part,  otherwise print other STLs.

### Assembly

Just assemble according to CAD drawings.

Be careful **NOT** to allow parts to run over, wrap around, or rub the wires.
