
## 常见恶意软件利用的 Windows API 函数

### NTDLL.dll 导出函数

*   `ntdll!ZwSetContextThread`
*   `ntdll!ZwGetContextThread`
*   `ntdll!ZwUnmapViewOfSection`
*   `ntdll!ZwMapViewOfSection`
*   `ntdll!ZwAllocateVirtualMemory`
*   `ntdll!ZwWriteVirtualMemory`
*   `ntdll!ZwProtectVirtualMemory`
*   `ntdll!ZwCreateThread`
*   `ntdll!ZwOpenProcess`
*   `ntdll!ZwQueueApcThread`
*   `ntdll!ZwTerminateProcess`
*   `ntdll!ZwTerminateThread`
*   `ntdll!ZwResumeThread`
*   `ntdll!ZwQueryDirectoryFile`
*   `ntdll!ZwCreateProcess`
*   `ntdll!ZwCreateProcessEx`
*   `ntdll!ZwCreateFile`
*   `ntdll!ZwDeviceIoControlFile`
*   `ntdll!ZwClose`
*   `ntdll!ZwSetInformationProcess`

### Kernel32.dll 导出函数

*   `kernel32!CreateRemoteThread`
*   `kernel32!WriteProcessMemory`
*   `kernel32!VirtualProtectEx`
*   `kernel32!VirtualAllocEx`
*   `kernel32!SetThreadContext`
*   `kernel32!CreateProcessInternalA`
*   `kernel32!CreateProcessInternalW`
*   `kernel32!CreateFileA`
*   `kernel32!CreateFileW`
*   `kernel32!CopyFileA`
*   `kernel32!CopyFileW`
*   `kernel32!CopyFileExW`

### Ws2_32.dll 导出函数

*   `ws2_32!connect`
*   `ws2_32!send`
*   `ws2_32!recv`
*   `ws2_32!gethostbyname`
