+   - WFSLock() Provides exclusive access to the peripheral.
+   - WFSExecute() Multiple calls of this function specify different commands, such as Dispense, Read Card, Print, and so on.
+   - WFSUnlock() Releases control of the peripheral.
+   - WFSDeregister() Stops the receiving of messages from the service provider.
+   - WFSClose() Ends the session.
+   - WFSCleanUp() Disconnects the application from the XFS manager.

![](bbox=[0.13, 0.27, 0.26, 0.35])

NOTE Every XFS API has synchronous and asynchronous versions that, when called, work as follows:

Synchronous call The program will be blocked until the function completes the entire operation. In this case, the application executes in a sequential manner.

Asynchronous call The function returns immediately but will be completed in an uncertain amount of time.

# XFS Manager

Every ATM vendor implements its own XFS manager via its own middleware, always following the WOSA/XFS standard defined by CEN. Here is a list of the most notable XFS middleware currently available:

+   - Diebold: Agilis Power
+   - NCR: APTRA ActiveXFS
+   - KAL: Kalignite
+   - Wincor Nixdorf: Probase (merged with Diebold)

As mentioned in the previous section, the XFS manager is responsible for mapping the API functions (DLLs starting with WFS) to SPI functions (DLLs starting with WFP) and calling the vendor-specific service providers. To see this process in action, let’s use the FreeXFS Framework (OpenXFS_V0.0.0.5.rar), which comes with the full implementation of XFSManager, service provider interfaces (SPIs) of various devices, and sample application code based on CEN XFS 3.0.2

If we look at the XFSManager implementation via FreeXFS, which is located in the \Manager\NI_XFSManager.h file, we can clearly see the definition of the supported WFS and WFM APIs: