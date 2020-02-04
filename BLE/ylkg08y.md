
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
|**0x0018**|**00002803-0000-1000-8000-00805f9b34fb**|**0a 00**|**Characteristic**|**[READ, WRITE]**|
|0x0019|00000014-0000-1000-8000-00805f9b34fb|10 d8 99 8c 8e cd 72 9d e4 21 02 8d|Value||
|0x001a|00002901-0000-1000-8000-00805f9b34fb|beaconkey|Characteristic User Description||


```
00000001  authCharacteristic      token           00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  Notify, Write
00000002                          productid       00 00                                                        Read
00000004  verCharacteristics      ver             5c 0b 1f 0a 41 0c 2a b0 39 4b                                Read
00000005                          wificfg         00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00	 Notify, Write
00000007                          eventrule       00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  Write
00000010 authInitCharacteristic   authentication  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  Write
00000013                          sn              ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  Read, Write
00000014                          beaconkey       10 d8 99 8c 8e cd 72 9d e4 21 02 8d                          Read, Write
```

- Send 0x90, 0xCA, 0x85, 0xDE bytes to authInitCharacteristic.
- Subscribe authCharacteristic.
- Send cipher(mixA(reversedMac, productID), token) to authCharacteristic.
- Now you'll get a notification on authCharacteristic. You must wait for this notification before proceeding to next step. The notification data can be ignored or used to check an integrity, this is optional. If you want to perform a check, compare cipher(mixB(reversedMac, productID), cipher(mixA(reversedMac, productID), res)) where res is received payload with your token, they must equal.
- Send 0x92, 0xAB, 0x54, 0xFA to authCharacteristic.
- Read from verCharacteristics. You can ignore the response data, you just have to perform a read to complete authentication process.

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
1000 1010 0100 1100     Time protocol, Mac included, Objects included, Binding confirm, Version = 12 
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





----------
### When turning dimmer
Right

```
--FC--  -PID-  -CNT- ------ MAC -------
0x3058  0x3b6        f8:24:41:c2:44:69
58 30   b6 03 | e7 | 69 44 c2 41 24 f8 | f9 ee f0 58 51 ee 01 | 00 00 | 4c
58 30   b6 03 | e8 | 69 44 c2 41 24 f8 | b0 24 11 25 88 96 01 | 00 00 | fd
58 30   b6 03 | e9 | 69 44 c2 41 24 f8 | 50 11 ac 61 a1 aa 01 | 00 00 | dd  
58 30   b6 03 | ea | 69 44 c2 41 24 f8 | 73 d1 18 f0 7f 2e 01 | 00 00 | b5   
58 30   b6 03 | eb | 69 44 c2 41 24 f8 | cf af e1 fa 7b df 01 | 00 00 | a9 
```
  
Left
```
--FC--  -PID-  -CNT- ------ MAC -------
0x3058  0x3b6        f8:24:41:c2:44:69
58 30   b6 03 | ec | 69 44 c2 41 24 f8 | 8e 94 70 ff ce 5a 01 | 00 00 | 66 
58 30   b6 03 | ed | 69 44 c2 41 24 f8 | 0a 02 0a b9 f1 86 01 | 00 00 | 3f 
58 30   b6 03 | ee | 69 44 c2 41 24 f8 | 91 b2 5e 20 8f 87 01 | 00 00 | 86                      
58 30   b6 03 | ef | 69 44 c2 41 24 f8 | f3 70 a0 16 46 a2 01 | 00 00 | 3a    
58 30   b6 03 | f0 | 69 44 c2 41 24 f8 | 70 72 ec de 2c 62 01 | 00 00 | 78   
58 30   b6 03 | f1 | 69 44 c2 41 24 f8 | ed 60 ee 1e 43 01 01 | 00 00 | e3        
58 30   b6 03 | f2 | 69 44 c2 41 24 f8 | a5 9d bc c7 42 bd 01 | 00 00 | 66    
58 30   b6 03 | f3 | 69 44 c2 41 24 f8 | a7 ba 10 44 ea 59 01 | 00 00 | 7f 
```  
  
Click once
```
--FC--  -PID-  -CNT- ------ MAC -------
0x3058  0x3b6        f8:24:41:c2:44:69
58 30   b6 03 | c1 | 69 44 c2 41 24 f8 | 17 4a bb 49  78 d3 02 | 00 00 | 63           
58 30   b6 03 | c2 | 69 44 c2 41 24 f8 | af 66 33 a4  96 58 02 | 00 00 | 82           
58 30   b6 03 | c3 | 69 44 c2 41 24 f8 | 8d 3d 6c 1b  a7 a5 02 | 00 00 | f4           
58 30   b6 03 | c4 | 69 44 c2 41 24 f8 | ca 72 77 53  6c 90 02 | 00 00 | 47           
58 30   b6 03 | c5 | 69 44 c2 41 24 f8 | ec 53 5f 58  b2 f3 02 | 00 00 | cb           
58 30   b6 03 | c6 | 69 44 c2 41 24 f8 | 50 71 f5 26  7a 5a 02 | 00 00 | 7d

```
Click twice
```
--FC--  -PID-  -CNT- ------ MAC -------
0x3058  0x3b6        f8:24:41:c2:44:69
58 30   b6 03 | 2f | 69 44 c2 41 24 f8 | 47 c1 69 a7 cb 62 03 | 00 00 | 82           
58 30   b6 03 | 30 | 69 44 c2 41 24 f8 | d1 18 63 e9 f2 ea 03 | 00 00 | bc           
58 30   b6 03 | 31 | 69 44 c2 41 24 f8 | f4 b1 e4 37 44 00 03 | 00 00 | f5           
58 30   b6 03 | 32 | 69 44 c2 41 24 f8 | d0 17 96 67 a3 7a 03 | 00 00 | e9           
58 30   b6 03 | 33 | 69 44 c2 41 24 f8 | da ec 11 83 12 ea 03 | 00 00 | 95           
58 30   b6 03 | 34 | 69 44 c2 41 24 f8 | f2 e1 87 93 df 3a 03 | 00 00 | 04           
58 30   b6 03 | 35 | 69 44 c2 41 24 f8 | 14 dd 64 da e9 21 03 | 00 00 | af           

```


One step left - one step right
```
58 30   b6 03 |  00  | 69 44 c2 41 24 f8  | 45 18 1e 80 8c 8a | 05 | 00 00 | 9b
58 30   b6 03 |  01  | 69 44 c2 41 24 f8  | 02 19 74 dc 7c d0 | 05 | 00 00 | 9c
58 30   b6 03 |  02  | 69 44 c2 41 24 f8  | 23 38 b0 b8 0b 7f | 05 | 00 00 | e0
58 30   b6 03 |  03  | 69 44 c2 41 24 f8  | 02 27 33 7e ce 23 | 05 | 00 00 | f5
58 30   b6 03 |  04  | 69 44 c2 41 24 f8  | 24 d4 3e e1 1b 6c | 05 | 00 00 | c1
58 30   b6 03 |  05  | 69 44 c2 41 24 f8  | a6 b3 9c 2c b5 3d | 05 | 00 00 | 7a
58 30   b6 03 |  06  | 69 44 c2 41 24 f8  | e2 28 9f 47 fd d4 | 05 | 00 00 | ab
58 30   b6 03 |  07  | 69 44 c2 41 24 f8  | 44 db 87 19 20 77 | 05 | 00 00 | 42
58 30   b6 03 |  08  | 69 44 c2 41 24 f8  | ab 1a f8 66 eb 98 | 05 | 00 00 | 5f
58 30   b6 03 |  09  | 69 44 c2 41 24 f8  | c3 b7 46 51 9d 90 | 05 | 00 00 | 6c
```
0x3058 => 
0 ...............15
0001 1010 0000 1100     Mac included, Objects included, Version = 12
```


 