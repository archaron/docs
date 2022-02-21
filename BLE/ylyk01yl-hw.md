# YeeLight YLYK01YL bluetooth remote hardware internals

Built on [TLSR8267](http://wiki.telink-semi.cn/doc/ds/DS_TLSR8267-E_Datasheet%20for%20Telink%20BLE%20SoC%20TLSR8267.pdf) SoC by TeLink semiconductor.


## Board view

![PCB Bottom](ylyk01y/yeelight_YLYK01Y-board1.jpg)
![PCB Bottom close view](ylyk01y/yeelight_YLYK01Y-board2.jpg)
![PCB Top](ylyk01y/yeelight_YLYK01Y-board3.jpg)

### Debug connector pinout:
Main board has 3.3V asynchronus UART & SWS flash/debug onewire interface routed on test pads:

![Debug connector pinout](ylyk01y/yeelight_YLYK01Y-pinout.jpg)

## Flash image

Here is a 512K [flash firmware image](ylyk01y/ylyk01y.bin)