
# YeeLight YLKG08YL bluetooth dimmer lamp control


### Hardware
Please, look at [Hardware page](ylkg08y-hw.md)


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


### Basic auth procedure

To decrypt messages from remote, we need to know `beacon_key` which is stored in the remote control. 
Application itself must define `token`, it will be used as cipher key in auth procedure.
Device uses MiBeacon V3 encryption protocol.

Device has some BLE characteristics:
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
#### Authentication process
- Send `0x90, 0xCA, 0x85, 0xDE` bytes to authInitCharacteristic. (UUID "0010")
- Subscribe authCharacteristic. (UUID "0001")
- Send cipher(mixA(reversedMac, productID), token) to authCharacteristic. (UUID "0001")
- Now you'll get a notification on authCharacteristic. You must wait for this notification before proceeding to next step. 
  The notification data can be ignored or used to check an integrity, this is optional. 
  If you want to perform a check, compare cipher(mixB(reversedMac, productID), cipher(mixA(reversedMac, productID), res)) 
  where res is received payload with your token, they must equal.
- Send cipher(token, `0x92, 0xAB, 0x54, 0xFA`) to authCharacteristic. (UUID "0010")
- Read from verCharacteristics (UUID "0004") . You can ignore the response data, you just have to perform a read to complete authentication process.

MixA is:
```{reversedMac[0], reversedMac[2], reversedMac[5], (uint8_t)(productId & 0xff), (uint8_t)(productId & 0xff), reversedMac[4], reversedMac[5], reversedMac[1]}```

MixB is:
```{reversedMac[0], reversedMac[2], reversedMac[5], (uint8_t)((productId >> 8) & 0xff),  reversedMac[4],  reversedMac[0], reversedMac[5], (uint8_t)(productId & 0xff)};```

Cipher is a basic RC4 algorithm.

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
1000 1010 0100 1100     Time protocol, Unencrypted, Mac included, Objects included, Binding confirm, Auth=0, Version = 3 
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
|0011|12 ~ 15|	**Version**|Device version 

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
Data is sent via BLE discovery packets. Payload is encrypted:

```
--FC--  -PID-  -CNT- ------ MAC -------  --- ENCRYPTED ---   - CNT -   MIC
0x3058  0x3b6        f8:24:41:c2:44:69  
58 30   b6 03 | e7 | 69 44 c2 41 24 f8 | f9 ee f0 58 51 ee | 01 00 00 | 4c
58 30   b6 03 | e8 | 69 44 c2 41 24 f8 | b0 24 11 25 88 96 | 01 00 00 | fd
58 30   b6 03 | e9 | 69 44 c2 41 24 f8 | 50 11 ac 61 a1 aa | 01 00 00 | dd  
58 30   b6 03 | ea | 69 44 c2 41 24 f8 | 73 d1 18 f0 7f 2e | 01 00 00 | b5   
58 30   b6 03 | eb | 69 44 c2 41 24 f8 | cf af e1 fa 7b df | 01 00 00 | a9 
```

### Payload encryption

For example dicovery packet from YKYL01YL: 
```
       | UUID  | <--- sData --->                                                             | 
 -- -- | -- -- | -FCE- | -PID- | CNT|    -- MAC --      |   -- payload --   |   CNT2   | MIC |
 18 16 | 95 FE | 58 30 | 53 01 | 0C | 1D 01 ED 41 24 F8 | 4D 75 BB F4 81 58 | 04 00 00 | 87  |
 0   1 |  2  3 |  4  5 |  6  7 |  8 |  9 10 11 12 13 14 | 15 16 17 18 19 20 | 21 22 23 | 24  |
 
``````

Let's parse:
Counter = CNT + CNT2 = `0C 04 00 00`  = 0x40c   (Use it to ignore duplicates, incremented on each packet)

Control Field = `58 30` = 0x3058

Product ID = `53 01`  = 0x153

Encrypted Payload = `4D 75 BB F4 81 58`  6 bytes

MIC = 0x87


To decrypt this packet we need to calculate AES key. `beaconKey` has 12 bytes length, but AES key should be 16 bytes, so let's extend it.

`AES_KEY = beaconKey[0..5] + 8D 3D 3C 97 + beaconKey[6..11]`

for example, if `beaconKey = F0 9B BE B9 8C 08 43 8B 8E 84 69 5B`, AES key will be:

`AES_KEY = F0 9B BE B9 8C 08  8D 3D 3C 97  43 8B 8E 84 69 5B`

Nonce for encryption is composed of packet fields:

`Nonce = [ FrameControl + deviceType + frameCounter + reversed mac[0..4] ]`

`Nonce = [ 58 30   53 01   0C 04 00 00   1D 01 ED 41 24 F8` ]

Let's decode
Python code:
```python
  aad = b"\x11"
  token = encrypted_payload[-1:]

  cipher = AES.new(key, AES.MODE_CCM, nonce=nonce, mac_len=4)
  cipher.update(aad)

  decrypted_payload = cipher.decrypt_and_verify(payload, mic)

```

ESP32 code:
```c++
  #define AES_KEY_LENGTH 16
  #define NONCE_LENGTH   13

  uint8_t add = 0x11; // Constant addon
  uint8_t tag[4];

  // Set AES key
  mbedtls_ccm_setkey(&ctx, MBEDTLS_CIPHER_ID_AES, aesKey, AES_KEY_LENGTH * 8);
  mbedtls_ccm_encrypt_and_tag(&ctx, PAYLOAD_LENGTH, nonce, NONCE_LENGTH, &add, 1, PAYLOAD, DECODED_BUFFER, tag, 4);
    
```
I don't know why, but for ESP32's `mbedtls_ccm_auth_decrypt` does not accept 1 byte tag, only 4 bytes. I've tried to
make [MIC 0 0 0], [0 0 0 MIC] and other combination, but this doesn't work. But, if we use encrypt function, it magically
decrypts message. I think this is because of XOR CCM nature. Anyway, we have plaintext message now.

Decrypted message is:
`01 10 03 01 00 00`

Please, refer to [Object structure](#object-structure)

```
01 10     Object identifier 0x1001 
03        Object length     3 bytes
01 00 00  Actual data
```

For YKYL01YL field meaning is:
```
01  - button number (OFF key) 
00  - ???
00  - hold flag, 0x00 - single press, 0x02 - hold
```

You can use [Proof-of-concept app for ESP32](https://github.com/archaron/xiaomi-ble-esp32-ylyk01yl) as strting point

