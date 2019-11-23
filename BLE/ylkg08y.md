
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















