# Thomas Kaunzinger Business Card

Hello! If you're reading this, it means you're a proud owner of my very own business card! This business card is unique in that it incorperates one of my own schematic designs and layouts for a custom Arduino-Uno compatible microcontroller powered by the versatile ATMEGA328P-AU microprocessor. In addition, I also included some other useful references to various standard package footprints, wire gagues, etc. to look back at for reference or practice in populating surface-mount components. Like all of my other personal projects, this business card was designed and layed out by me and is completely open source!

## Source

If you are interested in a few of my non-proprietary PCB designs, you can check out my [Altium Circuitmaker Profile](https://circuitmaker.com/Projects#/thomas%20kaunzinger/7//1 "Circuitmaker Profile"). More specifically, if you are interested in the development of this specific business card circuit board, you can view the source for that [here](https://circuitmaker.com/Projects/Details/Thomas-Kaunzinger-2/Thomas-Kaunzinger-Business-Card "Business Card").

## BOM / Arduino Setup

Regrettably, I am only one person and can not populate every single one of these business cards due to the sheer cost and time needed to do so. However, as I'm a firm believer in good documentation, I would like to include a BOM for the Arduino on the board so that you can populate it yourself!

This board requires intermediate practice in surface-mount soldering techniques and uses components as small as 0603 (I was feeling generous :D). A decent hobbyist soldering iron/station is recommended and optionally a PCB holder and microscope to help with populating.

### BOM

- U1: [ATMEGA328P-AU (TQFP-32 package)](https://www.digikey.com/product-detail/en/microchip-technology/ATMEGA328P-AUR/ATMEGA328P-AURCT-ND/3789455 "Microprocessor")

- U2: [FT232RL](https://www.digikey.com/product-detail/en/ftdi-future-technology-devices-international-ltd/FT232RL-REEL/768-1007-1-ND/1836402 "USB Controller")

- 16MHz: [ABM3B-16.000MHZ-B2-T](https://www.digikey.com/product-detail/en/abracon-llc/ABM3B-16.000MHZ-B2-T/535-9122-1-ND/675639 "16MHz Crystal Resonator") (Note: 16MHz is technically slightly out of spec for the ATMEGA328P at 3.3V VDD<sub>IO</sub>, but a fair bit of testing has shown that this frequency still works well without hiccups, and it is much easier to set-up the Arduino UNO firmware this way).

- 3.3V LDO: [MIC37100-3.3WS](https://www.digikey.com/product-detail/en/microchip-technology/MIC37100-3.3WS-TR/MIC37100-3.3WS-CT-ND/7897216 "3.3V LDO")(Note: this LDO is pin-compatible with the 5V UA78M05 regulator used on the normal Arduino UNOs. Using the 5V regulator should theoretically return 5V VDD<sub>IO</sub>, but I have not tested if this breaks anything else. Also, please note that there are some more commonly used 3.3V LDOs that have the same package, but are not pin-compatible. Please be mindful if you deviate)

- J1, J2, J3: [1 x 15 100mil (254mm) Breakaway Headers (anything will work)](https://www.digikey.com/product-detail/en/sullins-connector-solutions/PREC040SAAN-RC/S1012EC-40-ND/2774814 "40 Length Breakaway Header Row")

- J4: [Mini USB Type B Female Connector](https://www.digikey.com/product-detail/en/edac-inc/690-005-299-043/151-1206-1-ND/4312192 "USB Connector")

- RESET: [B3S-1000 Switch](https://www.digikey.com/product-detail/en/omron-electronics-inc-emc-div/B3S-1000/SW415-ND/20686 "Reset Button")

- F1: [500mA 15V 1812 Fuse](https://www.digikey.com/product-detail/en/bourns-inc/MF-MSMF050-2/MF-MSMF050-2CT-ND/662842 "MF-MSMF050-2 Fuse")

- D1: [SS1P3L-M3/84A Schottky Diode](https://www.digikey.com/product-detail/en/vishay-semiconductor-diodes-division/SS1P3L-M3-84A/SS1P3L-M3-84AGICT-ND/1091672 "Schottky Diode")

- 3.3V, RX, TX, D13: [1206 Green LEDs](https://www.digikey.com/product-detail/en/lite-on-inc/LTST-C150GKT/160-1169-1-ND/269241 "Indicator LEDs")

- R1, R2, R3, R4, R6, R7: [0603 Resistor (280Ω)](https://www.digikey.com/product-detail/en/yageo/RC0603FR-07280RL/311-280HRCT-ND/730058 "Thank you Yageo for your affordable resistors")

- R5: [0603 Resistor (1kΩ)](https://www.digikey.com/product-detail/en/yageo/RC0603FR-071KL/311-1.00KHRCT-ND/729790 "Thank you Yageo for your affordable resistors")

- C1, C2: [0603 Capacitor (22pF)](https://www.digikey.com/product-detail/en/avx-corporation/06035A220JAT2A/478-1167-1-ND/564199 "22 Puff Cap (For Crystal)")

- C5, C6, C8: [0603 Capacitor (0.1μF)](https://www.digikey.com/product-detail/en/kemet/C0603C104Z3VACTU/399-1100-1-ND/411375 "0.1μF Bypass Caps")

- C3, C4, C7: [0603 Capacitor (1μF)](https://www.digikey.com/product-detail/en/samsung-electro-mechanics/CL10A105KA8NNNC/1276-1102-1-ND/3889188 "1μF Bypass Caps")


### Arduino Setup

While you could flash the ATMEGA328P on the board with potentially whatever firmware you want through the on-board SPI pins (provided you have compatable compiled code for the microprocessor), I find that the most versatile use of this device is to flash it with the readily available [Arduino](https://www.arduino.cc/en/main/software "Download Arduino") Bootloader for on-the-fly hacks.

Fortunately, to accomplish this, Sparkfun has [an excellent tutorial](https://learn.sparkfun.com/tutorials/installing-an-arduino-bootloader/all "Flashing Tutorial") on how to install the Arduino bootloader on any Arduino-compatible device (including this business card)! By using either a dedicated programmer or simply another arduino, you can flash the now populated board in a matter of seconds. If you have another arduino, it's as simple as installing the readily available "ArduinoISP" sketch onto the programmer Arduino and hooking it up the respective ISP pins between the boards (the ISP boards are GND, RST, D11, D13, 3V3, and D12 at J3). Provided you follow the sparkfun tutorial and connect the right pins for the SPI communication, you should have no problem getting this board up and running. Please note, if you are using a normal off the shelf Arduino to program this, it will use 5V power and 5V VDD<sub>IO</sub> instead of the 3.3V on this board, however this has not proved to cause any issues during the flashing process in my past experiences.

Anyways, after populating the board and flashing the Arduino Bootloader onto the ATMEGA, you are good to go and ready to upload whatever code you want. If you have any questions, feel free to email me with the address on the business card. Thank you for reading and enjoy!