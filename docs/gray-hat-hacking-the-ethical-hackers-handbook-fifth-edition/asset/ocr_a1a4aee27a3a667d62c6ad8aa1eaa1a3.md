# (FSTENV (28-BYTE) PTR SS:[ESP-C] ).

Also, if the addresses held in EIP and ESP are too close to each other (which is very common if the shellcode is on the stack), then using NOPs is a good way to prevent corruption. But in that case, a simple stack adjust or pivot instruction might do the trick as well. Simply prepend the shellcode with the opcode bytes (for example, add esp,-450). The Metasploit assembler may be used to provide the required instructions in hex, as shown here:

```
root@kali:~# /usr/share/metasploit-framework/tools/metasm_shell.rb
type "exit" or "quit" to quit
use ";" or "\\n" for newline
metasm > add esp,-450
"\\x81\\xc4\\xf4\\x3e\\xfe\\xff\\xff"
metasm >
```

# Debugging the Exploit If Needed

It’s time to reset the virtual system and launch the preceding script. Remember to attach to wsshd.exe quickly and press F9 to run the program. Let the program reach the initial exception. Click anywhere in the disassembly section and press CTRL-G to bring up the “Enter expression to follow” dialog box. Enter the address from Mona that you are using to jump to ESP, as shown next. For this example, it was 0x7c345c30 from MSVCR71.dll. Press F9 to reach the breakpoint.

![](bbox=[0.14, 0.49, 0.86, 0.72])

If your program crashes instead of reaching the breakpoint, chances are you have a bad character in your shellcode or there is an error in your script. Bad character issues happen from time to time as the vulnerable program (or client SCP program, in this case) may react to certain characters and cause your exploit to abort or be otherwise modified.

To find the bad character, you will need to look at the memory dump of the debugger and match that memory dump with the actual shellcode you sent across the network. To set up this inspection, you need to revert to the virtual system and resend the attack script. When the initial exception is reached, click the stack section and scroll down until you see the A’s. Continue scrolling down to find your shellcode and then perform a manual