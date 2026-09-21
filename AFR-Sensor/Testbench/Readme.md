The testbench setup used non-rail to rail Op-amps (LF353 and LM358D) and typical/generic BJTs (2N3904 and 2N3906).
The voltage supply was not ideal (VCC was less than 12V slightly, and 5V was slightly over). Since the op-amps weren't rail to rail, I powered the Op-amps dealing with the lambda output with VCC/2, to allow the voltage to swing near 5V.
V+ = 2.5V approx and V- = 2.1V approx. If you wish to use V+ = 3.300V and V- = 3.000V, then you'd need to change the gain of the Shunt resistor amplifier to account so it can respond to the 300mV differential voltage.
I'll attach an excerpt of my comments from the main multisim schematic.
--- Output voltage analysis ---
Vo = Rf/Ri(VShunt+ - VShunt-) + VShunt+
Vo = Rf/Ri(2.5V - VShunt-) + 2.5V
When I = 0A, VShunt- = VShunt+ = 2.5V, therefore:
Vo = 0 + 2.5V = 2.5V @ I = 0A
--- Gain analysis ---
The differential voltage depends on VShunt-. We can infer the value
from the expected current range: -800uA < 0 < 800uA.
|VShunt+-| = |I|R = 800μA * 120 = 96mV
At a max, Vo = 5V (Max lean condition).
5V = Rf/Ri(96mV) + 2.5V -> 2.5V/96mV = Rf/Ri -> Rf/Ri = 26.04
Since Ri = 1k, then Rf = 26.04k = 26.1k (≤ 1% tol)
For Vo = 0V (Max Rich condition):
0V = Rf/Ri(-96mV) + 2.5V -> -2.5V/-96mV = Rf/Ri -> Rf/Ri = 26.04
Notice the gain value stays the same, therefore it is no problem as long as the gain approximates 26.
Note*: If you wanted to use the stock differential voltage, then you'd need to have a gain that satisfies both the I = 2.5mA case and the I = -2mA case. Am assuming using the gain for I = 2.5mA should suffice, though. 
