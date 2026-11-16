

## 内存堆栈转储

| 地址 | 数值 | 符号 |
|------|------|------|
| 0236eac | 7d61f5ed | ntdll!RtlFreeHeap+0x70f |
| 0236eb0 | 7d61f4ab | ntdll!RtlFreeHeap |
| 0236eb4 | 7d61c91b | ntdll!NtClose |
| 0236eb8 | 00000000 | |
| ... | ... | ... |
| 0236f08 | 00000000 | |
| 0236f0c | 7d621954 | ntdll!RtlImageNtHeaderEx+0xee |
| 0236f10 | 7d64e000 | |
| 0236f14 | 00001000 | |
| 0236f18 | 00000000 | |
| 0236f1c | 00000008 | |
| 0236f20 | 044000e8 | NullThread_enc$txtbss$begin <PERF> (NullThread+0x8e) |
| 0236f24 | 00000000 | |
| 0236f28 | 0236f10 | |
| 0236f2c | 00000000 | |
| 0236f30 | 0236f79c | |
| 0236f34 | 7d61f1f8 | ntdll!_except_handler3 |
| 0236f38 | 7d621954 | ntdll!RtlImageNtHeaderEx+0xee |
| 0236f3c | 00220000 | |
| ... | ... | ... |
| 0236fe8 | 0236eeb0 | |
| 0236fec | 7d61f5ed | ntdll!RtlFreeHeap+0x70f |
| 0236ff0 | 0236f79c | |
| 0236ff4 | 7d61f1f8 | ntdll!_except_handler3 |
| 0236ff8 | 7d61f5f0 | ntdll!CheckHeapFillPattern+0x64 |
| 0236ffc | ffffffff | |
| 0237000 | 7d61f5ed | ntdll!RtlFreeHeap+0x70f |
| 0237004 | 7d4e2183 | kernel32!CreateProcessInternalW+0x21f5 |
| 0237008 | 02220000 | |
| 023700c | 00000000 | |
| 0237010 | 02223910 | |
| 0236f794 | 7d4ebc0b | kernel32!CreateProcessInternalW+0x1f26 |
| 0236f798 | 00000000 | |
| 0236f79c | 00000996 | |
| 0236fa0 | 0236f814 | |
| 0236fa4 | 00000103 | |
| 0236fa8 | 7d64e000 | |
| 0236fac | 00000001 | |
| 0236fb0 | 0236ffc | |
| 0236fb4 | 00000200 | |
| 0236fb8 | 00000c00 | |
| 0236fbc | 0236f0bc | |
| 0236fc0 | 0236febc | |
| 0236fc4 | 7d625f68 | ntdll!bsearch+0x42 |
| 0236fc8 | 00180144 | |
| 0236fcc | 0236e600 | |
| 0236fd0 | 7d625992 | ntdll!ARRAY_FITS+0x29 |
| 0236fd4 | 0000aabc | |
| 0236fd8 | 00000000 | |
| 0236fdc | 00000000 | |
| 0236fe0 | 00080000 | |
| 0236fe4 | 00070000 | |
| 0236fe8 | 00040000 | |
| 0236fec | 00000044 | |
| 0236ff0 | 00000000 | |
| 0236ff4 | 7d535b50 | kernel32! 'string' |
| 0236ff8 | 00000000 | |
| 0236ffc | 00000000 | |
| ... | ... | ... |
| 0236f700 | 00000001 | |
| 0236f704 | 7d625ad8 | ntdll!RtlFindActivationContextSectionString+0xe1 |
| 0236f708 | 004000e8 | NullThread_enc$txtbss$begin <PERF> (NullThread+0x8e) |
| 0236f7c | 0236fcc | |
| 0236f80 | 00000000 | |
| 0236f84 | 7d625e68 | ntdll!bsearch+0x42 |
| 0236f88 | 00180144 | |
| 0236f8c | 0236f0a0 | |
| 0236f90 | 7d625992 | ntdll!ARRAY_FITS+0x29 |
| 0236f94 | 0000aabc | |
| ... | ... | ... |
| 0236fd0 | 0236f120 | |
| 0236fd4 | 7d625b62 | ntdll!RtlpFindUnicodeStringInSection+0x7b |
| 0236fd08 | 0236f204 | |
| 0236fd0c | 00000020 | |
| ... | ... | ... |
| 0236f190 | 7d625562 | ntdll!RtlpFindUnicodeStringInSection+0x7b |
| 0236f198 | 00000001 | |
| 0236f19c | 00000000 | |
| 0236f1a0 | 0236f1d0 | |
| 0236f1a4 | 7d6257f1 | ntdll!RtlpFindNextActivationContextSection+0x64 |
| 0236f1a8 | 0181f1c1 | |
| ... | ... | ... |
| 0236f1f0 | 7efaf000 | |
| 0236f1f4 | 7d625ad8 | ntdll!RtlFindActivationContextSectionString+0xe1 |
| 0236f1f8 | 0236f214 | |
| 0236f1fc | 0236f24c | |
| 0236f200 | 00000000 | |
| 0236f204 | 7d625e68 | ntdll!bsearch+0x42 |
| 0236f208 | 00180144 | |
| ... | ... | ... |
| 0236f24c | 00000200 | |
| 0236f250 | 00000734 | |
| 0236f254 | 7d625562 | ntdll!RtlpFindUnicodeStringInSection+0x7b |
| 0236f258 | 0236f384 | |
| ... | ... | ... |
| 0236f3f0 | 00000000 | |
| 0236f3f4 | 00000000 | |
| 0236f3f8 | 01034236 | |
| 0236f3fc | 00000000 | |
| 0236f400 | 7d4d5150 | kernel32!BaseProcessStartThunk |
| 0236f404 | 00000018 | |
| 0236f408 | 00003000 | |
| ... | ... | ... |
| 0236f62c | 0236f63c | |
| 0236f630 | 00000001 | |
| 0236f634 | 7d61f645 | ntdll!RtlpFreeToHeapLookaside+0x22 |
| 0236f638 | 00231088 | |
| 0236f63c | 0236f71c | |
| ... | ... | ... |
| 0236f70c | 002333b8 | |
| 0236f710 | 0236f720 | |
| 0236f714 | 00000001 | |
| 0236f718 | 7d61f645 | ntdll!RtlpFreeToHeapLookaside+0x22 |
| 0236f71c | 00228fb0 | |
| 0236f720 | 0236f800 | |
| 0236f724 | 7d61f5d1 | ntdll!RtlFreeHeap+0x20e |
| 0236f728 | 0022f318 | |
| 0236f72c | 7d61f5ed | ntdll!RtlFreeHeap+0x70f |
| 0236f730 | 00000000 | |
| 0236f734 | 00000096 | |
| 0236f738 | 02368814 | |
| 0236f73c | 00220608 | |
| 0236f740 | 7d61f5ed | ntdll!RtlFreeHeap+0x70f |
| 0236f744 | 0236f904 | |
| 0236f748 | 008e0000 | |
| ... | ... | ... |
| 0236f788 | 7d63d275 | |
| 0236f78c | 7d63d275 | ntdll!_vsnwprintf+0x30 |
| 0236f78c | 0236f79c | |
| 0236f790 | 0000f949 | |
| 0236f794 | 0236e098 | |
| 0236f798 | 00000095 | |
| 0236f79c | 0236b07c | |
| 0236f7a0 | 7d48d9c4 | kernel32!_except_handler3 |
| 0236f7a4 | 7d4ded0d | kernel32! 'string'+0xc |
| 0236f7a8 | ffffffff | |
| 0236f7ac | 7d4ebc0b | kernel32!CreateProcessInternalW+0x1f26 |
| 0236f7b0 | 7d4da1a2 | kernel32!CreateProcessW+0x2c |
| 0236f7b4 | 00000000 | |
| ... | ... | ... |
| 0236f7f0 | 0236fb7c | |
| 0236f7f4 | 7d61f1f8 | ntdll!_except_handler3 |
| 0236f7f8 | 7d61d951 | ntdll!NtWaitForMultipleObjects+0x15 |
| 0236f7fc | 7d61c92d | ntdll!NtClose+0x12 |
| 0236f800 | 7d4dbe4f | kernel32!CloseHandle+0x59 |
| 0236f804 | 00000108 | |
| 0236f808 | 0236f8bc | |
| 0236f80c | 7d55b507 | kernel32!UnhandledExceptionFilter+0x815 |
| 0236f810 | 00000108 | |
| 0236f814 | 04300022 | advapi32!_imp__OutputDebugStringW <PERF> (advapi32+0x222) |
| 0236f818 | 005c003a | |
| 0236f81c | 00720050 | |
| ... | ... | ... |
| 0236f8e4 | 0000000e | |
| 0236f8e8 | 7561f5b4 | |
| 0236f8ec | 00440047 | advapi32!CryptDuplicateHash+0x19 |
| 0236f8f0 | 0060d075 | |
| 0236f8f4 | 0073d070 | |
| 0236f8f8 | 006e005c | |
| 0236f8fc | 00770065 | |
| 0236f900 | 00700065 | |
| 0236f904 | 0064002e | |
| 0236f908 | 0070006d | |
| 0236f910 | 0020003b | |
| 0236f914 | 00220071 | |
| 0236f918 | 00000000 | |
| 0236f91c | 00000096 | |
| 0236f920 | 7d44d4a7 | kernel32!DuplicateHandle+0xd0 |
| 0236f924 | 7d44d4a7 | kernel32!DuplicateHandle+0xd0 |
| 0236f928 | 0236f8bc | |
| 0236f92c | 7d55b5cb | kernel32!UnhandledExceptionFilter+0x5f1 |
| 0236f930 | 0236f9f0 | |
| 0236f934 | 00000001 | |
| 0236f938 | 00000000 | |
| 0236f93c | 7d55b543 | kernel32!UnhandledExceptionFilter+0x851 |
| 0236f940 | 00000000 | |
| 0236f944 | 00000000 | |
| 0236f948 | 00000000 | |
| 0236f94c | 0036f95c | |
| 0236f950 | 00000098 | |
| 0236f954 | 000001a2 | |
| 0236f958 | 01c423b0 | |
| 0236f95c | 0236fb84 | |
| 0236f960 | 7d62155b | ntdll!RtlAllocateHeap+0x460 |
| 0236f964 | 7d61f78b | ntdll!RtlAllocateHeap+0xee7 |
| 0236f968 | 00000000 | |
| 0236f96c | 0000008c | |
| 0236f970 | 00000000 | |
| 0236f974 | 7d4d8472 | kernel32!$VfProc_ImageExportDirectory+0x6d4e |
| 0236f978 | 0236fac4 | |
| 0236f97c | 00000044 | |
| 0236f980 | 00000000 | |
| 0236f984 | 7d55b550 | kernel32! 'string' |
| 0236f988 | 00000000 | |
| 0236f98c | 00000000 | |
| 0236f990 | 00000000 | |
| 0236f994 | 00000000 | |
| 0236f998 | 00000000 | |
| 0236f99c | 00000000 | |
| 0236f9a0 | 00000000 | |
| 0236f9a4 | 00000000 | |
| 0236f9a8 | 00000000 | |
| 0236f9ac | 00000000 | |
| 0236f9b0 | 00000000 | |
| 0236f9b4 | 00000000 | |
| 0236f9b8 | 00000000 | |
| 0236f9bc | 00000000 | |
| 0236f9c0 | 0010000e | |
| 0236f9c4 | 77fe030 | SharedUserData+0x30 |
| 0236f9c8 | 000000e8 | |
| 0236f9cc | 00000108 | |
| 0236f9d0 | 00000200 | |
| 0236f9d4 | 00000734 | |
| 0236f9d8 | 00000018 | |
| 0236f9dc | 00000000 | |
| 0236f9e0 | 7d5621d0 | kernel32!ProgramFilesEnvironment+0x74 |
| 0236f9e4 | 00000040 | |
| 0236f9e8 | 00000000 | |
| 0236f9ec | 00000000 | |
| 0236f9f0 | 0000000c | |
| 0236f9f4 | 00000000 | |
| 0236f9f8 | 00000001 | |
| 0236f9fc | 00000118 | |
| 0236fa00 | 000000e8 | |
| 0236fa04 | c0000005 | |
| 0236fa08 | 00000000 | |
| 0236fa0c | 00000008 | |
| 0236fa10 | 00000000 | |
| 0236fa14 | 00000110 | |
| 0236fa18 | 0236f814 | |
| 0236fa1c | 69508784 | <Unloaded_faultrep.dll>+0x878ba |
| 0236fa20 | 00120010 | |
| 0236fa24 | 7d51c5e4 | kernel32! 'string' |
| 0236fa28 | 00000003 | |
| 0236fa2c | 05cb0847 | |
| ... | ... | ... |
| 0236fa74 | 00d0005c | advapi32!szPerflibSectionName <PERF> (advapi32+0x80032) |
| 0236fa78 | 05c00033 | |
| 0236fa80 | 00790073 | |
| ... | ... | ... |
| 0236fac8 | 0000002b | |
| 0236facc | 00000000 | |
| 0236fad0 | 7d61e6d0 | ntdll!ZwWow64CsrNewThread+0x12 |
| 0236fad4 | 00000000 | |
| ... | ... | ... |
| 0236fbf4 | 00000000 | |
| 0236fbf8 | 7d4d89c4 | kernel32!_except_handler3 |
| 0236fbfc | 00000000 | |
| 0236fc00 | 0036fc00 | |
| 0236fc04 | 0236fc18 | |
| 0236fc08 | 7d640ca6 | ntdll!RtlCallVectoredContinueHandlers+0x15 |
| 0236fc0c | 0236fc40 | |
| 0236fc10 | 0236fc40 | |
| 0236fc14 | 7d6a0608 | ntdll!RtlpCallBackEntryList |
| 0236fc18 | 0236fc88 | |
| 0236fc1c | 7d6354c9 | ntdll!RtlDispatchException+0x11f |
| 0236fc20 | 0236fc40 | |
| 0236fc24 | 0236fcf0 | |
| 0236fc28 | 00000000 | |
| 0236fc2c | 00000000 | |
| ... | ... | ... |
| 0236fc88 | 0236ffec | |
| 0236fc8c | 7d61d626 | ntdll!NtRaiseException+0x12 |
| 0236fc90 | 7d61e5a1 | ntdll!KiUserExceptionDispatcher+0x29 |
| 0236fc94 | 0236fc40 | |
| 0236fc98 | 0236fc00 | |
| 0236fc9c | 00000000 | |
| 0236fca0 | c0000005 | |
| 0236fca4 | 00000000 | |
| 0236fca8 | 00000000 | |
| 0236fcac | 00000000 | |
| 0236fcb0 | 00000002 | |
| 0236fcb4 | 00000008 | |
| 0236fcb8 | 00000000 | |
| 0236fcbc | 00000000 | |
| 0236fcc0 | 00000000 | |
| 0236fcc4 | 6b021fa0 | |
| 0236fcc8 | 78d83990 | |
| 0236fccc | 00000000 | |
| 0236fcd0 | 00000000 | |
| 0236fcd4 | 00000000 | |
| 0236fcd8 | 7efa0000 | |
| 0236fcdc | 0236ff80 | |
| 0236fce0 | 023a3f10 | |
| 0236fce4 | 78db3980 | |
| 0236fce8 | 010402e1 | |
| 0236fcec | 00000000 | |
| 0236fcf0 | 0001003f | |
| 0236fcf4 | 00000000 | |
| 0236fcf8 | 00000000 | |
| 0236fcfc | 00000000 | |
| 0236fd00 | 00000000 | |
| 0236fd04 | 00000000 | |
| 0236fd08 | 0000002f | |
| 0236fd10 | 00000000 | |
| 0236fd14 | 0000ffff | |
| 0236fd18 | 00000000 | |
| 0236fd1c | 00000000 | |
| 0236fd20 | 00000000 | |
| 0236fd24 | 00000000 | |
| 0236fd28 | 00000000 | |
| 0236fd2c | 00000000 | |
| 0236fd30 | 00000000 | |
| 0236fd34 | 00000000 | |
| 0236fd38 | 00000000 | |
| 0236fd3c | 00000000 | |
| 0236fd40 | 00000000 | |
| 0236fd44 | 00000000 | |
| 0236fd48 | 00000000 | |
| 0236fd4c | 00000000 | |
| 0236fd50 | 00000000 | |
| 0236fd54 | 00000000 | |
| 0236fd58 | 00000000 | |
| 0236fd5c | 00000000 | |
| 0236fd60 | 00000000 | |
| 0236fd64 | 00000000 | |
| 0236fd68 | 00000000 | |
| 0236fd6c | 00000000 | |
| 0236fd70 | 00000000 | |
| 0236fd74 | 00000000 | |
| 0236fd78 | 00000000 | |
| 0236fd7c | 0000002b | |
| 0236fd80 | 00000053 | |
| 0236fd84 | 0000002b | |
| 0236fd88 | 0000002b | |
| 0236fd8c | 00000000 | |
| 0236fd90 | 00000000 | |
| 0236fd94 | 00000000 | |
| 0236fd98 | 00000000 | |
| 0236fd9c | 47f30000 | |
| 0236fda0 | 00000000 | |
| 0236fda4 | 0236fec | |
| 0236fda8 | 00000000 | |
| 0236fdac | 00000023 | |
| 0236fdb0 | 00010246 | |
| 0236fdb4 | 0236ffbc | |
| 0236fdb8 | 0000002b | |
| 0236fdbb | 0000027f | |
| 0236fdc0 | 00000000 | |
| 0236fdc4 | 00000000 | |
| 0236fdc8 | 00000000 | |
| 0236fdcc | 00000000 | |
| ... | ... | ... |
| 0236fdd0 | 00000000 | |
| 0236fdd4 | 00000000 | |
| 0236fdd8 | 7d4dfe21 | kernel32!BaseThreadStart+0x34 |
| 0236fddc | 00000000 | |
| 0236fde0 | 00000000 | |
| 0236fde4 | 00000000 | |
| 0236fde8 | c0000005 | |
| 0236fdec | 00000000 | |
| 0236fdf0 | 00000005 | |
| 0236fdf4 | 0236ffc4 | |
| 0236fdf8 | 0236fbb4 | |
| 0236fdfc | dfff4ff | |
| 0236fe00 | 7d4d89c4 | kernel32!_except_handler3 |
| 0236fe04 | 7d4fe228 | kernel32!_string+0x18 |
| 0236fe08 | 00000000 | |
| 0236fe0c | 00000000 | |
| 0236fe10 | 00000000 | |
| 0236fe14 | 00000000 | |
| 0236fe18 | 00000000 | |
| 0236fe1c | ???????? |
| 02370000 | ???????? |

## Comments

!DumpStack and !EEStack SOS commands provide a summary of “call type” execution residue from the raw stack.

System Objects can shed extra light on past software behavior (page 971).

We can also use dpS WinDbg command on a range to get all symbolic references only.

