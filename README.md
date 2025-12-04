![Overview](./resources/Overview.jpg)

## The setup

DMX is a standard for digital communication networks that are commonly used to control lighting and effects. It can be used to control almost anything, reflecting its popularity in all types of venues. Because DMX does not include automatic error checking and correction, it is therefore not an appropriate control for hazardous applications, such as pyrotechnics or movement of theatrical rigging. However, it is still used for such applications. False triggering may be caused by electromagnetic interference, static electricity discharges, improper cable termination, excessively long cables, or poor quality cables.

At the datalink layer, a DMX512 controller transmits asynchronous serial data at 250 kbit/s. The data format is fixed at one start bit, eight data bits (least significant first), two stop bits and no parity.

> BeckHoff Application Film: [Partnership with PIXERA for media and building automation](https://www.youtube.com/watch?v=Y5K_fA3BEpw)

## Hardware

- DMX controller: DMX-SPI Decoder DMX200
  - LED strip: 12V WS2811 LED Strip (20 leds of the 5050 kind)

- *GSM module: Siemens TC35 for SMS and call (not used)*
- *DMX Moving Head: Fun Generation PicoSpot 20 LED (not used)*
- PLC terminal: 
  - EL6851 DMX master terminal
  - *EL6002 RS232 serial communication terminal (not used)*



## Preperations

- Lees de [documentatie van de LED driver](./resources/DMX200.pdf).
- Raadpleeg de handleiding van de Beckhoff [EL6851 DMX Master](https://download.beckhoff.com/download/Document/io/ethercat-terminals/el6851en.pdf). Lees zeker de pagina’s:
    - Product overview => Introduction
    - Product overview => Technical data 
    - Mounting and wiring => LEDs and connection
    - Commissioning => Basic function principles
- Lees volgende pagina’s over de DMX bibliotheek [Tc2_DMX](https://infosys.beckhoff.com/english.php?content=../content/1033/tcplclib_tc2_dmx/index.html&id=3663748578736491244)
    - Introduction
    - DMX
    - Programming => Function blocks => Low Level => Base => FB_EL6851CommunicationEx
    - Programming => DUTs => Structures => ST_EL6851InData, ST_EL6851OutData en ST_DMXCommandBuffer
    - Appendix => Example: DMX master

## Goals

1.  Leg in je eigen woorden DMX uit. Hoe is het opgebouwd en wat kan je ermee?
2.  Beschrijf de aansluitingen van de EL6851.
3.  Beschrijf de ‘FB_EL6851CommunicationEx’ functieblok. Welke zijn de in- en uitgangen en waarvoor wordt deze gebruikt?
4.  Beschrijf de ‘ST_EL6851InData’ structure. Wat is de inhoud en waarvoor wordt deze gebruikt?
5.  Beschrijf de ‘ST_EL6851OutData’ structure. Wat is de inhoud en waarvoor wordt deze gebruikt?
6.  Beschrijf de ‘ST_DMXCommandBuffer’ structure. Wat is de inhoud en waarvoor wordt deze gebruikt?
7.  Beschrijf de aansluitingen en de werking van de DMX LED-strip controller.
8.  Beschrijf de aansluitingen en de werking van de DMX200.

## Exercises

Programmeer de PLC zodat de ganse RGB LED-strip te besturen is vanuit een visualisatie. Voor DMX te programmeren dien je de bibliotheek Tc2_DMX toe te voegen bij je References.

Programmatie (minimaal vereist om 60% te behalen)

1. Maak gebruik van de ‘FB_EL6851CommunicationEx’ functieblok voor de communicatie met de EL6851. Koppel de juiste variabelen met de EL6851. Laat de status van deze functieblok zien in de visualisatie voor snelle foutopsporing. (5%)
2. Gebruik de array “arrProcessData” van de FB_EL6851CommunicationEx om data op de DMX bus te zetten. Zorg ervoor dat de DMX LED-strip controller vanuit de visualisatie te bedienen is. (5%)
3. Gebruik de DMX LED-strip controller om een status van een 'motor' weer te geven, die selecteerbaar is via een combo box integer in de visualisatie. Deze combo box heeft zowel een enumerator als een text list nodig.  (15%)
   - NOT READY: alle blauwe LEDs knipperen
   - READY: alle blauwe LEDs aan
   - MOVING: alle groene LEDs knipperen
   - LOW SPEED: alle groene LEDs aan
   - EMERGENCY: alle rode LEDs knipperen
4. Programmeer een looplicht met de DMX200 driver. Ga zelf na wat de volgorde voor de LEDs moet zijn. Dit looplicht moet zowel naar links als naar rechts kunnen gaan, dit is te kiezen in de visualisatie. De kleur van het looplicht mag je zelf kiezen. Deze functie is in- en uit te schakelen in de visualisatie. (25%)
5. Gebruik een potentiometer om de snelheid van je looplicht aan te passen en deze op het display dat verbonden is met de EL400x te tonen. (10%)

Bijkomende programmatie (Percentage telt enkel indien minimale programmatie bereikt is).

6. Programmeer een shooting light met de DMX driver. Met 3 druktoetsen kan men iedere kleur afzonderlijk van links naar rechts laten vloeien. Dit slecht over één helft van de LED strip. Met de drie andere druktoetsen kan men hetzelfde van rechts naar links doen. In tegenstelling tot het looplicht komt de LED niet meer terug, maar verlaat de LED strip. Men moet meerdere keren eenzelfde kleur kunnen laten afschieten. (20%) 
7. Bereken van de DMX LED-strip controller de totale brandduur voor elke kleur van LEDs en de totale brandduur van de volledige LED strip in minuten. De totale brandduur is niet de som van de brandduur per kleur! Maak zelf een structure aan waarin deze gegevens samen vervat zitten. (20%)

## Questions

For questions and support please place a comment in the pull request titled **Feedback**.

## Remarks

Take care of the setup. Afterwards return the setup to its original state and place it on top of the lab table in the same place. If you notice a defect, you must immediately inform the teacher.
