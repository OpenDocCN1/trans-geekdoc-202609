
## Contention Patterns

Windows:
- **High Contention** (.NET CLR monitors, page 472)
- **High Contention** (critical sections, page 475)
- **High Contention** (executive resources, page 477)
- **High Contention** (processors, page 480)

Linux:
- **Critical Region** (page 157)

## Deadlock and Livelock Patterns

Windows:
- Deadlock (critical sections, page 182)
- Deadlock (executive resources, page 194)
- Deadlock (LPC/ALPC, page 197)
- Deadlock (managed space, page 202)
- Deadlock (mixed objects, kernel space, page 205)
- Deadlock (mixed objects, user space, page 210)
- Deadlock (self, page 218)
- Livelock (page 606)

## DLL Link Patterns

Windows:
- Duplicated Module (page 287)
- Missing Component (general, page 668)
- Missing Component (static linking, user mode, page 672)
- Unloaded Module (page 1041)

## Dynamic Memory Corruption Patterns

Windows:
- Double Free (kernel pool, page 260)
- Double Free (process heap, page 267)
- Dynamic Memory Corruption (kernel pool, page 292)
- Dynamic Memory Corruption (managed heap, page 301)
- Dynamic Memory Corruption (process heap, page 307)

Mac OS X:
- Double Free (process heap, page 278)
- Dynamic Memory Corruption (process heap, page 305)

Linux:
- Dynamic Memory Corruption (process heap, page 304)

## Executive Resource Patterns

Executive resource (ERESOURCE) patterns may help with analysis of the output of **!locks** WinDbg command from Windows kernel and complete memory dumps:

- **Accidental Lock** (page 53)
- **Deadlock** (executive resources, page 194)
- **Deadlock** (mixed objects, kernel space, page 205)
- **Deadlock** (self, page 218)
- **High Contention** (executive resources, page 477)
- **Livelock** (page 606)
- **Semantic Split** (page 853)
- **Swarm of Shared Locks** (page 966)
- **Wait Chain** (executive resources, page 1089)

## Exception Patterns

Windows:
- C++ Exception (page 110)
- Custom Exception Handler (kernel space, page 169)
- Custom Exception Handler (user space, page 171)
- Distributed Exception (managed code, page 243)
- Exception Module (page 328)
- Exception Stack Trace (page 363)
- FPU Exception (page 398)
- Handled Exception (.NET CLR, page 428)
- Handled Exception (kernel space, page 433)
- Handled Exception (user space, page 434)
- Hidden Exception (kernel space, page 455)
- Hidden Exception (user space, page 457)
- Invalid Exception Information (page 568)
- Managed Code Exception (page 617)
- Mixed Exception (page 688)
- Multiple Exceptions (kernel mode, page 708)
- Multiple Exceptions (managed space, page 713)
- Multiple Exceptions (user mode, page 714)
- Nested Exceptions (managed code, page 723)
- Nested Exceptions (unmanaged code, page 726)
- Problem Exception Handler (page 810)
- Software Exception (page 875)
- Stored Exception (page 959)
- Translated Exception (page 1013)

Mac OS X:
- C++ Exception (page 109)
- Multiple Exceptions (page 706)

Linux:
- C++ Exception (page 108)

## Falsity and Coincidence Patterns

Windows:
- Coincidental Error Code (page 128)
- Coincidental Frames (page 130)
- Coincidental Symbolic Information (page 137)
- False Effective Address (page 389)
- False Function Parameters (page 390)
- False Positive Dump (page 393)

Mac OS X:
- Coincidental Symbolic Information (page 135)

Linux:
- Coincidental Symbolic Information (page 134)

“Hooksware” word describes applications heavily dependent on various hooks that are either injected by normal Windows hooking mechanism, registry, or via more elaborate tricks like remote threads or code patching. There are various patterns in memory dump analysis that help in detection, troubleshooting, and debugging hookware:

- **Changed Environment** (page 114)

  Loaded hooks shift other modules by changing their load address and may expose dormant bugs.

- **Coincidental Symbolic Information** (page 137)

  Sometimes hooks are loaded at round addresses like 0x10000000, and these values are very frequently used as flags or constants too.

- **Execution Residue** (page 371)

  Here we can find various hooks that use normal Windows hooking mechanism. Sometimes the search for “hook” word in symbolic raw stack output of dds command reveals them but beware of coincidental symbolic information. See also how to dump raw stack from x64/x86 process dump files 238, x86 processes saved as x64 process dump file 239, process spaces from x86 complete memory dumps 240, and x86/x64 process spaces from x64 complete memory dumps 241.

- **Hidden Module** (page 463)

  Some hooks may hide themselves.

- **Hooked Functions** (kernel space, Volume 1, page 468)

- **Hooked Functions** (user space, Volume 1, page 468)

- **Hooking Level** (page 489)

This is the primary detection mechanism for hooks that patch code (Patched Code, 802).

See also Raw Pointer (page 828) and Out-of-Module Pointer (page 773) patterns.

- **Hooked Modules** (page 489)

  The WinDbg script to run when we don't know which module was patched.

- **Insufficient Memory** (module fragmentation, page 544)

  Hooks loaded in the middle of address space limit the maximum amount of memory that can be allocated at once. For example, various virtual machines reserve the big chunk of memory at startup.

- **Message Hooks** (page 663)

  Windows message hooking pattern example. See also modeling example 242.

- **No Component Symbols** (page 734)

  We can get an approximate picture of what a 3rd-party hook module does by looking at its import table or in the case of patching by looking at the list of deviations returned by .chkimg command.

- **Unknown Component** (page 1035)

  This pattern might give an idea about the author of the hook.

- **Wild Code** (page 1148)

  When hooking goes wrong, the execution path goes into the wild territory.

## Memory Consumption Patterns

Windows:
- Handle Leak (page 416)
- Handle Limit (GDI, kernel space, page 417)
- Handle Limit (GDI, user space, page 423)
- Insufficient Memory (committed memory, page 523)
- Insufficient Memory (control blocks, page 525)
- Insufficient Memory (handle leak, page 526)
- Insufficient Memory (kernel pool, page 535)
- Insufficient Memory (module fragmentation, page 544)
- Insufficient Memory (physical memory, page 552)
- Insufficient Memory (PTE, page 555)
- Insufficient Memory (region, page 556)
- Insufficient Memory (reserved virtual memory, page 559)
- Insufficient Memory (session pool, page 562)
- Insufficient Memory (stack trace database, page 563)
- Memory Fluctuation (process heap, page 634)
- Memory Leak (.NET heap, page 636)
- Memory Leak (I/O completion packets, page 643)
- Memory Leak (page tables, page 644)
- Memory Leak (process heap, page 650)
- Memory Leak (regions, page 657)
- Object Distribution Anomaly (.NET heap, page 756)
- Punctuated Memory Leak (page 819)
- Reference Leak (page 830)
- Relative Memory Leak (page 834)

## Meta-Memory Dump Patterns

Windows:
- Abridged Dump (page 49)
- Clone Dump (page 118)
- Corrupt Dump (page 137)
- Early Crash Dump (page 312)
- Evental Dumps (page 328)
- False Positive Dump (page 393)
- Fat Process Dump (page 395)
- Inconsistent Dump (page 498)
- Late Crash Dump (page 601)
- Lateral Damage (page 602)
- Manual Dump (kernel, page 625)
- Manual Dump (process, page 630)
- Mirror Dump Set (page 666)
- No Process Dumps (page 740)
- No System Dumps (page 741)
- Quiet Dump (page 823)
- Self-Dump (page 850)
- Step Dumps (page 955)
- Tampered Dump (page 974)
- Truncated Dump (page 1015)
- Unsynchronized Dumps (page 1050)

Mac OS X:
- Truncated Dump (page 1014)
