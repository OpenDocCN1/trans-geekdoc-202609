Now we can try to interpret every double word as a pointer to a Unicode string:

```
0:000> dpu 00249000 00250000
...
```

There are no strings with ".dll" inside. Finally, if we try to interpret every double word as a pointer to an ASCII string we get a few references to "AppService.dll":

```
0:000> dpa 00249000 00250000
...
0024f1d0 76f00000 "MZ."
0024f1d4 7fbd2a5d
0024f1d8 0024f1e8 ""
0024f1dc 76fb8e8f ".-t.-E."
0024f1e0 6ecb940 "AppService.dll"
0024f1e4 0024f21c $"
0024f1e8 0024f200 ""
0024f1ec 6ec74e2a ".^.-.]..".
0024f1f0 6ecb940 "AppService.dll"
0024f1f4 6ecb9ff0 "CreateServiceInstance"
0024f1f8 0024f260 "..$"
0024f1fc 6eb1081e ".].....e."
0024f200 0c6d007f
0024f204 00000000
0024f208 00000001
0024f20c 0024f268 "..$"
0024f210 00000000
0024f214 0024f2c8 "...n .n.<.$"
0024f218 6ece220 ""
0024f21c 00000024
0024f220 6ecb9960 ".,"
0024f224 6eceb95c ".c..n.2.n"
0024f228 6ecb940 "AppService.dll"
0024f22c 00000001
0024f230 6ecb9ff0 "CreateServiceInstance"
0024f234 ffffffff
0024f238 00000000
```

If we search for 0024f1e0 pointer in dps WinDbg command output we would see that it is in the close proximity to RaiseException call and it seems that all our pointers to "AppService.dll" string fall into AppNativeLib address range:

```
0024f1b4 76f442eb kernel32!RaiseException+0x58
0024f1b8 00000001
0024f1bc 0024f21c
0024f1c0 00000000
0024f1c4 00000000
0024f1c8 00000000
0024f1cc 00000000
0024f1d0 76f00000 kernel32!_imp__aullrem (kernel32+0x0)
0024f1d4 7fbd2a5d
0024f1d8 0024f1e8
0024f1dc 76fb8e8f kernel32!LookupHandler+0x10
0024f1e0 6ecb9b40 AppNativeLib!ShutdownSingletonMgr+0x15b024
0024f1e4 0024f21c
```