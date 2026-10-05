# 232 Hacking Multifactor Authentication

![](bbox=[0.105, 0.093, 0.638, 0.497])

**Figure 10.5:** Whoami/groups command showing Super Admin's elevated group memberships

The demo will show what happens when the Help Desk user logs on. Figure 10.7 shows the Help Desk user logging on with their own smart and PIN.

After the Help Desk user is successfully logging in using his own user account, it can be validated using the Windows `whoami.exe` command (see Figure 10.8). The only elevated group membership the Help Desk user has is in the Local Administrators group, as seen in Figure 10.9. Being a member of the Local Administrators group does not confer any special permissions or privileges for something on the network, as demo shows.

Figure 10.10 shows the Help Desk user's smart digital certificate. Take note of this certificate's thumbnail (i.e., E9AE294225E6740DA8) and how it differs from the Super Admin's certificate print (i.e., 55FAD5667C33E23122).