environments would be bound by regulatory compliance. **B** is incorrect because trends may influence policy changes but wouldn't create some worldwide common trend. **C** is incorrect because security is not inspired or strengthened by trust.

+   30. A company is experiencing a substantial increase in incidents since allowing de employees to connect their mobile devices to the internal network. What is the key vulnerability behind this scenario?

+   A. Mobile devices are being allowed without any corporate policies.

+   B. Mobile devices are being used without a VPN connection.

+   C. Mobile devices are allowed to be plugged into USB ports on desktop PCs

+   D. The network infrastructure is burdened with additional traffic.

+   **A** is correct. The main vulnerability starting with a BYOD policy is the unknown status of all personally managed devices. Some will not be adequately patched or updated. Some will have malware already installed. And some may be compromised.

+   **B, C, and D** are incorrect. **B** is incorrect because a VPN still means you're connected to the network, whether on-site or remotely. **C** is incorrect because although this USB policy for desktop PCs would further increase the vulnerability of rogue devices on the network, **D** is incorrect because the additional load on the network is likely not that that significant.

+   31. Using the Windows registry editor, a security analyst navigates to the following key:

```
HKLM\Software\Policies\Microsoft\Windows\CurrentVersion\Internet Settings
```

At that key, the analyst sets the value **PreventIgnoreErrors** to **REG_DWORD = 1**. What is the vulnerability that encouraged this setting?

+   A. The Certificate Authority is employing too weak a cryptographic.

+   B. Users are ignoring certificate errors.

+   C. The Certificate Authority is untrusted.

+   D. Users' devices are unable to send an OSC status request.

+   **B** is correct. This registry entry, when set to 1, stops users from bypassing certificate errors. A certificate error could be due to any number of issues, such as a name mismatch on the certificate, the certificate having expired, or the certificate having an inadequate cryptographic strength.

+   **A, C, and D** are incorrect. **A** is incorrect because an overly weak cipher is