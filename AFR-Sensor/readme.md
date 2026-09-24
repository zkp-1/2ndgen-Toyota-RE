# Recommendation: Use the 0-5V versions of the Projects

# Multisim folder

- Has the main 0-5V circuit. Mostly did the testing there. Voltage references are real and not ideal (Voltage dividers).
- It has a bunch of comments accounting for stuff like if there were a short circuit, component selection... etc.

# LTSpice folder

- Has both main and OEM style circuit. Does NOT have voltage dividers.
- Has the operation graphs (behavior at different currents).

# Testbench folder

- Custom iteration of the circuit (non-rail to rail op-amp with a pot voltage divider and an older design).
- Pertinent testing information.
- Power draw is <20mA using 12V and 5V. With a status led, it is <50mA.

# KiCAD
- Design block of the circuit.
