# SERVER CORE SURVIVAL GUIDE

Retype the password to confirm:
nThe command completed successfully.

The asterisk prompts you for the new password.
The command is a really old one. It was old when NT was new technology.
One of the ways to change a password is using the PowerShell cmdlet
Set-ADAccountPassword. The following is the complete cmdlet with properties:

```
Set-ADAccountPassword [-ADAccount>] [--AuthType <Negotiate> | <Basic>]
[-Credential <PSCredential>] [-NewPassword SecureString>] [-OldPassword
<SecureString>] [-Partition <string>] [-PassThru switch] [-Reset switch]
[-Server <string>] [-Confirm] [-WhatIf] <<CommonParameters>
```

# Accessing File Shares

Given that Servers is a network operating system, you will have access to shares on thennetwork. If you're dependent on Windows Explorer, you may have never attempted to connect
to a shared folder with the command prompt. First, to display the shares on a server, use the
net view command:

```
PS C:\Users\Administrator>net view \bf1
Shared resources at \bf1
```

| Share name | Type | Comment |
|---|---|---|
| isos | Disk | |
| netlogon | Disk | |
| Public | Disk | |
| SYSVOL | Disk | |
| temp | Disk | |

The command completed successfully.

Then, to access a use, use the net command, which maps a share to a drive letter.

```
PS C:\Users\Administrator>net use Z: \bf1\temp
The command completed successfully
```

With the prompt command, you can switch to that drive by entering the drive letter, like Z:
Then use your MS-DOS commands to get around the Folders.
To remove the mapped drive, use the following command:

```
PS C:\Users\Administrator>net use Z: /del
Z: deleted successfully
```

You can also use PowerShell's get-psdrive cmdlet to get drive information and
New-PSDrive to map a new drive. Here is the New-PSDrive cmdlet for your reference:

```
New-PSDrive [-Name] <String> [-PSProvider] [-Root] <String> [-Credential
<PSCredential> ] [-Description <String>] [-Persist] [-Scope <String> ]
[-Confirm] [-WhatIf] [-UseTransaction] [<CommonParameters>
```