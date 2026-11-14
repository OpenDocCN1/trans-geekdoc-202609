![](bbox=[0.123, 0.083, 0.879, 0.206])

![](bbox=[0.123, 0.226, 0.879, 0.336])

Everything looks to be in order. Let's add and modify the following to subtract the RVA offset of 0x4504 to calculate the base address:

```
base_address = hex - 0x4504
text.value = "Leaked address: 0x"+ base_address.toString(16) // Line wrapped below
+ " - urlmon!CSecurityManager::`vftable'";
```

The following is the result on the screen in the browser.

![](bbox=[0.123, 0.48, 0.879, 0.595])

# Building the RVA ROP Chain

Our final effort in this chapter is to use mona.py from corelanc0d3r to generate an RVA ROP chain. Though Mona is available for WinDbg, we will use Immunity Debugger from Immunity Security. With Immunity Debugger attached to IE 11, we execute the following command to generate the ROP chain:

```
!mona rop -m urlmon.dll -cp nonull -rva
```

The following is an example of one of the generated ROP chains for VirtualProtect: