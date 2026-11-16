76e8d65d-76e8d661 5 bytes - user32!MessageBoxExW (+0x8a)
[ 8b ff 55 8b ec:e9 9e 29 00 09 ]
Total bytes compared: 422527(100%)
Number of errors: 70
70 errors : !user32 (76e3d6f8-76e8d661)

0:000> u EnumDisplayDevicesW
user32!EnumDisplayDevicesW:
76e3ba5b 8bff            mov edi,edi
76e3ba5d 55              push ebp
76e3ba5e 8bec            mov ebp,esp
76e3ba60 81ec54030000    sub esp,354h
76e3ba66 a1c990e976      mov eax,dword ptr [user32!__security_cookie (76e990c0)]
76e3ba6b 33c5            xor eax,ebp
76e3ba6d 8945fc          mov dword ptr [ebp-4],eax
76e3ba70 53              push ebx

# Expected behavior

0:000> !chkimg -lo 50 -d !user32 -v
Searching for module with expression: !user32
Will apply relocation fixups to file used for comparison
Will ignore NOP/LOCK errors
Will ignore patched instructions
Image specific ignores will be applied
Comparison image path: c:\mss\user32.dll\49E0380E9d000\user32.dll
No range specified

Scanning section: .text
Size: 422527
Range to scan: 76e31000-76e9827f
76e39c11-76e39c15 5 bytes - user32!MonitorFromPoint
[ 6a 08 68 50 9c:e9 ea 63 10 09 ]
76e3b8ea-76e3b8ee 5 bytes - user32!GetMonitorInfoA (+0x1cd9)
[ 8b ff 55 8b ec:e9 11 47 12 09 ]
76e3ba5b-76e3ba5f 5 bytes - user32!EnumDisplayDevicesW (+0x171)
[ 8b ff 55 8b ec:e9 a0 45 0b 09 ]
76e3d6f8-76e3d6fa 3 bytes - user32!NtUserSetThreadDesktop (+0x1c9d)
[ b8 30 12:e9 03 29 ]
76e3d6fc - user32!NtUserSetThreadDesktop+4 (+0x04)
[ 00:09 ]
76e3dc2a-76e3dc2e 5 bytes - user32!CreateWindowExA (+0x52e)
[ 8b ff 55 8b ec:e9 d1 23 15 09 ]
76e3e7cd-76e3e7d1 5 bytes - user32!SetWindowLongA (+0xba3)
[ 8b ff 55 8b ec:e9 2e 18 03 09 ]
76e3f8f8-76e3f8fc 5 bytes - user32!PostMessageA (+0x112b)
[ 8b ff 55 8b ec:e9 03 07 e7 08 ]
76e41305-76e41309 5 bytes - user32!CreateWindowExW (+0x1a0d)
[ 8b ff 55 8b ec:e9 f6 ec 13 09 ]
76e413b4-76e413b8 5 bytes - user32!SetWindowLongW (+0xaf)
[ 8b ff 55 8b ec:e9 47 ec 03 09 ]
76e41709-76e4170d 5 bytes - user32!MonitorFromRect (+0x355)
[ 6a 08 68 48 17:e9 f2 e8 0e 09 ]
76e435e3-76e435e7 5 bytes - user32!NtUserSetWindowPos (+0x1eda)
[ b8 38 12 00 00:e9 18 ca fe 08 ]