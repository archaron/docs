# YeeLight YLKG08YL bluetooth dimmer lamp control hardware internals

Built on the universal TLV0.1 module. Based on [TLSR8267](http://wiki.telink-semi.cn/doc/ds/DS_TLSR8267-E_Datasheet%20for%20Telink%20BLE%20SoC%20TLSR8267.pdf) SoC by TeLink semiconductor.


## TLV0.1 PCB 

![PCB Top](ylkg08yl/yeelight_tlv01.png)

![Pinout](ylkg08yl/yeelight_tlv01_pinout.png)

## Board view & debug interfaces

Main board has 3.3V asynchronus UART & SWS flash/debug onewire interface routed on test pads: 

![Board](ylkg08yl/yeelight_YLKG08YL_board.jpg)

## Flash image

Here is a 512K [flash firmware image](ylkg08yl/ylkg08yl.bin)