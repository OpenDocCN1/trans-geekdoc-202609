# Screwbolt Wait Chain

Here we introduce another **Wait Chain** (page 1082) pattern where a client thread makes a request and a created server thread servicing the request makes another request to the client which creates a new client thread to service the server request. The new client thread makes a request to the server again, and a new server thread is created which makes a new client request, and so on. The additional signs here may be an abnormal number of threads and possibly **Handle Leak** (page 416) pattern although the latter may be present only in a client or server process only. **Thread Age** (page 1001), **Waiting Thread Time** (page 1137), and common **Blocking Module** (page 96) patterns may be used to unwind the chain and diagnose the possible problem module and corresponding **Module Product Process** (page 697). The pattern is illustrated in this diagram:

![](bbox=[0.356, 0.306, 0.603, 0.756])

Although we initially found this pattern related to LPC /ALPC IPC (page 1097) we think it is not limited to it and can occur in different client-server communication implementations.