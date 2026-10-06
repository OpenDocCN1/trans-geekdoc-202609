operating system. If you match the server operating system across the top row with the client operating system down the left-hand column, the table will show you which version of SMB will be used during communication. For example, if you were to choose Server 2008 R2 from the top row as the server operating system and match a Windows 7 from the left-hand column, the table would show you that the highest supported version of SMB you could use is SMB 2.1.

# ### Table 13.3: SMB Version in Relation to Operating System Version

| CLIENT/SERVER OS | Windows Server 2012 R2 | Windows 7 Server 2008 R2 | Windows Vista Server 2008 | Previous Versions of Windows |
|---|---|---|---|--|
| Windows Server 2012 R2 | SMB 3.0 | SMB 2.1 | SMB 2.0 | SMB 1.0 |
| Windows 7 Server 2008 R2 | SMB 2.1 | SMB 2.1 | SMB 2.0 | SMB 1.0 |
| Windows Vista Server 2008 | SMB 2.0 | SMB 2.0 | SMB 2.0 | SMB 1.0 |
| Previous Versions of Windows | SMB 1.0 | SMB 1.0 | SMB 1.0 | SMB 1.0 |

SMB 3.0 is used whenever possible by the clients that support it. Since SMB 3.0 is not supported by other operating systems (such as Windows 7 or Windows Server 2008), newer clients can use older versions of the protocol to talk to legacy machines. The good news is that all of this is automatic. You don't need to do any special configuration to take advantage of SMB 3.0 or to switch back to SMB 2.0 or SMB 1.0 for legacy clients. Here's what occurs with SMB:

+   * If clients support SMB 3.0, SMB 3.0 will automatically be used.
* If one of the clients does not support SMB 3.0 (Windows 7, for example), the OS that it supports (SMB 2.1 in this example) will be used for the session.

You've probably heard some of Microsoft's "Better Together" marketing campaigns. That's not just marketing for marketing's sake. SMB is one example where you'll truly enjoy better performance when you match up new technologies with each other. A network running Windows Server 2012 R2 servers while still running Windows 7 desktops won't be using SMB 3.0. If it's a busy network, the difference will be noticeable.