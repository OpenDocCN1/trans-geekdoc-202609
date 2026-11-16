To confirm this suspicion, we can write code that calls CreateThread function similar to this one:

```
typedef DWORD (WINAPI *THREADPROC)(PVOID);

DWORD WINAPI ThreadProc(PVOID pvParam)
{
    // Does some work
    return 0;
}

void foo()
{
    //...
    THREADPROC thProc = ThreadProc;
    //...
    // thProc becomes NULL because of a bug
    //...
    HANDLE Thread = CreateThread(NULL, 0, thProc, 0, 0, NULL);
    CloseHandle(hThread);
}
```