```
uart ok
strap pin:0x412b8ae2
enable spi-nand
ROM ver:v1.1, sig:455cc27, time:2016.01.04-18:42+0800, CPU(400 MHz), DDR2(533 MHz)
load efuse ok
init IP ok
rom_progress: 0x0600006d
load_data_from_storage(260): 0xbfe01540, 0x00000000, 0xbfd16f44 
load_data_from_spi_nand_flash(70): 0xbfe01540, 0x00000000, 0xbfe03e18 
check_image_header(72): h(69,72,61,6d), s(69,72,61,6d) 
img sig ok
rom_progress: 0x0c00006d
load_data_from_spi_nand_flash(81) 0x00000004 0x000024ba 
load_data_from_spi_nand_flash(86): 0xbfe01d40, 0x00000001, 0xbfe03e18 
load_data_from_spi_nand_flash(86): 0xbfe02540, 0x00000002, 0xbfe03e18 
load_data_from_spi_nand_flash(86): 0xbfe02d40, 0x00000003, 0xbfe03e18 
load_data_from_spi_nand_flash(86): 0xbfe03540, 0x00000004, 0xbfe03e18 
load_data_from_spi_nand_flash(90) read done (size:9402) 
chksum ok
rom_progress: 0x0e00006d
load img ok
rom_progress: 0x1000006d
jump 0xbfe01550

Booting...
SPI NAND clock not enable

SPI Nand ID=00efaa21
SPI Nand die chipsize=0x08000000 byte
SPI Nand dienum=1,
SPI Nand blocksize=0x00020000 byte,
SPI Nand pagesize=0x00000800 byte,
SPI Nand oobsize=0x00000040 byte,
[rtkn_scan_bbt, line 1812], RBA=51, this->RBA_PERCENT = 5,block_v2r_num=1024
[rtkn_scan_bbt, line 1822] block_v2r_num 00000400
[rtk_scan_v2r_bbt]:678,RBA=00000033,2=00000400,
[rtk_scan_v2r_bbt]:684,block_v2r_num=000003cd
INFO: Stored BBT in Die 0: block=8 , block_status_p1=0x000000bb
load bbt v2r table:0 page:512
[rtk_scan_v2r_bbt] have created v2r bbt table:0 on block 8, just loads it !!
check v2r bbt table:0 OK
[rtk_nand_scan_bbt, line 393] mem_page_num=1 bbt_page 704
INFO: Stored BBT in Die 0: block=11 , block_status_p1=0x000000bb
load bbt table:0 page:704
[rtk_nand_scan_bbt] have created bbt table:0 on block 11, just loads it !!
check bbt table:0 OK
[dump_BBT] Nand BBT Content
Congratulation!! No BBs in this Nand.
=>CPU Wake-up interrupt happen! GISR=09000084 



Realtek RTL8197F boot code at 2019.11.15-19:29+0800 v3.4T-pre2.1 (993MHz)
-- version: 1.0.2.005 --
Info: Load boot_info success!
=== bootloader for mijia_gw ===
boot_info: ver:0
kernel: newest:1, curr:1
rootfs: newest:1, curr:1
kernel[0]: sum:0xe6b8, size:2126852, fail:0
      [1]: sum:0xe880, size:2126852, fail:0
rootfs[0]: sum:0x0e23, size:10215428, fail:0
      [1]: sum:0xa74b, size:7700484, fail:0
root_sum_check: off
watchdog_time: 0
boot_version: 1.0.2.005
priv mode
Info: loading kernel 1 ...  Done
Info: checking kernel 1 ... Success
Info: select rootfs 1
Info: booting...
Jump to image start=0x80a00000...
decompressing kernel:
Uncompressing Linux... done, booting the kernel.
done decompressing kernel.
start address: 0x804fb790
[    0.000000] Linux version 3.10.90 (luobo@compilex64-ipg) (gcc version 4.9.4 20151028 (prerelease) (Realtek MSDK-4.9.4p1 Build 2648) ) #70 Thu Dec 19 19:43:45 CST 2019
[    0.000000] bootconsole [early0] enabled
[    0.000000] CPU revision is: 00019385 (MIPS 24Kc)
[    0.000000] Determined physical RAM map:
[    0.000000]  memory: 04000000 @ 00000000 (usable)
[    0.000000] Zone ranges:
[    0.000000]   Normal   [mem 0x00000000-0x03ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00000000-0x03ffffff]
[    0.000000] Primary instruction cache 64kB, VIPT, 4-way, linesize 32 bytes.
[    0.000000] Primary data cache 32kB, 4-way, PIPT, no aliases, linesize 32 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping off.  Total pages: 4088
[    0.000000] Kernel command line: root=/dev/mtdblock8 console=ttyS0,38400
[    0.000000] PID hash table entries: 256 (order: -4, 1024 bytes)
[    0.000000] Dentry cache hash table entries: 8192 (order: 1, 32768 bytes)
[    0.000000] Inode-cache hash table entries: 4096 (order: 0, 16384 bytes)
[    0.000000] Writing ErrCtl register=0003c55e
[    0.000000] Readback ErrCtl register=0003c55e
[    0.000000] Memory: 58272k/65536k available (5134k kernel code, 7264k reserved, 974k data, 224k init, 0k highmem)
[    0.000000] SLUB: HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:192
[    0.000000] Realtek GPIO IRQ init
[    0.000000] Calibrating delay loop... 660.68 BogoMIPS (lpj=3303424)
[    0.070000] pid_max: default: 32768 minimum: 301
[    0.080000] Mount-cache hash table entries: 2048
[    0.090000] [rtl819x_gpio_pin_enable][277]: mask=0xf00 mux=0x0 mux_reg=0xb8000844 val=0x100,                         CNR_REG=0xffffffbf MUX_REG=0x100
[    0.100000] [rtl819x_gpio_direction_output][150]: set pin38 as output pin, default value=0, DIR_REG=0x40 DAT_REG=0x3000000
[    0.110000] [rtl819x_gpio_pin_enable][277]: mask=0xf0 mux=0x100 mux_reg=0xb8000844 val=0x10,                         CNR_REG=0xffffff3f MUX_REG=0x110
[    0.120000] [rtl819x_gpio_direction_output][150]: set pin39 as output pin, default value=0, DIR_REG=0xc0 DAT_REG=0x3000000
[    0.130000] [rtl819x_gpio_pin_enable][277]: mask=0xf000000 mux=0x0 mux_reg=0xb8000848 val=0x4000000,                         CNR_REG=0xfffffb3f MUX_REG=0x4000000
[    0.140000] [rtl819x_gpio_direction_output][150]: set pin42 as output pin, default value=0, DIR_REG=0x4c0 DAT_REG=0x3000000
[    0.150000] [rtl819x_gpio_pin_enable][277]: mask=0xf00000 mux=0x4000000 mux_reg=0xb8000848 val=0x400000,                     CNR_REG=0xfffff33f MUX_REG=0x4400000
[    0.160000] [rtl819x_gpio_direction_output][150]: set pin43 as output pin, default value=1, DIR_REG=0xcc0 DAT_REG=0x3000800
[    0.170000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000 mux=0x4400000 mux_reg=0xb8000848 val=0x60000,                       CNR_REG=0xffffe33f MUX_REG=0x4460000
[    0.180000] [rtl819x_gpio_direction_output][150]: set pin44 as output pin, default value=1, DIR_REG=0x1cc0 DAT_REG=0x3001800
[    0.190000] [rtl819x_gpio_pin_enable][277]: mask=0xf000 mux=0x4460000 mux_reg=0xb8000848 val=0x6000,                         CNR_REG=0xffffc33f MUX_REG=0x4466000
[    0.200000] [rtl819x_gpio_direction_output][150]: set pin45 as output pin, default value=1, DIR_REG=0x3cc0 DAT_REG=0x3003800
[    0.210000] [rtl819x_gpio_pin_enable][277]: mask=0xf000000 mux=0x11111000 mux_reg=0xb8000820 val=0x6000000,                  CNR_REG=0xffff833f MUX_REG=0x16111000
[    0.220000] [rtl819x_gpio_direction_output][150]: set pin46 as output pin, default value=1, DIR_REG=0x7cc0 DAT_REG=0x3007800
[    0.230000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000000 mux=0x16111000 mux_reg=0xb8000820 val=0x60000000,                        CNR_REG=0xffff033f MUX_REG=0x66111000
[    0.240000] [rtl819x_gpio_direction_output][150]: set pin47 as output pin, default value=0, DIR_REG=0xfcc0 DAT_REG=0x3007800
[    0.250000] [rtl819x_gpio_pin_enable][277]: mask=0xf00000 mux=0x66111000 mux_reg=0xb8000820 val=0x600000,                    CNR_REG=0xfffe033f MUX_REG=0x66611000
[    0.260000] [rtl819x_gpio_direction_output][150]: set pin48 as output pin, default value=1, DIR_REG=0x1fcc0 DAT_REG=0x3017800
[    0.270000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000 mux=0x66611000 mux_reg=0xb8000820 val=0x70000,                      CNR_REG=0xfffc033f MUX_REG=0x66671000
[    0.280000] [rtl819x_gpio_direction_output][150]: set pin49 as output pin, default value=1, DIR_REG=0x3fcc0 DAT_REG=0x3037800
[    0.290000] [rtl819x_gpio_pin_enable][277]: mask=0xf000 mux=0x66671000 mux_reg=0xb8000820 val=0x7000,                        CNR_REG=0xfff8033f MUX_REG=0x66677000
[    0.300000] [rtl819x_gpio_direction_output][150]: set pin50 as output pin, default value=0, DIR_REG=0x7fcc0 DAT_REG=0x3037800
[    0.310000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000000 mux=0x100000 mux_reg=0xb8000824 val=0x20000000,                  CNR_REG=0xfff0033f MUX_REG=0x20100000
[    0.320000] [rtl819x_gpio_direction_output][150]: set pin51 as output pin, default value=1, DIR_REG=0xffcc0 DAT_REG=0x30b7800
[    0.330000] [rtl819x_gpio_pin_enable][277]: mask=0xf000000 mux=0x20100000 mux_reg=0xb8000824 val=0x1000000,                  CNR_REG=0xffe0033f MUX_REG=0x21100000
[    0.340000] [rtl819x_gpio_direction_output][150]: set pin52 as output pin, default value=0, DIR_REG=0x1ffcc0 DAT_REG=0x30b7800
[    0.350000] [rtl819x_gpio_pin_enable][277]: mask=0xf00000 mux=0x21100000 mux_reg=0xb8000824 val=0x0,                         CNR_REG=0xffc0033f MUX_REG=0x21000000
[    0.360000] [rtl819x_gpio_direction_output][150]: set pin53 as output pin, default value=0, DIR_REG=0x3ffcc0 DAT_REG=0x30b7800
[    0.370000] [rtl819x_gpio_pin_enable][277]: mask=0xf000000 mux=0x33320000 mux_reg=0xb8000834 val=0x3000000,                  CNR_REG=0xff40033f MUX_REG=0x33320000
[    0.380000] [rtl819x_gpio_direction_output][150]: set pin55 as output pin, default value=0, DIR_REG=0xbffcc0 DAT_REG=0x30b7800
[    0.390000] NET: Registered protocol family 16
[    0.400000] <<<<<Register PCI Controller>>>>>
[    0.420000] Do MDIO_RESET
[    0.450000] 40MHz
[    0.810000] PCIE ->  Cannot LinkUP
[    0.820000] Realtek GPIO controller driver init
[    0.830000] INFO: initializing i2c devices ...
[    0.840000] INFO: registering sheipa spi device
[    0.860000] bio: create slab <bio-0> at 0
[    0.870000] SCSI subsystem initialized
[    0.880000] INFO: sheipa spi driver register
[    0.890000] INFO: sheipa spi probe
[    0.900000] cfg80211: Calling CRDA to update world regulatory domain
[    0.910000] Switching to clocksource MIPS
[    0.920000] NET: Registered protocol family 2
[    0.930000] TCP established hash table entries: 2048 (order: 0, 16384 bytes)
[    0.950000] TCP bind hash table entries: 2048 (order: -1, 8192 bytes)
[    0.970000] TCP: Hash tables configured (established 2048 bind 2048)
[    0.990000] TCP: reno registered
[    1.000000] UDP hash table entries: 1024 (order: 0, 16384 bytes)
[    1.020000] UDP-Lite hash table entries: 1024 (order: 0, 16384 bytes)
[    1.040000] NET: Registered protocol family 1
[    1.050000] RPC: Registered named UNIX socket transport module.
[    1.070000] RPC: Registered udp transport module.
[    1.080000] RPC: Registered tcp transport module.
[    1.100000] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    1.130000] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.150000] NFS: Registering the id_resolver key type
[    1.160000] Key type id_resolver registered
[    1.170000] Key type id_legacy registered
[    1.190000] NTFS driver 2.1.30 [Flags: R/W DEBUG].
[    1.200000] msgmni has been set to 113
[    1.210000] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 254)
[    1.240000] io scheduler noop registered (default)
[    1.250000] pwm_probe
[    1.260000] add buzzer dev!!!!!!!!!!!!!!!!
[    1.390000] Serial: 8250/16550 driver, 3 ports, IRQ sharing disabled
[    1.410000] serial8250: ttyS0 at MMIO 0x18147000 (irq = 17) is a 16550A
[    1.430000] console [ttyS0] enabled, bootconsole disabled
[    1.430000] console [ttyS0] enabled, bootconsole disabled
[    1.460000] serial8250: ttyS1 at MMIO 0x18147400 (irq = 46) is a 16550A
[    1.480000] serial8250: ttyS2 at MMIO 0x18147800 (irq = 47) is a 16550A
[    1.500000] Realtek GPIO Driver for Flash Reload Default
[    1.520000] Load Kernel firmware information Driver
[    1.530000] id_chain value=efaa219f
[    1.540000] id_chain value=efaa219f
[    1.550000] NAND device: Manufacturer ID: 0xef, Chip ID: 0xaa (Unknown W25M01GV 1G SPI NAND), 128MiB, page size: 2048, OOB size: 64
[    1.590000] [rtkn_scan_bbt, line 1812], RBA=51, this->RBA_PERCENT = 5,block_v2r_num=1024
[    1.610000] [rtkn_scan_bbt, line 1822] block_v2r_num 400
[rtk_scan_v2r_bbt]:678,RBA=33,2=400,
[    1.640000] [rtk_scan_v2r_bbt]:684,block_v2r_num=3cd
[    1.660000] INFO: Stored BBT in Die 0: block=8 , block_status_p1=0xbb
[    1.680000] load bbt v2r table:0 page:512
[rtk_scan_v2r_bbt] have created v2r bbt table:0 on block 8, just loads it !!
check v2r bbt table:0 OK
[rtk_nand_scan_bbt, line 393] mem_page_num=1 bbt_page 704
[    1.740000] INFO: Stored BBT in Die 0: block=11 , block_status_p1=0xbb
[    1.760000] load bbt table:0 page:704
[rtk_nand_scan_bbt] have created bbt table:0 on block 11, just loads it !!
check bbt table:0 OK
[dump_BBT] Nand BBT Content
[    1.810000] Congratulation!! No BBs in this Nand.
[    1.820000] 11 rtkxxpart partitions found on MTD device rtk_nand
[    1.840000] Creating 11 MTD partitions on "rtk_nand":
[    1.870000] Realtek WLAN driver - version 1.7 (2015-10-30)(SVN:Unversioned directory)
[    1.890000] Adaptivity function - version 9.3.4
[    1.910000] Device Name = RTKWiFi0 
[    1.920000] VIF_NUM=9
[    1.930000] MACHAL_version_init
[    1.940000] RFE TYPE =0
[    1.950000] RFE TYPE =0
[    1.950000] RFE TYPE =0
[    1.960000] RFE TYPE =0
[    1.970000] RFE TYPE =0
[    1.980000] RFE TYPE =0
[    1.990000] RFE TYPE =0
[    2.000000] RFE TYPE =0
[    2.010000] RFE TYPE =0
[    2.020000] RFE TYPE =0
[    2.030000] RFE TYPE =0
[    2.030000] lumi_btn_probe reset btn=7
[    2.040000] [rtl819x_gpio_request][42]: pin7
[    2.060000] [rtl819x_gpio_pin_enable][277]: mask=0xf00000 mux=0x13000000 mux_reg=0xb8000800 val=0x600000,                    CNR_REG=0xffffff7f MUX_REG=0x13600000
[    2.100000] [rtl819x_gpio_direction_input][120]: set pin7 as input pin, DIR_REG=0xff000000
[    2.120000] rtl819x_gpio: GPIO7 requests IRQ79
[    2.130000] input: lumi_key as /devices/virtual/input/input0
[    2.150000] i2c /dev entries driver
[    2.160000] [rtl819x_gpio_request][42]: pin57
[    2.180000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000 mux=0x33320000 mux_reg=0xb8000834 val=0x20000,                      CNR_REG=0xfd40033f MUX_REG=0x33320000
[    2.220000] [rtl819x_gpio_direction_output][150]: set pin57 as output pin, default value=1, DIR_REG=0x2bffcc0 DAT_REG=0x30b7800
[    2.250000] rtl819x_gpio: GPIO57 requests IRQ129
[    2.260000] [rtl819x_gpio_request][42]: pin56
[    2.280000] [rtl819x_gpio_pin_enable][277]: mask=0xf00000 mux=0x33320000 mux_reg=0xb8000834 val=0x300000,                    CNR_REG=0xfc40033f MUX_REG=0x33320000
[    2.320000] [rtl819x_gpio_direction_output][150]: set pin56 as output pin, default value=1, DIR_REG=0x3bffcc0 DAT_REG=0x30b7800
[    2.350000] rtl819x_gpio: GPIO56 requests IRQ128
[    2.370000] [rtl819x_gpio_request][42]: pin54
[    2.380000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000000 mux=0x33320000 mux_reg=0xb8000834 val=0x30000000,                        CNR_REG=0xfc00033f MUX_REG=0x33320000
[    2.420000] [rtl819x_gpio_direction_output][150]: set pin54 as output pin, default value=0, DIR_REG=0x3fffcc0 DAT_REG=0x30b7800
[    2.450000] rtl819x_gpio: GPIO54 requests IRQ126
[    2.470000] TCP: cubic registered
[    2.480000] NET: Registered protocol family 10
[    2.500000] sit: IPv6 over IPv4 tunneling driver
[    2.510000] NET: Registered protocol family 17
[    2.520000] Key type dns_resolver registered
[    2.540000] 
[    2.540000] Probing RTL819X NIC-kenel stack size order[0]...
[    3.230000] eth0 added. vid=9 Member port 0x110...
[    3.250000] eth1 added. vid=8 Member port 0x0...
[    3.280000] VFS: Mounted root (squashfs filesystem) readonly on device 31:8.
[    3.300000] Freeing unused kernel memory: 224K (805f8000 - 80630000)
init started: BusyBox v1.22.1 (2019-12-11 10:29:46 CST)
[    4.250000] WlanSupportAbility = 0x3
[    4.260000] [ODM_software_init] 
[    4.260000] [97F] Bonding Type 97FS, PKG1
[    4.260000] [97F] RFE type 0 PHY paratemters: DEFAULT
[    4.260000] clock 40MHz
[    4.260000] load efuse ok
[    4.260000] rom_progress: 0x200006f
[    4.260000] rom_progress: 0x400006f
[    4.330000] [GetHwReg88XX][PHY_REG_PG_8197Fmp_Type0] size
[    4.350000] [GetHwReg88XX][PHY_REG_PG_8197Fmp_Type0]
[    4.570000] [GetHwReg88XX][rtl8197Ffw]
[    4.580000] [GetHwReg88XX][rtl8197Ffw size]
[    5.020000] [97F] Default BB Swing=30
[    5.100000] device eth0 entered promiscuous mode
[    5.120000] device wlan0 entered promiscuous mode
[    5.130000] br0: port 2(wlan0) entered forwarding state
[    5.150000] br0: port 2(wlan0) entered forwarding state
=== Linux Firmware ===
version=1.4.5_0005
branch=aqara-rtl8197-gateway
try mount ubi0!!!
test for jacky![    5.230000] UBI: attaching mtd10 to ubi0

[    6.560000] UBI: scanning is finished
[    6.600000] UBI: attached mtd10 (name "AppData", size 56 MiB) to ubi0
[    6.620000] UBI: PEB size: 131072 bytes (128 KiB), LEB size: 126976 bytes
[    6.640000] UBI: min./max. I/O unit sizes: 2048/2048, sub-page size 2048
[    6.660000] UBI: VID header offset: 2048 (aligned 2048), data offset: 4096
[    6.680000] UBI: good PEBs: 449, bad PEBs: 0, corrupted PEBs: 0
[    6.700000] UBI: user volume: 1, internal volumes: 1, max. volumes count: 128
[    6.720000] UBI: max/mean erase counter: 5/2, WL threshold: 4096, image sequence number: 2321051527
[    6.750000] UBI: available PEBs: 0, total reserved PEBs: 449, PEBs reserved for bad PEB handling: 20
[    6.780000] UBI: background thread "ubi_bgt0d" started, PID 920
UBI device number 0, total 449 L[    6.820000] UBIFS: parse sync
EBs (57012224 bytes, 54.4 MiB), available 0 LEBs (0 bytes), LEB size 126976 bytes (124.0 KiB)
[    6.930000] UBIFS: background thread "ubifs_bgt0_0" started, PID 927
[    7.050000] UBIFS: recovery needed
[    7.470000] UBIFS: recovery completed
[    7.480000] UBIFS: mounted UBI device 0, volume 0, name "ubifs1"
[    7.500000] UBIFS: LEB size: 126976 bytes (124 KiB), min./max. I/O unit sizes: 2048 bytes/2048 bytes
[    7.530000] UBIFS: FS size: 52695040 bytes (50 MiB, 415 LEBs), journal size 2666496 bytes (2 MiB, 21 LEBs)
[    7.560000] UBIFS: reserved for root: 2488917 bytes (2430 KiB)
[    7.570000] UBIFS: media format: w4/r0 (latest is w4/r0), UUID A4D89DCD-EB3E-4200-93D1-376831EFC616, small LPT model
[    7.670000] [rtl819x_gpio_request][42]: pin18
[    7.680000] [rtl819x_gpio_pin_enable][277]: mask=0xf00 mux=0x455000 mux_reg=0xb8000808 val=0x600,                    CNR_REG=0xfffbff7f MUX_REG=0x455600
[    7.720000] rtl819x_gpio: GPIO18 requests IRQ90
[    7.740000] [rtl819x_gpio_direction_output][150]: set pin18 as output pin, default value=0, DIR_REG=0xff040000 DAT_REG=0x40080
[    7.780000] [rtl819x_gpio_request][42]: pin9
[    7.790000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000 mux=0x455600 mux_reg=0xb8000808 val=0xa0000,                        CNR_REG=0xfffbfd7f MUX_REG=0x4a5600
[    7.830000] rtl819x_gpio: GPIO9 requests IRQ81
[    7.850000] [rtl819x_gpio_direction_output][150]: set pin9 as output pin, default value=0, DIR_REG=0xff040200 DAT_REG=0x40080
MAC=5C:E5:0C:C3:EF:91
[    8.080000] [rtl819x_gpio_request][42]: pin31
[    8.100000] [rtl819x_gpio_pin_enable][277]: mask=0xf0 mux=0x22220077 mux_reg=0xb800083c val=0x70,                    CNR_REG=0x7ffbfd7f MUX_REG=0x22220077
[    8.280000] rtl819x_gpio: GPIO31 requests IRQ103
[    8.290000] [rtl819x_gpio_direction_output][150]: set pin31 as output pin, default value=0, DIR_REG=0xff040200 DAT_REG=0x40280
=== RootFS Firmware ===
product=aqara-rtl8197-gateway
branch=develop
VERSION=1.4.5_0005
version=1.4.5_0005
== 10 == factory test failed, can not run apps!!!!
== 9 == factory test failed, can not run apps!!!!
factory_test bulid time:19:44:24 Dec 19 2019
file=/var/device_config,did=317075222
key=VVugcamk46UWSVLg
mac=54:EF:44:00:57:B9
vendor=lumi
model=lumi.gateway.mgl03
check did 317075222
cat: can't open '/device.conf': No such file or directory
cp: can't create '/device.conf': Read-only file system
get_factory_result=1
gobal_cmd_list size 4804
factory_dir:/data/factory!
miio_dir:/data/miio!conf_dir:/data/conf!
version_file:/etc/rootfs_fw_info!
ble uart port: 1
zigbee uart port: 2
homekit i2c port: 1
factory udp_init!
Input cmd:[    9.670000] store_tty0_enable buf=disable
[    9.670000] , count=8
[   10.410000] br0: port 2(wlan0) entered disabled state
[   10.430000] WlanSupportAbility = 0x3
[   10.440000] [ODM_software_init] 
[   10.440000] [97F] Bonding Type 97FS, PKG1
[   10.440000] [97F] RFE type 0 PHY paratemters: DEFAULT
[   10.440000] clock 40MHz
[   10.440000] load efuse ok
[   10.440000] rom_progress: 0x200006f
[   10.440000] rom_progress: 0x400006f
[   10.520000] [GetHwReg88XX][PHY_REG_PG_8197Fmp_Type0] size
[   10.530000] [GetHwReg88XX][PHY_REG_PG_8197Fmp_Type0]
[   10.750000] [GetHwReg88XX][rtl8197Ffw]
[   10.760000] [GetHwReg88XX][rtl8197Ffw size]
[   11.210000] [97F] Default BB Swing=30
[   11.220000] br0: port 2(wlan0) entered forwarding state
[   11.230000] br0: port 2(wlan0) entered forwarding state
[   12.350000] [rtl819x_gpio_request][42]: pin36
[   12.360000] [rtl819x_gpio_pin_enable][277]: mask=0xf0000 mux=0x0 mux_reg=0xb8000844 val=0x10000,                     CNR_REG=0xfc00032f MUX_REG=0x10000
[   12.400000] rtl819x_gpio: GPIO36 requests IRQ108
[   12.420000] [rtl819x_gpio_direction_output][150]: set pin36 as output pin, default value=0, DIR_REG=0x3fffcd0 DAT_REG=0x3083800
[   12.870000] br0: port 2(wlan0) entered disabled state
[   12.890000] WlanSupportAbility = 0x3
[   12.900000] [ODM_software_init] 
[   12.900000] [97F] Bonding Type 97FS, PKG1
[   12.900000] [97F] RFE type 0 PHY paratemters: DEFAULT
[   12.900000] clock 40MHz
[   12.900000] load efuse ok
[   12.900000] rom_progress: 0x200006f
[   12.900000] rom_progress: 0x400006f
[   12.970000] [GetHwReg88XX][PHY_REG_PG_8197Fmp_Type0] size
[   12.990000] [GetHwReg88XX][PHY_REG_PG_8197Fmp_Type0]
[   13.210000] [GetHwReg88XX][rtl8197Ffw]
[   13.220000] [GetHwReg88XX][rtl8197Ffw size]
[   13.670000] [97F] Default BB Swing=30
[   13.680000] br0: port 2(wlan0) entered forwarding state
[   13.690000] br0: port 2(wlan0) entered forwarding state
[   17.600000] i2c_designware i2c_designware.1: i2c_dw_handle_tx_abort: slave address not acknowledged (7bit mode)
[   20.580000] br0: port 2(wlan0) entered disabled state
[   22.200000] br0: port 2(wlan0) entered forwarding state
[   22.220000] br0: port 2(wlan0) entered forwarding state
[   32.240000] br0: port 2(wlan0) entered forwarding state
[   34.910000] i2c_designware i2c_designware.1: i2c_dw_handle_tx_abort: slave address not acknowledged (7bit mode)
```