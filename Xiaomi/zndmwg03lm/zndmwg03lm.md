# Xiaomi Mijia Smart Multi-Mode Gateway 
#####ZNDMWG03LM LM18-MJGWA-V3.0

## Serial console
Standard TTL console at 3.3 volts, using following test pins on PCB:

| Testpoint | Signal |
| ---  | --- |
|TP8  | GND |
|TP11 | TX  |
|TP4| RX |
|TP10|+5v|

Params: 38400 8N1

Serial console input is software-disabled by boot loader.


## PCB Views

![PCB Top](1.jpg)

![PCB Bottom](1.jpg)

## Main CPU

RTL8197FS SoC

![SoC](6.jpg)

## Flash chip
Winbond W25M01GV 1G SPI NAND, 128MiB
![Flash](4.jpg)

## Bluetooth module
Model MHCB03R

![Bluetooth module ](3.jpg)

## ZigBee module

EFR32 MG18232G6

![Zigbee module](5.jpg)

 

## Logs
[Boot log](boot_log.md)

[First start / Failed IKEA lamp attach / OTA MIIO packets](packet_flow.md)