# LiPo-Battery-Charger
A simple PCB project that implements regulated output voltage and battery charging capabilities.

TODO ADD IMAGE HERE.

The purpose of this project was to gain the experience on building out a board that can function from battery supply and also provide battery charging capabilities. Currently, all my projects need to be tethered to a USB supply which is a pain to deal with. I'm hoping to use this project as a building block to add to other projects.

# Features
This board features the following:
* USB-C Power Only input with status LED.
* VBUS, regulated 3v3, and GND output headers.
* Additional VBAT and GND headers for checking battery voltage.
* Capable of charging **Only 3v7 Nominal >= 100mAh Single Cell LiPo Batteries**
  * Adafruit provides compatible cells with appropriate headers: https://www.adafruit.com/product/1578 
* Two charging status LED. Left LED indicates charging and right LED indicates complete charging.

The charging capability is provided by the **MCP73831** charger IC. As mentioned, this charger IC is capable of charging single cell LiPo batteries. See the bullet list above for battery requirements and recommendation.

## Functionality
This board can generate regulated 3v3 power given either VBUS or VBAT are active. The following truth table indicates which voltage source is used to provide power to the 3v3 regulator.
| VBUS Active | VBAT Active | Selected Supply |
| ----------- | ----------- | --------------- |
| False | False | INACTIVE |
| False | True | VBAT |
| True | False | VBUS |
| True | True | VBUS |

An important feature becomes active when both VBUS and VBAT are active. When both sources are active, the VBUS will take priority in providing power to the 3v3 regulator and to the charger IC. This means that the board will provide regulated 3v3 power and charge up the LiPo Battery. In the event where VBUS becomes inactive, VBAT will take over and provide power to the regulator.

# Stackup and Assembly
It is a two-layer board with the following stackup:
| Layer | Type |
| ----- | ---- |
| L1 | PWR |
| L2 | GND |

The board was manufactured by OSHPARK and they came back perfectly! No defects were found.

As for assembly, the board was assembled by me using parts sourced from Digikey. The part selection can be found in (TODO ADD BOM REFERENCE).
