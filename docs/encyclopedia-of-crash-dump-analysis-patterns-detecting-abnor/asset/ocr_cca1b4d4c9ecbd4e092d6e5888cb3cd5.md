```
mscorwks!GetManagedNameForTypeInfo+0xa6e:
7a319e44 mov edx,dword ptr [esp+8]
7a319e8 lea eax,[edx+0Ch]
7a319eeb mov ecx,dword ptr [edx-30h]
7a319eee xor ecx,eax
7a319ef0 call mscorwks!___security_check_cookie (79e72037)
7a319ef5 mov eax,offset mscorwks!_C_T?_R0H@xcx14 (7a319f00)
7a319efa jmp mscorwks!__CxxFrameHandler3 (79f5f258)
```

# Comments

The other way around, when CLR exception is enveloped by unmanaged exception is possible like in ntdebugging blog example 139 .

One of the questions asked: From

```
0012e73c 77f299f7 ntdll!KiUserExceptionDispatcher+0xf
0012e740 0012e750
0012e744 0012e76c
```

Does this correspond to the args for the call to ntdll!RtlDispatchException? If so, is then 0012e76c the 2nd arg to ntdll!RtlDispatchException that is the context record?

A. Yes, it corresponds because it calls it:

```
0:000> ub 77f299f7
ntdll!KiUserCallbackDispatcher+0x42:
77f299e2 ret 0Ch
77f299e5 lea ecx,[ecx]
ntdll!KiUserExceptionDispatcher:
77f299e8 cld
77f299e9 mov ecx,dword ptr [esp+4]
77f299ed mov ebx,dword ptr [esp]
77f299f0 push ecx
77f299f1 push ebx
77f299f2 call ntdll!RtlDispatchException (77f0d132)
```