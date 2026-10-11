# LiPo-Battery-Charger
A simple PCB project that implements regulated output voltage and battery charging capabilities.

TODO ADD IMAGE HERE.

The purpose of this project was to gain the experience on building out a board that can function from battery supply and also provide battery charging capabilities. Currently, all my projects need to be tethered to a USB supply which is a pain to deal with. I'm hoping to use this project as a building block to add to other projects.

# Features
This board features the following:
* USB-C Power Only input with status LED.
* VBUS, regulated 3v3, and GND output headers.
* Additional VBAT and GND headers for checking battery voltage.
* Two charging status LED. Left LED indicates charging and right LED indicates complete charging.

## Functionality
This board can generate regulated 3v3 power given either VBUS or VBAT are active. The following truth table indicates which voltage source is used to provide power to the 3v3 regulator.
| VBUS Active | VBAT Active | Selected Supply |
| ----------- | ----------- | --------------- |
| False | False | INACTIVE |
| False | True | VBAT |
| True | False | VBUS |
| True | True | VBUS |

An important feature becomes active when both VBUS and VBAT are active. When both sources are active, the VBUS will take priority in providing power to the 3v3 regulator and to the charger IC. This means that the board will provide regulated 3v3 power and charge up the LiPo Battery. In the event where VBUS becomes inactive, VBAT will take over and provide power to the regulator.
