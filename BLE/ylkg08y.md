
# YeeLight YLKG08YL bluetooth dimmer lamp control



### BLE Services
| Handle  	| UUID  	| Value  	| Description  	| Notice  	|
|---	|---	|---	|---	|---	|
|**0x0001** |**00002800-0000-1000-8000-00805f9b34fb**|**95 fe**|**Primary Service**|**Mi IoT Discovery service => FE95**|
|	|	|	|	|	|
|**0x0002**|**00002803-0000-1000-8000-00805f9b34fb**|**18 00**|**Characteristic**|**[NOTIFY, WRITE]**|
|0x0003|00000001-0000-1000-8000-00805f9b34fb|00 00 00 00 00 00 00 00 00 00 00 00|Value||
|0x0004|00002902-0000-1000-8000-00805f9b34fb|00 00|Client Characteristic Configuration|
|0x0005|00002901-0000-1000-8000-00805f9b34fb|token|Characteristic User Description|
|	|	|	|	|	|
|**0x0006**|**00002803-0000-1000-8000-00805f9b34fb**|**02 00**|**Characteristic**|**[READ]**|
|0x0007|00000002-0000-1000-8000-00805f9b34fb|00 00|Value|
|0x0008|00002901-0000-1000-8000-00805f9b34fb|productid|Characteristic User Description|
|	|	|	|	|	|
|**0x0009**|**00002803-0000-1000-8000-00805f9b34fb**|**02 00**|**Characteristic**|**[READ]**|
|0x000a|00000004-0000-1000-8000-00805f9b34fb|5c 0b 1f 0a 41 0c 2a b0 39 4b|Value|
|0x000b|00002901-0000-1000-8000-00805f9b34fb|ver|Characteristic User Description|
|	|	|	|	|	|
|**0x000c**|**00002803-0000-1000-8000-00805f9b34fb**|**18 18**|**Characteristic**|**[NOTIFY, WRITE]**|
|0x000d|00000005-0000-1000-8000-00805f9b34fb|00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00|Value||
|0x000e|00002901-0000-1000-8000-00805f9b34fb|wificfg|Characteristic User Description||
|	|	|	|	|	|
|**0x000f**|**00002803-0000-1000-8000-00805f9b34fb**|**08 00**|**Characteristic**|**[WRITE]**|
|0x0010|00000007-0000-1000-8000-00805f9b34fb|00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00|Value||
|0x0011|00002901-0000-1000-8000-00805f9b34fb|eventrule|Characteristic User Description||
|	|	|	|	|	|
|**0x0012**|**00002803-0000-1000-8000-00805f9b34fb**|**08 00**|**Characteristic**|**[WRITE]**|
|0x0013|00000010-0000-1000-8000-00805f9b34fb|00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00|Value||
|0x0014|00002901-0000-1000-8000-00805f9b34fb|authentication|Characteristic User Description||
|	|	|	|	|	|
|**0x0015**|**00002803-0000-1000-8000-00805f9b34fb**|**0a 02**|**Characteristic**||
|0x0016|00000013-0000-1000-8000-00805f9b34fb|ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff|Value|[READ, WRITE]|
|0x0017|00002901-0000-1000-8000-00805f9b34fb|sn|Characteristic User Description||
|	|	|	|	|	|
|**0x0018**|**00002803-0000-1000-8000-00805f9b34fb**|**0a 00**|**Characteristic**|[**READ, WRITE]**|
|0x0019|00000014-0000-1000-8000-00805f9b34fb|10 d8 99 8c 8e cd 72 9d e4 21 02 8d|Value||
|0x001a|00002901-0000-1000-8000-00805f9b34fb|beaconkey|Characteristic User Description||



### Discovery packet
```
Frame 97: 46 bytes on wire (368 bits), 46 bytes captured (368 bits) on interface 0
Bluetooth
Bluetooth HCI H4
    [Direction: Rcvd (0x01)]
    HCI Packet Type: HCI Event (0x04)
Bluetooth HCI Event - LE Meta
    Event Code: LE Meta (0x3e)
    Parameter Total Length: 43
    Sub Event: LE Advertising Report (0x02)
    Num Reports: 1
    Event Type: Connectable Undirected Advertising (0x00)
    Peer Address Type: Public Device Address (0x00)
    BD_ADDR: Yeelink_c2:44:69 (f8:24:41:c2:44:69)
    Data Length: 31
    Advertising Data
        Flags
            Length: 2
            Type: Flags (0x01)
            000. .... = Reserved: 0x0
            ...0 .... = Simultaneous LE and BR/EDR to Same Device Capable (Host): false (0x0)
            .... 0... = Simultaneous LE and BR/EDR to Same Device Capable (Controller): false (0x0)
            .... .1.. = BR/EDR Not Supported: true (0x1)
            .... ..1. = LE General Discoverable Mode: true (0x1)
            .... ...0 = LE Limited Discoverable Mode: false (0x0)
        Device Name: yee-rc
            Length: 7
            Type: Device Name (0x09)
            Device Name: yee-rc
        Service Data - 16 bit UUID
            Length: 19
            Type: Service Data - 16 bit UUID (0x16)
            UUID 16: Xiaomi Inc. (0xfe95)
            Service Data: 5132b603016944c24124f80200020110
    RSSI: -43dBm
```


#### Service data 
UUID 16: Xiaomi Inc. (*0xfe95*)

|Data |Mandatory|Length| Field description | Note|
|---	|---|--- |---	|---|
|51 32|yes|2|Frame Control|0x3251 Refer to [Frame control structure](#frame-control-field)|
|b6 03|yes|2|Product ID|0x03b6|
|01|yes|1|Frame Counter||
|69 44 c2  41 24 f8|no|6|MAC address| F8:24:41:C2:44:69| 
|--|no|1|Capability|Refer to [capability structure](#capability-field)|
|00 02 01 10|no|N x ObjCount|Objects|Refer to [Object structure](#object-structure)|
|--|no|3|Random number|Mandatory, if encryption is used|

##### Frame Control field
```
0x3251 => 
0 ...............15
1000 1010 0100 1100
```

|Value| Bit number| Field name| Description
|---	|---	|---	|---|
|1|0|	**Time Protocol**|Time included|
|00|1 ~ 2|	(Reserved)|For future use|
|0|3|	Encrypted|Packet is encrypted|
|1|4|	**MAC**| MAC-Address field included|
|0|5|	Capability|Capability field included|
|1|6|	**Object**|Object fields are included|
|00|7 ~ 8|	(Reserved)|
|1|9|	**Binding Confirm**| This is binding confirmation packet|
|0|10|Secure Auth|Secure authentication supported by chip|
|0|11|Secure Login|Symmetric encryption is supported, otherwise, use assymetric encryption|
|1100|12 ~ 15|	**Version**|Device version 

##### Capability field
|Bit number| Field name| Description
|---	|---	|---|
|0|	Connectable|	Device has support to establish connection| 
|1|	Centralable|	Device can be centralized|
|2|	Encryptable|	Device can make encryption|
|3 ~ 4|BondAbility|	Device bonding ability type|
|5 ~ 7|(Reserved)||

Bond abilities are:
```
00 = User selected or by RSSI level
01 = Scan first, device sends ACK packet to bond
10 = Bond immediately after scan, device will confirm by vibration & etc
11 = Dedicated device with combined bonding type 
```
##### Object structure
|Value|Field name|Length|Description|Notice
|---|---|---|---|---|
|00 02|ID|2|Object identifier|0x0200|
|01|Length|1|Object length|1 byte|
|10|Data|N * Length|Object data|0x10|










