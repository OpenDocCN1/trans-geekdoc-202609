For the pattern about **NULL Code Pointer** (page 750), we created a simple program that crashes when we pass a NULL thread procedure pointer to `CreateThread` function. We might expect to see little in the raw stack data 72 because there was no user-supplied thread code. In reality, if we dump it we will see a lot of symbolic information for code and data including ASCII and UNICODE fragments that we call **Execution Residue** patterns, and one of them is **Exception Handling Residue** 73 we can use to check for **Hidden Exceptions** (page 457) and differentiate between 1st and 2nd chance exceptions 74. Code residues are very powerful in reconstructing stack traces manually 75 or looking for partial stack traces and **Historical Information** (page 483).

To show typical execution residues we created another small program with two additional threads based on Visual Studio Win32 project. After we dismiss `About` box we create the first thread, and then we crash the process when creating the second thread because of the NULL thread procedure:

```
typedef DWORD (WINAPI *THREADPROC)(PVOID);

DWORD WINAPI ThreadProc(PVOID pvParam)
{
    for (unsigned int i = 0xFFFFFFFF; i; --i);
    return 0;
}

// Message handler for about box.
INT_PTR CALLBACK About(HWND hDlg, UINT message, WPARAM wParam, LPARAM lParam)
{
    UNREFERENCED_PARAMETER(lParam);
    switch (message)
    {
    case WM_INITDIALOG:
        return (INT_PTR)TRUE;

    case WM_COMMAND:
        if (LOWORD(wParam) == IDOK || LOWORD(wParam) == IDCANCEL)
        {
            EndDialog(hDlg, LOWORD(wParam));
            THREADPROC thProc = ThreadProc;
            HANDLE hThread = CreateThread(NULL, 0, ThreadProc, 0, 0, NULL);
            CloseHandle(hThread);
            Sleep(1000);
        }
        hThread = CreateThread(NULL, 0, NULL, 0, 0, NULL);
```