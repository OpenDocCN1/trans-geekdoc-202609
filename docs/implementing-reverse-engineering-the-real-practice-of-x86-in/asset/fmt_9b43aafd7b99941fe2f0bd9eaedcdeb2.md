
```
[ESP+0x2C] 0012FF40  13789938  XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B  ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.19.jpg)

### Figure 11.19: Old ESI value is preserved

## Line 32-44

```
; Line 8
xor esi, esi
mov DWORD PTR _iArray$[esp+48], esi
mov DWORD PTR _iArray$[esp+52], 1
mov DWORD PTR _iArray$[esp+56], 2
mov DWORD PTR _iArray$[esp+60], 3
mov DWORD PTR _iArray$[esp+64], 4
mov DWORD PTR _iArray$[esp+68], 5
mov DWORD PTR _iArray$[esp+72], 6
mov DWORD PTR _iArray$[esp+76], 7
mov DWORD PTR _iArray$[esp+80], 8
mov DWORD PTR _iArray$[esp+84], 9
npad 3
```

Line 8 of the C/C++ code initializes `iArray`:
`int iArray[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};`

In the ASM code, the `XOR` instruction resets the `ESI` register to `0x00` and then moves `ESI` to the `[ESP+0x04]` location as the first element of `iArray`. All the other `MOV` instructions push the remaining elements of `iArray` on the stack.

We see the `npad` macro, which inserts the non-destructive and non-operational instructions rather than a series of NOP instructions. `Npad 3` corresponds to `lea ecx, [ecx+00]`. For more details related to `npad`, refer to the Appendix. The stack state immediately after the `npad` macro is as follows:

```
[ESP]  0012FF14  00000000   old ESI value is preserved here
[ESP+0x04] 0012FF18  00000000   iArray first element pushed here
[ESP+0x08] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x0C] 0012FF20  00000002   iArray third element pushed here
[ESP+0x010] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x014] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x18] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x1C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x20] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x24] 0012FF38  00000008   iArray ninth element pushed here
[ESP+0x28] 0012FF3C  00000009   iArray tenth element pushed here
[ESP+0x2C] 0012FF40  13789938   XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B   ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.20.jpg)

### Figure 11.20: The stack state after npad

## Line 45-55

```
$LL3@main:
; Line 12
mov eax, DWORD PTR _iArray$[esp+esi*4+48]
push eax
push esi
push OFFSET $SG4682
call _printf
inc esi
add esp, 12     ; 0000000cH
cmp esi, 10     ; 0000000aH
jl SHORT $LL3@main
```

Line 12 of the C/C++ code prints the elements of `iArray` along with the index on the screen.
`printf ("iArray[%d]=%d\n", iLoop, iArray[iLoop]);`

This same concept was discussed in the previous section without optimization. The `printf` function takes three arguments to the print `iArray` elements and indexes on the screen. So, all these three arguments need to be pushed onto the stack before the call to the `printf` function.

In the ASM code, the first argument to be pushed on the stack will be `iArray[iLoop]`. To push this value on the stack, the `iLoop` value stored in the `ESI` register is multiplied by 4 (the size of the integer) and then added to the `_iArray$` macro and offset of 48 bytes to calculate the memory location of the element stored for the particular `iLoop` value. So, during the first iteration when the `iLoop` stored at `ESI` = 0, the first `MOV` instruction will result in:
`mov eax, DWORD PTR _iArray$[esp+esi*4+48]`
`mov eax, dword ptr ss:[esp+esi*4+0x4], as ESI = 0`
`mov eax, dword ptr ss:[esp+0x4]`

This will give us the value of the first array element in the `EAX` register. So, by pushing `EAX` onto the stack, we pushed the first argument to `printf` onto the stack.

The next argument to `printf` is the `iLoop` value. It is pushed onto the stack by pushing the `ESI` register.

Last argument, which is string constant is pushed by `push OFFSET $SG4682`.

Now that the three arguments are on the stack, a call to `printf` is made. Stack at this point in time is as follows:

```
[ESP]  0012FF08  00408140   "iArray[%d]=%d\n", string argument to printf
[ESP+0x04] 0012FF0C  00000000   iLoop value, ESI is pushed as printf argument
[ESP+0x08] 0012FF10  00000000   iArray first element is pushed as printf argument
[ESP+0x0C] 0012FF14  00000000   old ESI value is preserved here
[ESP+0x10] 0012FF18  00000000   iArray first element pushed here
[ESP+0x14] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x18] 0012FF20  00000002   iArray third element pushed here
[ESP+0x1C] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x20] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x24] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x2C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x30] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x34] 0012FF38  00000008   iArray ninth element pushed here
```
![](images/Figure-11.21.jpg)

### Figure 11.21: Arg to printf on stack

The `INC` instruction will increment the `ESI` register. This means that it increments the `iLoop` value stored in `ESI`.

The `ADD` instruction cleans the stack by 12 bytes. Next, `ESI` is compared with `10 (0x0A)`. At this point, the `CMP` instruction will perform a signed comparison jump to the label `$LL3@main` as the `iLoop` at `ESI` less than `10(0x0A)`. The stack state after JUMP if Less than `JL` is as follows:

```
[ESP-0x0C] 0012FF08  00408140   Now JUNK
[ESP-0x08] 0012FF0C  00000000   Now JUNK
[ESP-0x04] 0012FF10  00000000   Now JUNK
[ESP]  0012FF14  00000000   old ESI value is preserved here
[ESP+0x04] 0012FF18  00000000   iArray first element pushed here
[ESP+0x08] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x0C] 0012FF20  00000002   iArray third element pushed here
[ESP+0x010] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x014] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x18] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x1C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x20] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x24] 0012FF38  00000008   iArray ninth element pushed here
[ESP+0x28] 0012FF3C  00000009   iArray tenth element pushed here
[ESP+0x2C] 0012FF40  13789938   XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B   ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.22.jpg)

### Figure 11.22: The stack state after JL

Now, imagine that we iterated 10 times over the instructions and the `iLoop` value at `ESI` has become `10 (0x0A)`. At this point, the `CMP` instruction will result in `ZF=1` and the jump will not happen to the `$LL3@main` label. The instruction pointer will move to the next instruction. The stack state at this stage will be:

```
[ESP-0x0C] 0012FF08  00408140   Now JUNK
[ESP-0x08] 0012FF0C  00000009   Now JUNK
[ESP-0x04] 0012FF10  00000009   Now JUNK
[ESP]  0012FF14  00000000   old ESI value is preserved here
[ESP+0x04] 0012FF18  00000000   iArray first element pushed here
[ESP+0x08] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x0C] 0012FF20  00000002   iArray third element pushed here
[ESP+0x010] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x014] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x18] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x1C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x20] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x24] 0012FF38  00000008   iArray ninth element pushed here
[ESP+0x28] 0012FF3C  00000009   iArray tenth element pushed here
[ESP+0x2C] 0012FF40  13789938   XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B   ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.23.jpg)
