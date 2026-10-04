When reviewing the Event 4625, pay close attention to the Logon field. If this field is set to 3, it means the logon attempt came from the network. In this case, you'll also see an IPAddress field with the corresponding IP address. If LogonType set to 5, it means the logon attempt is coming from a source or process. A Process field will contain the process name. The code shown in Listing 4-1 contains the entire content of the Event 4625, which is generated when a logon request fails, and it appears on the computer where access was attempted.

# LISTING 4-1 Event ID 4625

```
Log Name: Security
Source: Microsoft-Windows-Security-Auditing
Date: 2/19/2019 9:08:29 AM
Event ID: 4625
Task Category: Logon
Level: Information
Keywords:Audit Failure
User: N/A
Computer: ARCOS
Description:
An account failed to log on.
Subject:
Security ID: NULL SID
Account Name: -
Account Domain: -
Logon ID: 0x0
Logon Type: 3
Account For Which Logon Failed:
Security ID: NULL SID
Account Name:
YURIDBVT01$
Account Domain: NORTHAMERICA
Failure Information:
Failure Reason:
Unknown user name or bad password.
Status:
xC000006D
Sub Status: 0xC0000064
Process Information:
Caller Process ID: 0x0
Caller Process Name: -
Network Information:
Workstation Name: YURIDBVT01
Source Network Address: 192.168.1.254
Source Port: 53407
```