```
```
0:005> dps 10000000+2000 10000000+2000+58
10002000 76376101 gdi32!CreateCompatibleDC
10002004 763793d6 gdi32!StretchBlt
10002008 76377461 gdi32!CreateDIBSection
1000200c 763762a0 gdi32!SelectObject
10002010 00000000
10002014 754e4a11 kernel32!lstrcmpW
10002018 75e440aa kernel32!VirtualFree
1000201c 75e4ad55 kernel32!VirtualAlloc
10002020 00000000
10002024 77429ced user32!ReleaseDC
10002028 77423ba7 user32!NtUserGetWindowDC
1000202c 77430e21 user32!GetWindowRect
10002030 00000000
10002034 744a75e9 GdiPlus!GdiplusStartup
10002038 744976dd GdiPlus!GdipSaveImageToStream
1000203c 744cd38 GdiPlus!GdipGetImageEncodersSize
10002040 744971cf GdiPlus!GdipDisposeImage
10002044 744a8591 GdiPlus!GdipCreateBitmapFromHBITMAP
10002048 744cdbae GdiPlus!GdipGetImageEncoders
1000204c 00000000
10002050 7707d51b ole32!CreateStreamOnHGlobal
10002054 00000000
10002058 00000000
```
```

```
```
0:000> !dh 012a0000
[...]
0 [ ] address [size] of Export Directory
0 [ ] address [size] of Import Directory
0 [ ] address [size] of Resource Directory
0 [ ] address [size] of Exception Directory
0 [ ] address [size] of Security Directory
8000 [ FC] address [size] of Base Relocation Directory
4000 [ 1C] address [size] of Debug Directory
0 [ ] address [size] of Description Directory
0 [ ] address [size] of Special Directory
0 [ ] address [size] of Thread Storage Directory
0 [ ] address [size] of Load Configuration Directory
0 [ ] address [size] of Bound Import Directory
0 [ ] address [size] of Import Address Table Directory
0 [ ] address [size] of Delay Import Directory
0 [ ] address [size] of COR20 Header Directory
0 [ ] address [size] of Reserved Directory
[...]
```
```