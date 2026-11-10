# Pneumatic gear shifter

**Formula Manipal (Formula Student), 2020 · Excel, pneumatic circuit design**

The combustion car used a motorcycle gearbox with a sequential shift drum. A pneumatic actuator on the shift lever lets the driver change gear from paddles on the steering wheel, which shortens the shift and keeps both hands on the wheel. I studied what such a system needs and sized the actuator. The shifter was built and ran on the car.

## Sizing

Starting point is the force the gearbox needs at the shift lever and the travel of the lever:

| Quantity | Value |
|---|---|
| Force per shift at the lever | 225 N |
| Shifter arm length | 32 mm |
| Cylinder stroke | 25 mm |
| Cylinder bore | 25 mm |
| Supply hose inner diameter | 4 mm |

From these I worked out the piston area, the area ratio between cylinder and hose, the air velocities in both, and from an energy balance on the flow the supply pressure needed to complete a shift. The calculation is set up as a spreadsheet so bore, stroke and lever length can be traded against each other.

## Circuit design

To understand the valve side I worked through a set of standard pneumatic control problems and built the circuits for them:

- single-acting and double-acting cylinders with 3/2 and 5/2 directional valves
- quick-exhaust valves to speed up the return stroke
- dual-pressure (AND) and shuttle (OR) valves for interlocks
- time-delay and pressure-sequence valves for timed and pressure-dependent strokes

A shifter is the same building blocks arranged for two short, fast strokes: a double-acting cylinder, a 5/2 solenoid valve triggered from the paddles, and quick exhausts to keep the shift time down.

## What I took from it

This was my introduction to fluid power, and the reason the hydraulic and pneumatic side of later actuator work felt familiar.
