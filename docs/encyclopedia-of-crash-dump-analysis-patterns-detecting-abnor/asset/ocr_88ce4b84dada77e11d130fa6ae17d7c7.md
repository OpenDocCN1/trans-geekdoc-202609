# Last Error Collection

Sometimes a dump file looks normal inside, and we don’t see any suspicious past activity. However, as it often happens, the dump was saved manually as a response to some failure. This pattern might help in finding further troubleshooting suggestions. If we have a process memory dump we can get all errors and NTSTATUS values at once using !gle command with -all parameter:

```
0:000> !gle -all
Last error for thread 0:
LastErrorValue: (Win32) 0x3e5 (997) - Overlapped I/O operation is in progress.
LastStatusValue: (NTSTATUS) 0x103 - The operation that was requested is pending completion.

Last error for thread 1:
LastErrorValue: (Win32) 0 (0) - The operation completed successfully.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

Last error for thread 2:
LastErrorValue: (Win32) 0 (0) - The operation completed successfully.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

Last error for thread 3:
LastErrorValue: (Win32) 0 (0) - The operation completed successfully.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

...

Last error for thread 28:
LastErrorValue: (Win32) 0 (0) - The operation completed successfully.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

Last error for thread 29:
LastErrorValue: (Win32) 0x6ba (1722) - The RPC server is unavailable.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

Last error for thread 2a:
LastErrorValue: (Win32) 0 (0) - The operation completed successfully.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

Last error for thread 2b:
LastErrorValue: (Win32) 0 (0) - The operation completed successfully.
LastStatusValue: (NTSTATUS) 0 - STATUS_WAIT_0

...
```