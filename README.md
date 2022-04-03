# ebpf-usb

Heavily based on: https://github.com/gpioblink/ebpf-usb-inspector

## Usage

```
usage: ebpf-usb [-h] [--vendor-id VENDOR_ID] [--product-id PRODUCT_ID] [--out-only] [--in-only] [--truncate]

Monitor USB traffic using eBPF

options:
  -h, --help            show this help message and exit
  --vendor-id VENDOR_ID, -v VENDOR_ID
                        The vendor id, expressed in hex
  --product-id PRODUCT_ID, -p PRODUCT_ID
                        The product id, expressed in hex
  --out-only, -o        Filter out all incoming messages
  --in-only, -i         Filter out all outgoing messages
  --truncate, -t        Truncate hexdump buffer outputs to their actual length
```

## Example output

```
Starting capture [VID=unspecified and PID=unspecified]
1: 0403:6014 [0x00 IN] (CONTROL) actual length = 2, buffer length = 2
<GET_STATUS> wValue: 0x0000 wIndex: 0x0000 Dir=IN Type=Standard Recipient=Device
00000000: 00 00                                             ..

2: 0403:6014 [0x00 OUT] (CONTROL) actual length = 0, buffer length = 0
<GET_STATUS> wValue: 0x0000 wIndex: 0x0000 Dir=OUT Type=Vendor Recipient=Device

3: 0403:6014 [0x00 OUT] (CONTROL) actual length = 0, buffer length = 0
<SET_FEATURE> wValue: 0x4138 wIndex: 0x0000 Dir=OUT Type=Vendor Recipient=Device

4: 0403:6014 [0x00 OUT] (CONTROL) actual length = 0, buffer length = 0
<GET_STATUS> wValue: 0x0000 wIndex: 0x0000 Dir=OUT Type=Vendor Recipient=Device

5: 0403:6014 [0x00 OUT] (CONTROL) actual length = 0, buffer length = 0
<SET_INTERFACE> wValue: 0x0000 wIndex: 0x0000 Dir=OUT Type=Vendor Recipient=Device

...

34: 0c45:652f [0x00 IN] (CONTROL) actual length = 66, buffer length = 66
00000000: 09 02 42 00 02 01 00 A0  C8 09 04 00 00 01 03 01  ..B.............
00000010: 01 00 09 21 11 01 00 01  22 4F 00 07 05 81 03 08  ...!...."O......
00000020: 00 01 09 04 01 00 02 03  01 02 00 09 21 11 01 00  ............!...
00000030: 01 22 70 00 07 05 82 03  40 00 01 07 05 03 03 40  ."p.....@......@
00000040: 00 01                                             ..

35: 0c45:652f [0x00 IN] (CONTROL) actual length = 4, buffer length = 255
00000000: 04 03 09 04 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000010: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000040: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000050: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000060: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000070: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000080: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000090: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000A0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000B0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000C0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000D0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000E0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000F0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00     ...............

36: 0c45:652f [0x00 IN] (CONTROL) actual length = 22, buffer length = 255
00000000: 16 03 55 00 53 00 42 00  20 00 44 00 45 00 56 00  ..U.S.B. .D.E.V.
00000010: 49 00 43 00 45 00 00 00  00 00 00 00 00 00 00 00  I.C.E...........
00000020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000040: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000050: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000060: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000070: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000080: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000090: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000A0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000B0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000C0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000D0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000E0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000F0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00     ...............

37: 0c45:652f [0x00 IN] (CONTROL) actual length = 12, buffer length = 255
00000000: 0C 03 53 00 4F 00 4E 00  69 00 58 00 00 00 00 00  ..S.O.N.i.X.....
00000010: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000040: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000050: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000060: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000070: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000080: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
00000090: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000A0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000B0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000C0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000D0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000E0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
000000F0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00     ...............

38: 0c45:652f [0x00 OUT] (CONTROL) actual length = 0, buffer length = 0

39: 0c45:652f [0x00 OUT] (CONTROL) actual length = 0, buffer length = 0

40: 0c45:652f [0x00 IN] (CONTROL) actual length = 79, buffer length = 79
00000000: 05 01 09 06 A1 01 05 07  19 E0 29 E7 15 00 25 01  ..........)...%.
00000010: 75 01 95 08 81 02 95 01  75 08 81 01 95 05 75 01  u.......u.....u.
00000020: 05 08 19 01 29 05 91 02  95 01 75 03 91 01 95 06  ....).....u.....
00000030: 75 08 15 00 26 FF 00 05  07 19 00 2A FF 00 81 00  u...&......*....
00000040: 05 0C 09 00 15 80 25 7F  95 40 75 08 B1 02 C0     ......%..@u....

```