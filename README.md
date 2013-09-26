FitzSPA
=======

Joe Fitz's Simple Power Analysis Tool

This is a simple board for monitoring power analysis of small microcontroller circuits.

## Theory

The current across the shunt resistor Rv is measured with a differential amplifier U2. The output is digitized by the A-D converter, U1, which is triggered and synchronized by the device's own clock signal. The JP1 pins connect to a logic analyzer for sampling.

The differential amplifier will cancel out all sorts of common mode noise and only amplify the voltage across the Rv shunt resistor, which will be proportional to the instantaneous current draw of your target device. By synchronizing the A/D sampling to the device clock, we can get a digital readout at roughly the same time every clock cycle and not have to oversample 10x or more. Right now the Logic analyzer connection is asynchronous, but that should be fixed in future revisions.

Future versions will integrate a Cypress EZ-usb FX2 logic analyzer and power regulation, but they were excluded to reduce time and complexity for revision 1.0

##Using

Connect the logic analyzer to the J1 connector. Pin1 in the upper left is AD0, the LSB. The bottom two pins are both ground. If you have an 8-bit logic analyzer, start with the 8 MSBs, and if all of your sampling is in the same range, try connecting to less significant pins for higher gain.

Power +5vdc can come from a USB cable, an external supply, your logic analyzer, or from your target system

JP3 has a number of pins for various ways of connecting your shunt resistor and powering your target. Pins in order: VCC  Rv+  Rv-  GND  GND  CLK

To measure with a shunt on VCC, power supplied by FitzSPA:
* Connect VCC and Rv+ with a jumper
* Connect RV- to your target board's VCC
* Connect GND to your target board's GND
* Connect CLK to your target board's CLK

To measure with a shunt on GND, power supplied by FitzSPA:
* Connect VCC to your target board's VCC
* Connect Rv+ to your target board's ground
* Connect RV- and GND with a jumper
* Connect CLK to your target board's CLK

To measure with a shunt on VCC, with a separate external supply:
* Connect Rv+ to the external supply
* Connect RV- to your target board's VCC
* Connect GND to your target board's GND and external supply GND
* Connect CLK to your target board's CLK

To measure with a shunt on GND, power supplied by FitzSPA:
* Connect your external supply to the target board's VCC
* Connect Rv+ to your target board's ground
* Connect RV- and GND with a jumper
* Connect the second GND pin to the external supply's GND
* Connect CLK to your target board's CLK

Fire up your logic analyzer, turn on your board, and you should see the live power consumption updated each clock cycle!

##Building
Rev 1.0 is functional but still has some kinks to be ironed out. There are a few options for building out your board:

#### Differential Amplifier:
The AD8129 should provide much higher gains for more sensitive readings. However, I still haven't debugged why the AD8130 works fine and the AD8129 does not at G=10. For the time being, use the x30 unless you want to help the debug effort. the x29 is digikey AD8129ARMZ-ND
#### Gain setting circuit:
The gain of the differential amplifier is 1+(Rf/Rg). The default BOM uses 1k Ohm/100 Ohm, but you can vary this, or replace Rf with a potentiometer, such as digikey 987-1155-ND
####Voltage Regulator Load:
the 5v to +-12v regulator needs a minimum load to work properly. I haven't needed them, but populating R1 and R2 with 2.4k ohm resistors should provide the required load. digikey RMCF0603FT2K40CT-ND

####For the basic build you probably want:

Component | Description | Value | notes | Digikey | Price
--- | --- | --- | --- | --- | ---
U1 | AD9200ARZ | 20msps 10-bit A/D converter | | AD9200ARSZ-ND | 5.83
U2 | AD8130ARMZ | differential amplifier | AD8129 - unresolved issues. use AD8130 for now | AD8130ARMZ-ND | 4.06
U3 | VAT1-S5-D12-SMT | 5v to +-12v converter | | 102-1386-1-ND | 5.51
JP1 | 2x6 .1" header | | connects to LA | S1012EC-40-ND	| 0.51
JP2 | 1x3 .1" header | | connects ot power/ground | same as jp1 |
JP3 | 1x6 .1" header | | connects ot DUT | same as jp1 |
C1,C2,C3,C4,C5,C6,C7,C8 | 0603 SMT Capacitor | .1uF | | 587-1240-1-ND	| 0.10
C11,C12,C13,C14,C15,C16 | 0805 SMT Capacitor | 10uF | doesn't need to be electrolytic | 587-1295-1-ND | 0.54
R1,R2 | 0603 SMT resistor |  | leave empty unless needed to stabilize +-12v output |
R3 | 0603 SMT resistor | 150 ohm | LED series resistor | RMCF0603FT150RCT-ND | 0.04
R4 | 0603 SMT resistor | 10 ohm | provides a little isolation between digital and analog VCC | RMCF0603FT10R0CT-ND | 0.04
Rv | 0603 SMT resistor | 1 ohm | shunt resistor - DUT power crosses over this | RMCF0603FT1R00CT-ND	| 0.04 
Rg | 0603 SMT resistor | 100 ohm | gain resistor | RMCF0603FT100RCT-ND | 0.04
Rf1 | 0603 SMT resistor | 1k ohm | gain resistor | RMCF0603FT1K00CT-ND | 0.04
Rf | 84WR SMT Potentiometer |  | leave empty if using fixed Rf1 instead |

The Digikey BOM is saved in FitzSPA-BOM.csv, you can upload or paste it's contents into the BOM wizard: https://www.digikey.com/classic/registereduser/BOMWizard.aspx

$20.15 + shipping
