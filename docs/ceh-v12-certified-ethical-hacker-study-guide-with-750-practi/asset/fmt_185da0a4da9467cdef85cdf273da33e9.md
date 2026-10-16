
```
  
 msf6> search arch:x86 platform:windows reverse_tcp
  
 Matching Modules
 ================
  
    #   Name                                                     Disclosure Date  Rank    Check  Description
    -   ----                                                     ---------------  ----    -----  -----------
    0   `payload/windows/dllinject/reverse_tcp_allports`                            normal  No     Reflective DLL Injection, Reverse All-Port TCP Stager
    1   `payload/windows/dllinject/reverse_tcp`                                     normal  No     Reflective DLL Injection, Reverse TCP Stager
    2   `payload/windows/dllinject/reverse_tcp_dns`                                 normal  No     Reflective DLL Injection, Reverse TCP Stager (DNS)
    3   `payload/windows/dllinject/reverse_tcp_rc4_dns`                             normal  No     Reflective DLL Injection, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    4   `payload/windows/dllinject/reverse_tcp_rc4`                                 normal  No     Reflective DLL Injection, Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    5   `payload/windows/dllinject/reverse_tcp_uuid`                                normal  No     Reflective DLL Injection, Reverse TCP Stager with UUID Support
    6   `payload/windows/vncinject/reverse_tcp_allports`                            normal  No     VNC Server (Reflective Injection), Reverse All-Port TCP Stager
    7   `payload/windows/vncinject/reverse_tcp`                                     normal  No     VNC Server (Reflective Injection), Reverse TCP Stager
    8   `payload/windows/vncinject/reverse_tcp_dns`                                 normal  No     VNC Server (Reflective Injection), Reverse TCP Stager (DNS)
    9   `payload/windows/vncinject/reverse_tcp_rc4_dns`                             normal  No     VNC Server (Reflective Injection), Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    10  `payload/windows/vncinject/reverse_tcp_rc4`                                 normal  No     VNC Server (Reflective Injection), Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    11  `payload/windows/vncinject/reverse_tcp_uuid`                                normal  No     VNC Server (Reflective Injection), Reverse TCP Stager with UUID Support
    12  `payload/windows/shell/reverse_tcp_allports`                                normal  No     Windows Command Shell, Reverse All-Port TCP Stager
    13  `payload/windows/shell_reverse_tcp`                                         normal  No     Windows Command Shell, Reverse TCP Inline
    14  `payload/windows/shell/reverse_tcp`                                         normal  No     Windows Command Shell, Reverse TCP Stager
    15  `payload/windows/shell/reverse_tcp_dns`                                     normal  No     Windows Command Shell, Reverse TCP Stager (DNS)
    16  `payload/windows/shell/reverse_tcp_rc4_dns`                                 normal  No     Windows Command Shell, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    17  `payload/windows/shell/reverse_tcp_rc4`                                     normal  No     Windows Command Shell, Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    18  `payload/windows/shell/reverse_tcp_uuid`                                    normal  No     Windows Command Shell, Reverse TCP Stager with UUID Support
    19  `payload/windows/patchupdllinject/reverse_tcp_allports`                     normal  No     Windows Inject DLL, Reverse All-Port TCP Stager
    20  `payload/windows/patchupdllinject/reverse_tcp`                              normal  No     Windows Inject DLL, Reverse TCP Stager
    21  `payload/windows/patchupdllinject/reverse_tcp_dns`                          normal  No     Windows Inject DLL, Reverse TCP Stager (DNS)
    22  `payload/windows/patchupdllinject/reverse_tcp_rc4_dns`                      normal  No     Windows Inject DLL, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    23  `payload/windows/patchupdllinject/reverse_tcp_rc4`                          normal  No     Windows Inject DLL, Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    24  `payload/windows/patchupdllinject/reverse_tcp_uuid`                         normal  No     Windows Inject DLL, Reverse TCP Stager with UUID Support
    25  `payload/windows/peinject/reverse_tcp_allports`                             normal  No     Windows Inject PE Files, Reverse All-Port TCP Stager
    26  `payload/windows/peinject/reverse_tcp`                                      normal  No     Windows Inject PE Files, Reverse TCP Stager
    27  `payload/windows/peinject/reverse_tcp_dns`                                  normal  No     Windows Inject PE Files, Reverse TCP Stager (DNS)
    28  `payload/windows/peinject/reverse_tcp_rc4_dns`                              normal  No     Windows Inject PE Files, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    29  `payload/windows/peinject/reverse_tcp_rc4`                                  normal  No     Windows Inject PE Files, Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    30  `payload/windows/peinject/reverse_tcp_uuid`                                 normal  No     Windows Inject PE Files, Reverse TCP Stager with UUID Support
    31  `payload/windows/powershell_reverse_tcp`                                    normal  No     Windows Interactive Powershell Session, Reverse TCP
    32  `payload/windows/powershell_reverse_tcp_ssl`                                normal  No     Windows Interactive Powershell Session, Reverse TCP SSL
    33  `payload/windows/meterpreter/reverse_tcp_allports`                          normal  No     Windows Meterpreter (Reflective Injection), Reverse All-Port TCP Stager
    34  `payload/windows/meterpreter/reverse_tcp`                                   normal  No     Windows Meterpreter (Reflective Injection), Reverse TCP Stager
    35  `payload/windows/meterpreter/reverse_tcp_dns`                               normal  No     Windows Meterpreter (Reflective Injection), Reverse TCP Stager (DNS)
    36  `payload/windows/meterpreter/reverse_tcp_rc4_dns`                           normal  No     Windows Meterpreter (Reflective Injection), Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    37  `payload/windows/meterpreter/reverse_tcp_rc4`                               normal  No     Windows Meterpreter (Reflective Injection), Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    38  `payload/windows/meterpreter/reverse_tcp_uuid`                              normal  No     Windows Meterpreter (Reflective Injection), Reverse TCP Stager with UUID Support
    39  `payload/windows/patchupmeterpreter/reverse_tcp_allports`                   normal  No     Windows Meterpreter (skape/jt Injection), Reverse All-Port TCP Stager
    40  `payload/windows/patchupmeterpreter/reverse_tcp`                            normal  No     Windows Meterpreter (skape/jt Injection), Reverse TCP Stager
    41  `payload/windows/patchupmeterpreter/reverse_tcp_dns`                        normal  No     Windows Meterpreter (skape/jt Injection), Reverse TCP Stager (DNS)
    42  `payload/windows/patchupmeterpreter/reverse_tcp_rc4_dns`                    normal  No     Windows Meterpreter (skape/jt Injection), Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    43  `payload/windows/patchupmeterpreter/reverse_tcp_rc4`                        normal  No     Windows Meterpreter (skape/jt Injection), Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    44  `payload/windows/patchupmeterpreter/reverse_tcp_uuid`                       normal  No     Windows Meterpreter (skape/jt Injection), Reverse TCP Stager with UUID Support
    45  `payload/windows/metsvc_reverse_tcp`                                        normal  No     Windows Meterpreter Service, Reverse TCP Inline
    46  `payload/windows/meterpreter_reverse_tcp`                                   normal  No     Windows Meterpreter Shell, Reverse TCP Inline
    47  `payload/windows/upexec/reverse_tcp_allports`                               normal  No     Windows Upload/Execute, Reverse All-Port TCP Stager
    48  `payload/windows/upexec/reverse_tcp`                                        normal  No     Windows Upload/Execute, Reverse TCP Stager
    49  `payload/windows/upexec/reverse_tcp_dns`                                    normal  No     Windows Upload/Execute, Reverse TCP Stager (DNS)
    50  `payload/windows/upexec/reverse_tcp_rc4_dns`                                normal  No     Windows Upload/Execute, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    51  `payload/windows/upexec/reverse_tcp_rc4`                                    normal  No     Windows Upload/Execute, Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    52  `payload/windows/upexec/reverse_tcp_uuid`                                   normal  No     Windows Upload/Execute, Reverse TCP Stager with UUID Support
    53  `payload/windows/custom/reverse_tcp_allports`                               normal  No     Windows shellcode stage, Reverse All-Port TCP Stager
    54  `payload/windows/custom/reverse_tcp`                                        normal  No     Windows shellcode stage, Reverse TCP Stager
    55  `payload/windows/custom/reverse_tcp_dns`                                    normal  No     Windows shellcode stage, Reverse TCP Stager (DNS)
    56  `payload/windows/custom/reverse_tcp_rc4_dns`                                normal  No     Windows shellcode stage, Reverse TCP Stager (RC4 Stage Encryption DNS, Metasm)
    57  `payload/windows/custom/reverse_tcp_rc4`                                    normal  No     Windows shellcode stage, Reverse TCP Stager (RC4 Stage Encryption, Metasm)
    58  `payload/windows/custom/reverse_tcp_uuid`                                   normal  No     Windows shellcode stage, Reverse TCP Stager with UUID Support
    59  `payload/windows/pingback_reverse_tcp`                                      normal  No     Windows x86 Pingback, Reverse TCP Inline
 
```
