Table 10-3: These functions enable an application to request to receive or stop receiving notifications about device attachment and removal.

| API Function | DLL | Purpose |
|---|---|---|
| RegisterDeviceNotification | user32 | Request to receive device notifications |
| UnregisterDeviceNotification | user32 | Request to stop receiving device notifications |

# Visual C++

The declaration for the DEV_BROADCAST_DEVICEINTERFACE structure is this:

```
typedef struct _DEV_BROADCAST_DEVICEINTERFACE {
    DWORD dbcc_size;
    DWORD dbcc_devicetype;
    DWORD dbcc_reserved;
    GUID dbcc_classguid;
    TCHAR dbcc_name[1];
} DEV_BROADCAST_DEVICEINTERFACE
*PDEV_BROADCAST_DEVICEINTERFACE;
```

This is the function's declaration:

```
HDEVNOTIFY RegisterDeviceNotification(
    HANDLE hRecipient,
    LPVOID NotificationFilter,
    DWORD Flags
);
```

This is the code to call the function:

```
HDEVNOTIFY DeviceNotificationHandle;

DEV_BROADCAST_DEVICEINTERFACE
    DevBroadcastDeviceInterface;

DevBroadcastDeviceInterface.dbcc_size =
    sizeof(DevBroadcastDeviceInterface);

DevBroadcastDeviceInterface.dbcc_devicetype =
    DBT_DEVTYP_DEVICEINTERFACE;

DevBroadcastDeviceInterface.dbcc_classguid = HidGuid;
```