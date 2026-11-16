```
76e440c5-76e440c9 5 bytes - user32!EnumDisplaySettingsExW (+0xae2)
[ 8b ff 55 8b ec:e9 36 bf 06 09 ]
76e41a1-76e41a15 5 bytes - user32!EnumDisplaySettingsW (+0xdc)
[ 8b ff 55 8b ec:e9 5a be 08 09 ]
76e46d4a-76e46d4e 5 bytes - user32!EnumDisplayDevicesA (+0x2ba9)
[ 8b ff 55 8b ec:e9 b1 92 0b 09 ]
76e46fe6-76e46fea 5 bytes - user32!EnumDisplaySettingsA (+0x29c)
[ 8b ff 55 8b ec:e9 15 90 09 09 ]
76e47010-76e47014 5 bytes - user32!EnumDisplaySettingsExA (+0x2a)
[ 8b ff 55 8b ec:e9 bf 07 09 ]
76e47d12-76e47d16 5 bytes - user32!GetMonitorInfoW (+0xd02)
[ 8b ff 55 8b ec:e9 e9 82 10 09 ]
76e48343-76e48347 5 bytes - user32!PeekMessageA (+0x631)
[ 8b ff 55 8b ec:e9 b8 7c e8 08 ]
76e4844c-76e48450 5 bytes - user32!NtUserEnumDisplayMonitors (+0x109)
[ b8 81 11 00 00:e9 af 7b 0c 09 ]
76e488d4-76e488d8 5 bytes - user32!MonitorFromWindow (+0x488)
[ 6a 08 d8 68 28 89:e9 27 77 0d 09 ]
76e48ab3-76e48ab7 5 bytes - user32!GetMessageA (+0x1df)
[ 8b ff 55 8b ec:e9 48 75 ea 08 ]
76e49994-76e49998 5 bytes - user32!GetWindowLongA (+0xee1)
[ 6a 08 68 d0 99:e9 67 66 00 09 ]
76e49af1-76e49af5 5 bytes - user32!GetSystemMetrics (+0x15d)
[ 6a 0c 68 58 9b:e9 0a 65 12 09 ]
76e41a75-76e41a79 5 bytes - user32!PostMessageW (+0x684)
[ 8b ff 55 8b ec:e9 86 5e e5 08 ]
76e4f8bf-76e4f8c3 5 bytes - user32!GetWindowLongW (+0x574a)
[ 6a 08 68 00 f9:e9 3c 07 01 09 ]
76e4fef7-76e4fefb 5 bytes - user32!GetMessageW (+0x638)
[ 8b ff 55 8b ec:e9 04 01 e9 08 ]
76e5045a-76e5045e 5 bytes - user32!PeekMessageW (+0x563)
[ 8b ff 55 8b ec:e9 a1 fb e6 08 ]
76e8d37d-76e8d381 5 bytes - user32!MessageBoxTimeoutW (+0x3cf23)
[ 8b ff 55 8b ec:e9 7e 2c ea 08 ]
76e84df9-76e84dfd 5 bytes - user32!MessageBoxIndirectA (+0x15c)
[ 8b ff 55 8b ec:e9 22 2b ec 08 ]
76e85dd3-76e85dd7 5 bytes - user32!MessageBoxIndirectW (+0xfa)
[ 8b ff 55 8b ec:e9 28 2a eb 08 ]
76e8d65d-76e8d661 5 bytes - user32!MessageBoxExW (+0x8a)
[ 8b ff 55 8b ec:e9 9e 29 ed 08 ]
Total bytes compared: 422527(100%)
Number of errors: 154
154 errors : !user32 (76e39c11-76e8d661)
```

```
0:000> u EnumDisplayDevicesW
user32!EnumDisplayDevicesW:
76e3ba5b e90a450b09    jmp 7fef0000
76e3ba60 81ec54030000    sub esp,354h
76e3ba66 a1c090e976    mov eax,dword ptr [user32!__security_cookie (76e990c0)]
76e3ba6b 33c5    xor eax,ebp
76e3ba6d 8945fc    mov dword ptr [ebp-4],eax
76e3ba70 53 push    ebx
76e3ba71 56 push    esi
76e3ba72 8b7510 mov esi,dword ptr [ebp+10h]
```