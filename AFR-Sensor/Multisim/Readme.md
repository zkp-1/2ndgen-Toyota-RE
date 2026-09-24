The multisim file has a lot of comments inside the design. I'll mention the important ones.
Op-amp: I utilzed the MCP6024 since it's a quad, rail-to-rail and can handle -40C thru 120C operation. If you change the op-amp for another one, make sure it is rail to rail, and that it has a good PSRR (power supply rejection ratio; which is how stable it'll behave if the power supply voltage varies) and CMRR (Common mode rejection ratio; which is external noise attenuation).
Shunt AND op-amp inverting and feedback resistance: Select resistors with low ppm (<100, less than <50 is even better). Power rating can be 1/8W or greater.
Emitter resistors:  Select 120ohm resistors of 1/2W capability for safety. It can handle 1/4W during a short circuit to ground, but it is slightly over 80% using 1/4W as a reference but less than 1/4W.
Capacitors: X7R should be good, with good voltage capacity (50V peak to start). Haven't investigated too much into it as of sept 23 2026.
Voltage dividers: They can be separated and each output buffered if desired.
--- If the circuit is to be tested physically ---
On the Shunt measurement rail, sink your desired current using I = Vrail/R (Sinking current means connecting a resistor to the rail, and the other terminal to ground). This simulates a shift to lean condition.
To simulate a rich condition shift, add any voltage (doesn't matter magnitude since the op-amp will force whatever the rail gets to Vrail) in series with the resistor, and this will inject/source current into the shunt, making the PNP sink the current. The equation remains: I = Vrail/R.
If using the 2.5V design, then Vrail = 2.5V. If using the Toyota style references, then Vrail = 3.3V.
Expected behavior:
Idle (no sourcing/sinking): V = Stoich (~2.5V default)
Fully lean (sinking 0.8mA): V = +5V
Fully rich (sourcing 0.8mA): V = 0V (may be millivolts, but it should be less than 500mV)
For more info or a schematic, lookup the testbench circuit I made alongside my results as a reference in the repo.
