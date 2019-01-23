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

