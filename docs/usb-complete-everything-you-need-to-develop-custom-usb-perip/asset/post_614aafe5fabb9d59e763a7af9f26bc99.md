
For an input report, the application can use ReadFile to read an Input report from a device.

To read a report, the application declares a buffer to hold the data and calls ReadFile. The buffer size should equal at least the size reported in the InputReportByteLength property of the HIDP_CAPS structure returned by HidP_GetCaps.

When called with non-overlapped I/O, ReadFile is a blocking call. If an application calls ReadFile when the HID's read buffer is empty, the application's thread waits until either a report is available, the user closes the application from the Task Manager, or the user removes the device from the bus. There are several approaches to keeping an application from hanging as it waits for a report. The device can continuously send reports. The application can attempt to read a report only after requesting one using an Output or Feature report. The application can use ReadFile with overlapped I/O and a timeout. The ReadFile calls can also take place in a separate thread.

To ensure that the device always has data to send, you can write the firmware so that the IN endpoint is always enabled and ready to respond to a request for data. If there is no new data to send, the device can send the same data as last time, or the device can return a vendor-defined code that indicates there is nothing new to report. Or before each ReadFile, the application can send a report that prompts the firmware to provide a report to send to the host.

In an overlapped read, ReadFile returns immediately even if there is no report available, and the application can call WaitForSingleObject to retrieve the report. The advantage of WaitForSingleObject is the ability to set a timeout. If the data hasn't arrived when the timeout period has elapsed, the function returns a code that indicates a timeout and the application can try again or use the CancelIo function to cancel the read operation. This approach works well if reports are normally available without delay, but the application needs to regain control if for some reason there is no report.

To prevent long delays waiting for WaitForSingleObject to return, an application can set the timeout to zero and call the function repeatedly in a loop or periodically, triggered by a timer. The function returns immediately if no report is available, and the application can perform other tasks in the loop or between timeouts.

Another way to improve the performance of an application that is reading Input reports is to do the ReadFile calls in a separate thread that notifies the main thread when a report is available. A .NET application can define an asynchronous delegate and use the BeginInvoke method to call a method that performs the ReadFile calls in a different thread. BeginInvoke can specify a callback routine that executes in the application's main thread when the method that has called ReadFile returns, enabling the application to retrieve the returned report.

## Visual C++

In addition to CreateFile, introduced in Chapter 10, an overlapped ReadFile uses these functions:

```c
BOOL CancelIo
    (HANDLE hFile);

HANDLE CreateEvent
    (LPSECURITY_ATTRIBUTES lpEventAttributes,
    BOOL bManualReset,
    BOOL bInitialState,
    LPCTSTR lpName);

BOOL ReadFile
    (HANDLE hFile,
    LPVOID lpBuffer,
    DWORD nNumberOfBytesToRead,
    LPDWORD lpNumberOfBytesRead,
    LPOVERLAPPED lpOverlapped);

DWORD WaitForSingleObject
    (HANDLE hHandle,
    DWORD dwMilliseconds);
```

This is the code for doing an overlapped ReadFile:

```c
CHAR    InputReportBuffer[3];
DWORD   BytesRead;
DWORD   Result;
HANDLE  hEventObject;
OVERLAPPED HIDOverlapped;

hEventObject = CreateEvent
    ((LPSECURITY_ATTRIBUTES)NULL,
    FALSE,
    TRUE,
    "");

HIDOverlapped.hEvent = hEventObject;
HIDOverlapped.Offset = 0;
HIDOverlapped.OffsetHigh = 0;

// Set the first byte in the buffer to the Report ID.
InputReportBuffer[0] = 0;

ReadHandle = CreateFile
    (DetailData->DevicePath,
    GENERIC_READ|GENERIC_WRITE,
    FILE_SHARE_READ|FILE_SHARE_WRITE,
    (LPSECURITY_ATTRIBUTES)NULL,
    OPEN_EXISTING,
    FILE_FLAG_OVERLAPPED,
    NULL);

Result = ReadFile
    (ReadHandle,
    InputReportBuffer,
    Capabilities.InputReportByteLength,
    &BytesRead,
    (LPOVERLAPPED) &HIDOverlapped);

Result = WaitForSingleObject
    (hEventObject,
    3000);

switch (Result)
{
    case WAIT_OBJECT_0: {
        // Success;
        // Use the report data;
        break;
    }
    case WAIT_TIMEOUT: {
        // Timeout error;
        // Cancel the read operation.
        CancelIo(ReadHandle);
        break;
    }
    default: {
        // Undefined error;
        // Cancel the read operation.
        CancelIo(ReadHandle);
        break;
    }
}
```

## Visual Basic

These are the constants and structures used in an overlapped ReadFile:

```vb
Public Const FILE_FLAG_OVERLAPPED As Integer _
    = &H40000000
Public Const FILE_SHARE_READ As Short = &H1S
Public Const FILE_SHARE_WRITE As Short = &H2S
Public Const GENERIC_READ As Integer = &H80000000
Public Const GENERIC_WRITE As Integer = &H40000000
Public Const OPEN_EXISTING As Short = 3
Public Const WAIT_OBJECT_0 As Short = 0
Public Const WAIT_TIMEOUT As Integer = &H102
```

```vb
<StructLayout(LayoutKind.Sequential)> _
Public Structure OVERLAPPED
    Dim Internal As Integer
    Dim InternalHigh As Integer
    Dim Offset As Integer
    Dim OffsetHigh As Integer
    Dim hEvent As Integer
End Structure
```

In addition to CreateFile, introduced in Chapter 10, an overlapped ReadFile uses these functions:

```vb
<DllImport("kernel32.dll")> _
Function CancelIo _
    (ByVal hFile As Integer) _
    As Integer
End Function
```

```vb
<DllImport("kernel32.dll", CharSet:=CharSet.Auto)> _
Function CreateEvent _
    (ByRef SecurityAttributes _
        As SECURITY_ATTRIBUTES, _
    ByVal bManualReset As Integer, _
    ByVal bInitialState As Integer, _
    ByVal lpName As String) _
    As Integer
End Function
```

```vb
<DllImport("kernel32.dll")> _
Function ReadFile _
    (ByVal hFile As Integer, _
    ByRef lpBuffer As Byte, _
    ByVal nNumberOfBytesToRead As Integer, _
    ByRef lpNumberOfBytesRead As Integer, _
    ByRef lpOverlapped As OVERLAPPED) _
    As Integer
End Function
```

```vb
<DllImport("kernel32.dll")> _
Function WaitForSingleObject _
    (ByVal hHandle As Integer, _
    ByVal dwMilliseconds As Integer) _
    As Integer
End Function
```

This is the code to do an overlapped ReadFile:

```vb
Dim EventObject As Integer
Dim HIDOverlapped As OVERLAPPED
Dim InputReportBuffer() As Byte
Dim NumberOfBytesRead As Integer
Dim Result As Integer
Dim Security As SECURITY_ATTRIBUTES
Dim Success As Boolean

Security.lpSecurityDescriptor = 0
Security.bInheritHandle = CInt(True)
Security.nLength = Len(Security)

EventObject = CreateEvent _
    (Security,
    CInt(False),
    CInt(True),
    "")

HIDOverlapped.Offset = 0
HIDOverlapped.OffsetHigh = 0
HIDOverlapped.hEvent = EventObject

' Set the first byte in the report buffer to the
' report ID.

InputReportBuffer(0) = 0

ReadHandle = CreateFile _
    (DevicePathName, _
    GENERIC_READ Or GENERIC_WRITE, _
    FILE_SHARE_READ Or FILE_SHARE_WRITE, _
    Security, _
    OPEN_EXISTING, _
    FILE_FLAG_OVERLAPPED, _
    0)

ReDim InputReportBuffer _
    (Capabilities.InputReportByteLength - 1)

Result = ReadFile _
    (ReadHandle, _
    InputReportBuffer(0), _
    Capabilities.InputReportByteLength, _
    NumberOfBytesRead, _
    HIDOverlapped)

Result = WaitForSingleObject _
    (EventObject, _
    3000)

Select Case Result
    Case WAIT_OBJECT_0

        ' Success
        ' Use the report data.

    Case WAIT_TIMEOUT

        ' Timeout error.
        ' Cancel the Read operation.

        CancelIo(ReadHandle)

    Case Else

        ' Undefined error.
        ' Cancel the Read operation.

        CancelIo(ReadHandle)

    End Select
```

## Details

Before calling ReadFile for the first time, the application calls CreateEvent to create an event object that is set to the signaled state when the ReadFile operation completes. Overlapped I/O requires a handle obtained from a call to CreateFile with the dwFlagsAndAttributes parameter set to FILE_FLAG_OVERLAPPED.
