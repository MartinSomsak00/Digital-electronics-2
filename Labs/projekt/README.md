  # Water tank controller

### Team members

* Jan Rajm (flowchart, návrh FSM, programování)
* Tomáš Rotrekl (senzor vzdálenosti, programování)
* Martin Šomšák (zpracování)


Link to this file in your GitHub repository:

[https://github.com/your-github-account/repository-name/project](https://github.com/...)

### Table of contents

* [Project objectives](#objectives)
* [Hardware description](#hardware)
* [Libraries description](#libs)
* [Main application](#main)
* [Video](#video)
* [References](#references)

<a name="objectives"></a>

## Project objectives

Cílem bylo sestrojit chytrou vodní pumpu, která bude schopná udržovat výšku hladiny v požadovaných mezích. Předpokládalo se, že tato chytrá pumpa bude sloužit u lokálního zdroje vody, tzn. že je k dispozici hlavní zdroj vody, ze kterého by bylo možné dočerpávat vodu v případě potřeby (např. vodovodní řád).

<a name="hardware"></a>

## Hardware description

K měření hladiny vody byl použit ultrazvukový měřič vzdálenosti: [Ultrasonic HC-SR04 Module](https://www.electronicwings.com/avr-atmega/ultrasonic-module-hc-sr04-interfacing-with-atmega1632)
Ultrazvukový modul HC-SR04 pracuje na principu systému SONAR a RADAR. Má ultrazvukový vysílač, přijímač a řídicí obvod. 4 piny, *Vcc, Gnd, Trig a Echo*. Přivedením pulsu na Trig (10us) vygeneruje 8 pulsu s frekvencí 40kHz a Echo pin se přepne do vysoké úrovně a zůstane tak dokud nedostane signál zpět. Podle času jak dlouho byl pin Echo v úrovni High se pak lehce spočítá pomocí rychlosti zvuku ve vzduchu vzdálenost objektu, v našem případě vodní hladiny.
Byla použita deska *Arduino Uno* s čipem [ATmega328P](https://www.microchip.com/en-us/product/ATmega328p)


<a name="libs"></a>

## Libraries description

Write your text here.

<a name="main"></a>

## Main application

Write your text here.

<a name="video"></a>

## Video

 [Video](https://www.youtube.com/watch?v=KrOki5VO4F4)
 https://www.youtube.com/watch?v=KrOki5VO4F4

Write your text here

<a name="references"></a>

## References

1. Write your text here.
   