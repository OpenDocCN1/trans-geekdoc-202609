This is the code for the OnDeviceChange function:

```
```cpp
BOOL CUSbhidiocDlg::OnDeviceChange
    (WPARAM wParam,
     LPARAM lParam)
{
    switch(wParam)
    {
        case DBT_DEVICEARRIVAL:
            // Find out if the device path name matches
            // wParam.
            // If yes, perform any tasks required
            // on device attachment.

            return TRUE;

        case DBT_DEVICEREMOVECOMPLETE:

            // Find out if the device path name matches
            // wParam.
            // If yes, perform any tasks required
            // on device removal.

            return TRUE;

        default:
            return TRUE;
    }
}
```
```

# Visual Basic

These constants are from dbt.h:

```
```vb
Public Const DBT_DEVICEARRIVAL As Integer = &H8000
Public Const DBT_DEVICEREMOVECOMPLETE As Integer _
    = &H8004
```
```