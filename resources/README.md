# Overzicht van extra modules

Deze uitbreiding beschrijft twee optionele hardwarecomponenten die beschikbaar zijn in het labo-opstelling: 

- een DMX moving head
- een Siemens TC35 GSM-module

> [!Note]
>
> Deze modules zijn niet standaard opgenomen in de oefeningen, maar kunnen op aanvraag gebruikt worden voor uitbreiding of experiment. Vraag gerust aan de docent voor ondersteuning of toegang tot deze hardware.



------------

### Moving Head

Een moving head is een schijnwerper die wordt gebruikt als podiumverlichting bij evenementen en tv-programma's. Men kan vaak de beweging (pan/tilt), kleur, gobo's en dimmerfuncties aansturen. Voor het aansturen van moving heads wordt vaak het DMX-protocol gebruikt, maar er kan ook gebruikgemaakt worden van de ingebouwde bewegingen of bewegingen op muziek door middel van ingebouwde microfoons. De hoeveelheid DMX-kanalen kan uiteenlopen van eenvoudige moving heads tot moving heads met dertig kanalen voor professioneel gebruik. Dat wil zeggen dat deze moving heads meer functies hebben ten opzichte van de simpelere uitvoering.

### Aansluiting

- **DMX IN**: verbinden met de EL6851 DMX master terminal.
- **Voeding**: 230V via standaard IEC-kabel.

### Referenties

- [Algemene uitleg over moving heads](https://www.learnstagelighting.com/what-is-a-moving-head-light/)
- Product informatie over de [Fun Generation PicoSpot 20 LED](https://open-fixture-library.org/fun-generation/picospot-20-led)
- Datasheet: [PicoSpot_372642_r3](PicoSpot_372642_r3.pdf) 

--------------

### Siemens TC35 GSM Module

De Siemens TC35 is een seriële GSM-modem die SMS en oproepen kan versturen via AT-commando’s.

### Aansluiting

- **RS232**: verbinden met de Beckhoff EL6002 terminal
- **Voeding**: 5–12V DC
- **SIM-kaart**: vereist actieve SIM

### SIM-kaart

- **Gegevens**: de SIM-kaart en de PIN-code krijg je van de docent.


### Gebruik

- Communicatie via AT-commando’s zoals `AT+CMGS` voor SMS.
- TwinCAT kan via seriële communicatieblokken AT-commando’s versturen.

### Referenties

- [Siemens TC35 datasheet](https://www.scribd.com/document/23424562/Siemens-TC35-Datasheet)
- [AT Command Set](https://www.sparkfun.com/datasheets/CellularModules/AT_Commands_v1.0.pdf)

---------

### Beckhoff EL6002 RS232 Terminal

Deze terminal biedt seriële communicatie via RS232 en is geschikt voor het aansturen van de TC35 GSM-module.

### Aansluiting

- **COM-poort parameters**: instellen via TwinCAT configuratie
- **TwinCAT functieblok**: `FB_SerialCommunication` of `FB_EL600xCommunication`

### Referentie

- [EL6002 handleiding](https://download.beckhoff.com/download/document/io/ethercat-terminals/el6002en.pdf)