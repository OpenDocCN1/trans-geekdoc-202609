```
Args: 00000000 00000000 00000000 00000000
[ 0, 0] 0 0 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 00000000
[ 0, 0] 0 0 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 00000000
[ 0, 0] 0 0 00000000 00000000 00000000-00000000

Args: 00000000 00000000 00000000 00000000
[ 11, 0] 0 2 fffffa8004ada620 00000000 fffff880177d9cc-fffffa800710e580
\FileSystem\mrxsmb mu!Mup!UncProviderCompletion
Args: 00000000 00000000 00000000 00000000
>[ 11, 1] 0 0 fffffa8004066400 fffffa80048e66c0 00000000-00000000
\FileSystem\Mup
Args: fffffa8004a98120 00000001 00000000 00000000
```

From that IRP we see a file name:

```
0: kd> !fileobj fffffa80048e66c0

[...]\AppData\Roaming\Vendor\Product\Recent\index.dat

LockOperation Set Device Object: 0xfffffa8004066400 \FileSystem\Mup
Vpb is NULL
Access: Read SharedRead SharedWrite SharedDelete

Flags: 0x40002
Synchronous IO
Handle Created

File Object is currently busy and has 0 waiters.

FsContext: 0xfffff8a00e8d9010 FsContext2: 0xfffff8a0012e4d688
CurrentByteOffset: 0
Cache Data:
Section Object Pointers: fffffa8006086928
Shared Cache Map: 00000000
File object extension is at fffffa8005c8cbe0:
```

Alternatively we get a 32-bit stack trace from Virtualized Process (page 1068):

```
0: kd> .process /r /p fffffa80063dd970
Implicit process is now fffffa80`063dd970
Loading User Symbols

0: kd> .thread /w fffffa8005eca060
Implicit thread is now fffffa80`05eca060
The context is partially valid. Only x86 user-mode context is available.
x86 context set
```