Another possibility of a hardware error: frequent multiple unrelated bugchecks and bugchecks in memory dumps with valid instructions at faulting IP. Beware also about misaligned IP that can look like a valid instruction.

Additional examples:

```
WHEA_UNCORRECTABLE_ERROR (124)
A fatal hardware error has occurred. Parameter 1 identifies the type of error
source that reported the error. Parameter 2 holds the address of the
WHEA_ERROR_RECORD structure that describes the error condition.
Arguments:
Arg1: 0000000000000000, Machine Check Exception
Arg2: ffffa8004846748, Address of the WHEA_ERROR_RECORD structure.
Arg3: 0000000000000000, High order 32-bits of the MCi_STATUS value.
Arg4: 0000000000000000, Low order 32-bits of the MCi_STATUS value.

1: kd> dt -r _WHEA_ERROR_RECORD ffffa8004846748
hal!_WHEA_ERROR_RECORD
   +0x000 Header            : _WHEA_ERROR_RECORD_HEADER
      +0x000 Signature        : 0x52455043
      +0x004 Revision         : _WHEA_REVISION
         +0x000 MinorRevision  : 0x10 ''
         +0x001 MajorRevision  : 0x2 ''
         +0x002 AsUSHORT       : 0x210
      +0x006 SignatureEnd     : 0xffffffff
      +0x00a SectionCount     : 3
      +0x00c Severity         : 1 ( WheaErrSevFatal )
      +0x010 ValidBits        : _WHEA_ERROR_RECORD_HEADER_VALIDBITS
         +0x000 PlatformId     : 0y0
         +0x000 Timestamp      : 0y1
         +0x000 PartitionId    : 0y0
         +0x000 Reserved       : 0y000000000000000000000000000000000 (0)
         +0x000 AsULONG        : 2
      +0x014 Length         : 0x3a0
      +0x018 Timestamp      : _WHEA_TIMESTAMP
         +0x000 Seconds        : 0y00100010 (0x22)
         +0x000 Minutes        : 0y00101011 (0x2b)
         +0x000 Hours          : 0y00001100 (0xc)
         +0x000 Precise        : 0y0
         +0x000 Reserved       : 0y00000000 (0)
         +0x000 Day            : 0y00010110 (0x16)
         +0x000 Month          : 0y00000100 (0x4)
         +0x000 Year           : 0y00001010 (0xa)
         +0x000 Century        : 0y00010100 (0x14)
      +0x000 AsLARGE_INTEGER : _LARGE_INTEGER 0x140a0416`00c2b22
   +0x020 PlatformId        : _GUID {00000000-0000-0000-0000-000000000000}
      +0x000 Data1          : 0
      +0x004 Data2          : 0
      +0x006 Data3          : 0
      +0x008 Data4          : [8] ""
   +0x030 PartitionId       : _GUID {00000000-0000-0000-0000-000000000000}
      +0x000 Data1          : 0
      +0x004 Data2          : 0
      +0x006 Data3          : 0
      +0x008 Data4          : [8] ""
   +0x040 CreatorId         : _GUID {cf07c4bd-b789-4e18-b3c4-1f732cb57131}
      +0x000 Data1          : 0xcf07c4bd
      +0x004 Data2          : 0xb789
      +0x006 Data3          : 0x4e18
      +0x008 Data4          : [8] "????"
   +0x050 NotifyType        : _GUID {e8f56ffe-919c-4cc5-ba88-65abe14913bb}
```