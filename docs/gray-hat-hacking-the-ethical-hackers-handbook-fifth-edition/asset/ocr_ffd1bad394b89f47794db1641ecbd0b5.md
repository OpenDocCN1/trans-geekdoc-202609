```
#define  WFS_SERVICE_CLASS_IDC                         (2)
#define  WFS_SERVICE_CLASS_NAME_IDC                    "IDC"
#define  WFS_SERVICE_CLASS_VERSION_IDC                 0x0203

#define  IDC_SERVICE_OFFSET                            (WFS_SERVICE_CLASS_IDC * 100)

/* IDC Info Commands */
#define  WFS_INF_IDC_STATUS                            (IDC_SERVICE_OFFSET + 1)
#define  WFS_INF_IDC_CAPABILITIES                      (IDC_SERVICE_OFFSET + 2)
#define  WFS_INF_IDC_FORM_LIST                         (IDC_SERVICE_OFFSET + 3)
#define  WFS_INF_IDC_QUERY_FORM                        (IDC_SERVICE_OFFSET + 4)

/* IDC Execute Commands */
#define  WFS_CMD_IDC_READ_TRACK                        (IDC_SERVICE_OFFSET + 1)
#define  WFS_CMD_IDC_WRITE_TRACK                       (IDC_SERVICE_OFFSET + 2)
#define  WFS_CMD_IDC_EJECT_CARD                        (IDC_SERVICE_OFFSET + 3)
#define  WFS_CMD_IDC_RETAIN_CARD                       (IDC_SERVICE_OFFSET + 4)
```

For malware such as Ploutus that focuses on controlling the XFS middleware (Aglis, APTRA, Kalignite, and so on), this approach won’t work. Fortunately, Ploutus likes .NET. Therefore, once the malware is deobfuscated, full source code is available for analysis, without any need for reversing the majority of the components (although some components are implemented in Delphi and require reversing).

# ATM Malware Countermeasures

Here is a list of best practices when dealing with ATM malware that are definitely recommended but not applicable to all attack scenarios:

+   - An antivirus or Host Intrusion Prevention System (HIPS) is useful if and only if it is “ATM environment” aware. These products normally won’t be able to detect malicious behavior in the dispenser, for example.
+   - Disk encryption helps with offline attacks that transfer the malware to the teller machine by disconnecting the storage device from the ATM.
+   - Application whitelisting helps to execute the expected processes only.
+   - Penetration testing helps to proactively identify issues before hackers do.
+   - BIOS with password protection should be enabled.
+   - ATM malware training is useful for understanding how to dissect and detect specific threats.
+   - The “ATM Software Security Best Practices Guide” and the “ATM Security Guidelines” should be followed. See the “For Further Reading” section for more specifics.

# Summary