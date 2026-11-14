be one or more ways to force the loading of an undesired DLL. Let’s use a simple analogy to describe an example of the problem. We will assume that you always put the salt and pepper used on food at a very specific location in a kitchen cabinet. Imagine that the next time you go to use them, they are not at that location. You could forgo using the salt and pepper, or you could go looking for them at other common locations, such as other cabinets, tables, and counters. Eventually, you will either locate the salt and pepper or give up. This is not so different from the search order used in relation to DLL loading. A more secure setting would be to only allow a desired DLL to be loaded from a very specific location, such as C:\Windows\System32\. A less secure option would be to allow the DLL to be loaded from various locations based on a search order precedence.

Let’s get into a bit more detail about how and from where DLLs can be loaded. First, for the past few versions of Windows there is a registry container, typically at HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\KnownDlls\. An example is shown here.

![](bbox=[0.118, 0.374, 0.881, 0.608])

This container stores DLLs that are commonly used to help expedite program loading, but it’s also seen by some as a security control because it specifies that the DLLs listed can only be loaded from the System32 folder under C:\Windows\System32\ or C:\Windows\SysWOW64\4. Next, the LoadLibraryEX function can be used to dynamically load DLLs requested by a process:

```
HMODULE WINAPI LoadLibraryEx(
_In_ LPCTSTR lpFileName,
_Reserved_ HANDLE hFile,
_In_ DWORD dwFlags
);
```

One of the required arguments is dwFlags, which is used to specify from where the DLL can potentially be loaded and other behaviors, such as that related to AppLocker and what will happen upon entry in regard to code execution. More information can be found at https://msdn.microsoft.com/en-us/library/windows/desktop/ms684179(v=vs.85).aspx. If