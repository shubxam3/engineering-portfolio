# Electro-pneumatic gear shifting and clutching

**Formula Manipal (Formula Student), combustion car, 2020 – 2022 · transmission subsystem**

The combustion car runs a Honda CBR600RR engine with its sequential motorcycle gearbox. Instead of a hand lever and a clutch pedal, the driver shifts and clutches with buttons on the steering wheel, and pneumatic actuators do the work. Both hands stay on the wheel, the clutch pedal disappears from the footwell, and shifts are faster and repeatable.

The system was a joint effort of the transmission and electronics subsystems and ran on the car. My part was on the transmission side, starting with the actuator sizing.

## System

| | Gear shifting | Clutch |
|---|---|---|
| Actuator | Pneumatic cylinder on the shift spindle | Spring-return cylinder |
| Valves | Two directional control valves behind a pressure regulator | One directional control valve behind a pressure regulator |
| System pressure | 6 bar | 7.5 bar |
| Torque needed at the spindle | 7.2 Nm | 6.3 Nm |
| Actuation time | 80 ms upshift, 100 ms downshift | 150 ms engage or disengage |
| Air per actuation | 0.042 g | 0.10 g |

Air comes from a 90 cubic inch tank. From the air mass per actuation and the number of shifts per event predicted by lap simulation, one fill covers about 4000 shifts and 3000 clutch actuations, which was then confirmed in endurance test runs.

## Sizing

The sizing starts from the force needed at the shift lever and its travel, and works back to the cylinder and the supply:

| Quantity | Value |
|---|---|
| Force per shift at the lever | 225 N |
| Shifter arm length | 32 mm |
| Cylinder stroke | 25 mm |
| Cylinder bore | 25 mm |
| Supply hose inner diameter | 4 mm |

225 N on a 32 mm arm is the 7.2 Nm at the spindle. From bore and stroke follow the piston area, the swept volume and with it the air mass per shift, which sizes the tank. I set the calculation up as a spreadsheet so bore, stroke and arm length could be traded against each other.

To understand the valve side I also worked through the standard pneumatic control circuits: single- and double-acting cylinders with 3/2 and 5/2 valves, quick-exhaust valves, AND/OR logic valves, time-delay and pressure-sequence valves.

## Control strategies

The valves are driven from auxiliary outputs of the MoTeC M400 engine control unit, which makes shift strategies possible that a driver cannot do by hand:

- **Auto-upshift.** The ECU triggers the upshift itself, so no clutch is needed and less air is used. Measured 0 – 80 km/h in 4.71 s, against 5.03 s with driver-triggered flat shifting.
- **Auto-clutch downshift.** The ECU operates the clutch during downshifts and blocks downshifts above 8000 rpm to prevent over-revving. A manual-clutch downshift took 301 ms on average; over three consecutive downshifts into a hairpin the automatic sequence saves about 0.8 s.

## What I took from it

This was my introduction to fluid power and to actuators as part of a controlled system, and the reason the hydraulic and pneumatic side of my later actuator work felt familiar.
