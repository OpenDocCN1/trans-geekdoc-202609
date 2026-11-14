```
NI_XFSMANAGER_API HRESULT extern WINAPI WFSStartUp ( DWORD dwVersionsRequired, LPWFSVERSION lpWFSVersion);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSOpen ( LPSTR lpszLogicalName, HAPP hApp, LPSTR lpszAppID, DWORD
dwTraceLevel, DWORD dwTimeOut, DWORD dwSrvcVersionsRequired, LPWFSVERSION lpSrvcVersion, LPWFSVERSION lpSPIVersion,
LPHSERVICE lphService);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSRegister ( HSERVICE hService, DWORD dwEventClass, HWND hWndReg);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSExecute ( HSERVICE hService, DWORD dwCommand, LPVOID lpCmdData, DWORD
dwTimeOut, LPWFSRESULT * lppResult);
NI_XFSMANAGER_API HRESULT extern WINAPI WFSCleanUp ();
NI_XFSMANAGER_API HRESULT extern WINAPI WFMAllocateBuffer( ULONG ulSize, ULONG ulFlags, LPVOID * lppvData);
NI_XFSMANAGER_API HRESULT extern WINAPI WFMAllocateMore( ULONG ulSize, LPVOID lpvOriginal, LPVOID * lppvData);
NI_XFSMANAGER_API HRESULT extern WINAPI WFMFreeBuffer( LPVOID lpvData);
```

![](bbox=[0.133, 0.253, 0.256, 0.336])

NOTE The implementation of these APIs can be found in
\Manager\NI_XFSManager.cpp.

Let's explore the code in \Samples\WosaXFSTest20100106\WosaXFSTestView.cpp to
fully understand the XFS manager's operation.

# # Step 1: WFSSStartUp

The first step is to connect the Windows-based app with the XFS manager:

```
if(m_strXFSPath == "") m_strXFSPath = FindXMLManagerPath(); ①
if(!LoadManagerFunction(m_strXFSPath)){ ②
 m_strResult += _T("WFSSStartUp error in loading funcitons.\r\n");
 m_bStartUp = FALSE;
}
else{
HRESULT hr = (*m_pfnWFSSStartUp)( nVersion, &WFSVersion); ④
if(hr == S_OK){
 str.Format("WFSSStartUp OK with version %08X\r\n", nVersion);
 m_bStartUp = TRUE;
}
```