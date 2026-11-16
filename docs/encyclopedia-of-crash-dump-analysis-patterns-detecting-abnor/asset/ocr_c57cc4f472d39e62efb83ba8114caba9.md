# Debugger Omission

If some false positives can be considered soft **Debugger Bugs** (page 219), false negatives can have more severe impact on software behavior analysis, especially in the malware analysis. A typical example here is the current .imgscan command which according to the documentation should by default scan virtual process space for MZ/PE signatures. Unfortunately it doesn't detect such signatures in resource pages (we haven't checked stack regions yet):

```
00000000`0fd0000 image base
SECTION HEADER #4
  .rsrc name
  6430 virtual size
  4000 virtual address
  6600 size of raw data
  1600 file pointer to raw data
  [...]
  40000040 flags
        Initialized Data
        (no align specified)
        Read Only
0:000> .imgscan /r 00000000`0fd4000 L200
0:000> s -[12]sa 00000000`0fd4000 L200
00000000`0ffd40b0  "MZ"
00000000`0ffd40fd  "!This program cannot be run in D"
00000000`0ffd411d  "OS mode."
00000000`0ffd4188  "Rich"
00000000`0ffd4198  "PE"
0:000> !dh 00000000`0ffd40b0
File Type: DLL
FILE HEADER VALUES
  14C machine (i386)
  3 number of sections
  time date stamp Fri Jan 18 21:27:25 2013
  0 file pointer to symbol table
  0 number of symbols
E0 size of optional header
2102 characteristics
        Executable
        32 bit word machine
        DLL
[...]
```

Other analysis scenarios include **!analyze -v** that shows us a breakpoint instead of an exception violation from a parallel thread.