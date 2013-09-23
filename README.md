FitzSPA
=======

Joe Fitz's Simple Power Analysis Tool

Component | Description | Value | notes | Digikey | Price
--- | --- | --- | ---
U1 | AD9200ARZ | 20msps 10-bit A/D converter | |
U2 | AD8130ARMZ | differential amplifier | AD8129 should work better for high gains, but has unresolved issues. use AD8130 for now |
U3 | VAT1-S5-D12-SMT | 5v to +-12v converter | |
JP1 | 2x6 .1" header | | connects to LA |
JP2 | 1x3 .1" header | | connects ot power/ground |
JP3 | 1x6 .1" header | | connects ot DUT |
C1,C2,C3,C4,C5,C6,C7,C8 | 0603 SMT Capacitor | .1uF | |
C11,C12,C13,C14,C15,C16 | 0603 SMT Capacitor | 10uF | doesn't need to be electrolytic |
R1,R2 | 0603 SMT resistor |  | leave empty unless needed to stabilize +-12v output |
R3 | 0603 SMT resistor | 150 ohm | LED series resistor |
R4 | 0603 SMT resistor | 10 ohm | provides a little isolation between digital and analog VCC
Rv | 0603 SMT resistor | 1 ohm | shunt resistor - DUT power crosses over this |
Rg | 0603 SMT resistor | 100 ohm | gain resistor |
Rf1 | 0603 SMT resistor | 1k ohm | gain resistor |
Rf | 84WR SMT Potentiometer |  | leave empty if using fixed Rf1 instead |

