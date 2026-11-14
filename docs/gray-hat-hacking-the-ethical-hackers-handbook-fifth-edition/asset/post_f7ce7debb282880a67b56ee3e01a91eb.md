
steps:
- 1. The Windows-based application communicates with peripherals via the XFS manager using a predefined set of app-level APIs (WFS prefix).
- 2. The XFS manager maps the specified app-level API to the corresponding service provider's APIs (WFP prefix).
  - a. The XFS manager uses the configuration information stored in the registry for the mapping process.
  - b. The XFS manager and service provider are vendor-specific implementations.
- 3. Any results from the peripheral are sent back to the Windows-based application via the XFS manager's APIs (WFM prefix).

The XFS architecture is shown in Figure 20-3.

![](img/5f597c6a70133069118d9e804ace3775_559_0.png)

Figure 20-3 XFS architecture

The following example shows the common app-level APIs used during an interaction between the Windows-based application and the XFS manager:

- WFSStartUp() Connects the Windows-based application with the XFS manager.
- WFSOpen() Establishes a session between the Windows-based application and the service provider via the XFS manager.
- WFSRegister() Configures messages to receive from the service provider.
- WFSLock() Provides exclusive access to the peripheral.
- WFSExecute() Multiple calls of this function specify different commands, such as Dispense, Read Card, Print, and so on.
- WFSUnlock() Releases control of the peripheral.
- WFSDeregister() Stops the receiving of messages from the service provider.
- WFSClose() Ends the session.
- WFSCleanUp() Disconnects the application from the XFS manager.

![](img/5f597c6a70133069118d9e804ace3775_560_0.png)

NOTE Every XFS API has synchronous and asynchronous versions that, when called, work as follows:

Synchronous call The program will be blocked until the function completes the entire operation. In this case, the application executes in a sequential manner.

Asynchronous call The function returns immediately but will be completed in an uncertain amount of time.

## XFS Manager

Every ATM vendor implements its own XFS manager via its own middleware, always following the WOSA/XFS standard defined by CEN. Here is a list of the most notable XFS middleware currently available:

- Diebold: Agilis Power
- NCR: APTRA ActiveXFS
- KAL: Kalignite
- Wincor Nixdorf: Probase (merged with Diebold)

As mentioned in the previous section, the XFS manager is responsible for mapping the API functions (DLLs starting with WFS) to SPI functions (DLLs starting with WFP) and calling the vendor-specific service providers. To see this process in action, let’s use the FreeXFS Framework (OpenXFS_V0.0.0.5.rar), which comes with the full implementation of XFSManager, service provider interfaces (SPIs) of various devices, and sample application code based on CEN XFS 3.0.2

If we look at the XFSManager implementation via FreeXFS, which is located in the \Manager\NI_XFSManager.h file, we can clearly see the definition of the supported WFS and WFM APIs:

```
NI_XFSMANAGER_API HRESULT extern WINAPI WFSStartUp ( DWORD dwVersionsRequired, LPWFSVERSION lpWFSVersion);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSOpen ( LPSTR lpszLogicalName, HAPP hApp, LPSTR lpszAppID, DWORD dwTraceLevel, DWORD dwTimeOut, DWORD dwSrvcVersionsRequired, LPWFSVERSION lpSrvcVersion, LPWFSVERSION lpSPIVersion, LPHSERVICE lphService);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSRegister ( HSERVICE hService, DWORD dwEventClass, HWND hWndReg);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSExecute ( HSERVICE hService, DWORD dwCommand, LPVOID lpCmdData, DWORD dwTimeOut, LPWFSRESULT * lppResult);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSCleanUp ();
NI_XFSMANAGER_API HRESULT extern WINAPI WFMAllocateBuffer( ULONG ulSize, ULONG ulFlags, LPVOID * lppvData);
NI_XFSMANAGER_API HRESULT extern WINAPI WFMAllocateMore( ULONG ulSize, LPVOID lpvOriginal, LPVOID * lppvData);
NI_XFSMANAGER_API HRESULT extern WINAPI WFMFreeBuffer( LPVOID lpvData);
```

![](img/5f597c6a70133069118d9e804ace3775_561_0.png)

NOTE The implementation of these APIs can be found in \Manager\NI_XFSManager.cpp.

Let's explore the code in \Samples\WosaXFSTest20100106\WosaXFSTestView.cpp to fully understand the XFS manager's operation.

## Step 1: WFSStartUp

The first step is to connect the Windows-based app with the XFS manager:

```
if(m_strXFSPath == "") m_strXFSPath = FindXFSManagerPath(); ①
if(!LoadManagerFunction(m_strXFSPath)){ ②
 m_strResult += _T("WFSStartUp error in loading functions.\r\n");
 m_bStartUp = FALSE;
}
else{
HRESULT hr = (*m_pfnWFSStartUp)( nVersion, &WFSVersion); ④
if(hr == S_OK){
 str.Format("WFSStartUp OK with version %08X\r\n", nVersion);
 m_bStartUp = TRUE;
}
}
CString CWosaXFSTestView::FindXFSManagerPath() ①
{
    HRESULT hr = WFMOpenKey(HKEY_CLASSES_ROOT, //WOSA/XFS_ROOT/LOGICAL_SERVICES,
                          "WOSA/XFS_ROOT", //lpszSubKey,
                          &hKeyXFS_ROOT); //phkResult, lpdwDisposition
    if(hr != WFS_SUCCESS) return -1;
}

BOOL CWosaXFSTestView::LoadManagerFunction(CString strPath) ②
{
    m_hLib = LoadLibrary(strPath);
    if(m_hLib == NULL){
        m_strResult += _T("Load XFS Manager failed.\\r\\n");
        UpdateData(FALSE);
        return FALSE;
    }
    else
    {
        m_strResult += _T("Load XFS Manager succeeded.\\r\\n");
        UpdateData(FALSE);
    }

    m_pfnWFSStartUp = (pfnWFSStartUp)GetProcAddress(m_hLib, "WFSStartUp"); ⑤
    m_pfnWFSOpen = (pfnWFSOpen)GetProcAddress(m_hLib, "WFSOpen");
    m_pfnWFMAllocateBuffer = (pfnWFMAllocateBuffer)GetProcAddress(m_hLib, "WFMAllocateBuffer");
}
```

Before anything else, the XFS manager must be loaded in memory; then it is implemented in a DLL and the associated path is stored in the registry. In this example, the FindXFSManagerPath() function ① (duplicated to also show the function implementation; the same for callout ②) helps to retrieve this value. Once the DLL path is identified, the LoadManagerFunction() ② helps to load it in memory via the LoadLibrary API. Within the same function, all WFS* and WFM* functions are supported by the XFS manager and loaded via the GetProcAddress API ③.

At this point, the XFS manager is loaded in memory and now needs to be connected with the Windows-based application via the WFSStartUp API ④, which passes as its first parameter the range of SPI versions that are expected to be handled by the XFS manager. If those are not supported by middleware, the call will return an error.

## Step 2: WFSOpen

Once the Windows-based application and the XFS manager are synchronized, it’s time to interact with an ATM peripheral (also known as _logical service_) to perform any desired action, such as opening the card reader or dispensing some money. The interaction with the peripheral is done via its SPI, so we first need to identify all the logical services available by querying HKEY_USERS\.DEFAULT\XFS\LOGICAL_SERVICES\ in the Windows registry.

It is important to mention that each ATM vendor has its own naming convention; for example, NCR names its dispenser CurrencyDispenser1, whereas Diebold uses the name DBD_AdvFuncDisp. These indicators are really helpful when we’re trying to identify the target of the ATM malware. Another use of this registry key is to query the status of the peripheral via the WFSGetInfo API before we start interacting with it. More details are provided in the section “ATM Malware Analysis,” later in this chapter.

Once the logical service to interact with is identified, the WFSOpen API (or the WFSAsyncOpen API, depending on the application’s needs) will receive this value as the first argument, following our example based on WosaXFSTestView.cpp. That value is passed via the m_strLocalService variable ⑤, shown next:

```
hr = (*m_pfnWFSOpen) (m_strLocalService.GetBuffer(0), ⑥
    m_hAppSync, //WFS_DEFAULT_HAPP, //hApp,
    "MySession", //NULL, //LPSTR lpszAppID,
    WFS_TRACE_ALL_API, //NULL, //DWORD dwTraceLevel,
    WFS_INDEFINITE_WAIT, //DWORD dwTimeOut,
    0x00020003, //DWORD dwSrvcVersionsRequired,
    &WFVersion1, //LPWFVERSION lpsrvcVersion,
    &WFVersion2, //LPWFVERSION lpSPIVersion,
    &hService // LPHSERVICE lphService
    );
if(hr == 0) m_hSyncService = hService; else m_hSyncService = 0;
```

```
if(hr == 0)
{
    CString str;
    str.Format("OK SyncOpen Service ID = %d SPI version High %04X Low %04X\\r\\n",m_hSyncService,WFVersion2.wHighVersion,
    WFVersion2.wLowVersion);
}
```

The remaining parameters passed to the function are self-explanatory and are not important for the purpose of our analysis.

Now, how does the XFS manager know the SPI DLL to interact with? It also comes from the registry key \XFS\SERVICE_PROVIDERS\ and is based on the logical services previously identified. Figure 20-4 shows that the DLL of the pinpad SPI is NCR_PINSP.DLL. Note that the SPIs are independently implemented by every vendor.
