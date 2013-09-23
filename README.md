FitzSPA
=======

Joe Fitz's Simple Power Analysis Tool

Component | Description | Value | notes | Digikey | Price
--- | --- | --- | --- | --- | ---
U1 | AD9200ARZ | 20msps 10-bit A/D converter | | AD9200ARSZ-ND | 5.83
U2 | AD8130ARMZ | differential amplifier | AD8129 - unresolved issues. use AD8130 for now | AD8130ARMZ-ND | 4.06
U3 | VAT1-S5-D12-SMT | 5v to +-12v converter | | 102-1386-1-ND | 5.51
JP1 | 2x6 .1" header | | connects to LA | S1012EC-40-ND	| 0.51
JP2 | 1x3 .1" header | | connects ot power/ground | same as jp1 |
JP3 | 1x6 .1" header | | connects ot DUT | same as jp1 |
C1,C2,C3,C4,C5,C6,C7,C8 | 0603 SMT Capacitor | .1uF | | 587-1240-1-ND	| 0.10
C11,C12,C13,C14,C15,C16 | 0603 SMT Capacitor | 10uF | doesn't need to be electrolytic | 587-3238-1-ND	| 0.54
R1,R2 | 0603 SMT resistor |  | leave empty unless needed to stabilize +-12v output |
R3 | 0603 SMT resistor | 150 ohm | LED series resistor | RMCF0603FT150RCT-ND | 0.04
R4 | 0603 SMT resistor | 10 ohm | provides a little isolation between digital and analog VCC | RMCF0603FT10R0CT-ND | 0.04
Rv | 0603 SMT resistor | 1 ohm | shunt resistor - DUT power crosses over this | RMCF0603FT1R00CT-ND	| 0.04 
Rg | 0603 SMT resistor | 100 ohm | gain resistor | RMCF0603FT100RCT-ND | 0.04
Rf1 | 0603 SMT resistor | 1k ohm | gain resistor | RMCF0603FT1K00CT-ND | 0.04
Rf | 84WR SMT Potentiometer |  | leave empty if using fixed Rf1 instead |


Digikey bom in FitzSPA-BOM.csv

$20.15 + shipping
