MVSPlus
=======

Arduino replacement for both MV-LED (credits) and MV-ELA (lamp driver) Neo Geo MVS arcade hardware

These specialist pieces of hardware are becoming increaingly hard to find and more expensive with their increasing rarity.
MVSPlus addresses this issue by utilising a relatively cheap Arduino Mega 2560

By default the sketch utilisies a SainSmart LCD to display the credits and current game position but, with some un-commenting, it supports 7-Segment display output (via MVLED.h) and LEDs / bulbs for game position.
When attempting to connect multiple output pins on an arduino supply a relatively high input voltage (9V+) to the arduino.

Arduino Setup
=============

Input:
- Game position - connect EL pins 2 -> 6 (asc) from MVS to odd pins 53 -> 45 (desc) on arduino
- Credits - connect 1P pins 3 -> 12 (asc) from MVS to odd pins 23 -> 39 (asc) on arduino

Output:
- For Sainsmart LCD, plug in shield and initialise with the following pins:
LiquidCrystal lcd(8, 13, 9, 4, 5, 6, 7);
- For seven-segment displays include MVLED.h, uncomment respective code and use a 74HC595 shift register per 7-seg. For the first digit shift register, connect the latch, data and clock pins to arduino pins 2,3 and 4 respectively. The second digit's register should connect with 5,6 and 7.
- For LED / bulb output uncomment respective code and connect bulb pins to arduino pins 42, 44, 46 and 48.
