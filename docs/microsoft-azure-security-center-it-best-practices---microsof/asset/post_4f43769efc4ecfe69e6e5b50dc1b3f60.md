
- **Active Critical Notable Issues**: Notable issues are critical events. In the context of identity, they are critical identity events. This counter reflects the active notable issues that require immediate attention.
- **Active Warning Notable Issues**: This is the same as the previous counter, for medium-priority issues rather than critical ones.

The Failed Logs section of the Identity & Access dashboard conveys, at a glance, the main causes of failed logs.

When a user fails to authenticate, Windows generates an event called Event 4625. To investigate why a particular logon failed, click the logon in the Failed Logon Regions section. See in Figure 4-34, an Event 4625 window shows the reason for the failure. (See the Failure Information section.)

![](img/4b11e95292819ab1a383a41ef73aedb4_100_0.png)

**FIGURE 4-34** A description of Event 4625

The information available in the Event 4625 dialog may vary depending on the reasons for the failure. Table 8-1 lists some of the most common reasons for the failure.

| Error code (status/substatus) | Description |
|---|---|
| 0xC000006D | Unknown user name or bad password. |
| 0xC0000234 | Account locked out. |
| 0xC0000072 | Account currently disabled. |
| 0xC0000193 | The specified user account has expired. |
| 0xC0000071 | Expired password. |

**TABLE 8-1** Common reasons for logon failure

> TIP For a complete list of logon failure reasons, see https://aka.ms/AccountLogon.

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
0xC000006D
Sub Status: 0xC0000064
Process Information:
Caller Process ID: 0x0
Caller Process Name: -
Network Information:
Workstation Name: YURIDBVT01
Source Network Address: 192.168.1.254
Source Port: 53407
```

Detailed Authentication Information:
Logon Process: Ntlmsp
Authentication Package: NTLM
Transited Services: -
Package Name (NTLM only): -
Key Length: 0

- **Subject fields.** The Subject fields indicate the account on the local system that requested the logon. This is most commonly a service, such as the Server service, or a local process, such as Winlogon.exe or Services.exe.
- **Logon field.** The Logon Type field indicates the kind of logon that was requested. The most common types are 2 (interactive) and 3 (network).
- **Process Information fields.** The Process information fields indicate which account and process on the system requested the logon.
- **Network Information fields.** The Network Information fields indicate where a remote logon request originated. Workstation Name is not always available and may be left blank in some cases.
- **Authentication Information fields.** The Authentication Information fields provide detailed information about this logon request:
- **Transited Services.** Transited Services indicate which intermediate services have participated in this logon request.
- **Package Name.** Package name indicates which subprotocol was used among the NTLM protocols.
- **Key Length.** Key Length indicates the length of the generated session key. This will be 0 if no session key was requested.

# LISTING 4-2 Event ID 4625

```
<Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
<System>
<Provider Name="Microsoft-Windows-Security-Auditing" Guid="54849625-5478-4994-A5BBA-3E30B2C8C00" />
<EventID>4625</EventID>
<Version>0</Version>
<Level>1</Level>
<Task>12544</Task>
<Opcode>0</Opcode>
<Keywords>0x8010000000000000</Keywords>
<TimeCreated SystemTime="2019-02-19T15:08:29.580371002Z" />
<EventRecordID>60107528</EventRecordID>
<Correlation />
<Execution ProcessID="724" ThreadID="16256" />
```
<Channel>Security</Channel>
<ARGOS/></Computer>
<Security />
<System-id />
<EventData>
<Data Name="SubjectUserId">S-1-0-0</Data>
<Data Name="UserName">--</Data>
<Data Name="SubjectDomain">--</Data>
<Data Name="SubjectLogId">0x0</Data>
<Data Name="TargetUserId">S-1-0-0</Data>
<Data Name="TargetUserName">YURIDBVTO01</Data>
<Data Name="TargetDomainName">NORTHAMERICA</Data>
<Data Name="Status">0xC000006D</Data>
<Data Name="FailureReason">Unknown user name or bad password.</Data>
<Data Name="Sub Status">0xC0000064</Data>
<Data Name="Logon Type">3</Data>
<Data Name="Process Name">Ntlmsp</Data>
<Data Name="Authentication Package">NTLM</Data>
<Data Name="Transited Services">--</Data>
<Data Name="Package Name">--</Data>
<Data Name="Key Length">0</Data>
</EventData>
</Event>
```
