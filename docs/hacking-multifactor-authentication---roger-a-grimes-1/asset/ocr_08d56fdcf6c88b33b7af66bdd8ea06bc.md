# 236 Hacking Multifactor Authentication

![](bbox=[0.092, 0.103, 0.418, 0.212])

![](bbox=[0.488, 0.103, 0.814, 0.212])

![](bbox=[0.092, 0.227, 0.418, 0.336])

Figure 10.11: The Help Desk usaming its existing UPN to frogtemp@victim.com first before renaming Super Admin's UPN to helpdesk@victim.com

![](bbox=[0.092, 0.393, 0.478, 0.595])

Figure 10.12: Demo login showing the Help Desk user login using their smartcard, PIN, and UPN

When the Help Desk user runs whoami.exe (Figure 10.13) and whoami /groups (Figure 10.14), it now reveals the Help Desk user is logged in as Super Admin and has the elevated group memberships of Super Admin, even though they are using their own smartcard and PIN.

Now at this point you might be thinking that I could just copied Figure 10.13 and 10.14 from the previous Super Admin screenshots from Figures 10.8 and 10.9. And I could have, but I didn't. For one, you can see it real time. You can see a video of this simulated attack demo' in action by the author here: you.be/0L031AMuoKI. Second, when the currently logged-on user's (e.g., Help Desk) smartcard digital certificate is revealed displays the thumbprint (i.e., E9E2A94225E6A740DA8) From Figure 10.10 (i.e., the Help Desk user's cert) and not 55DAD6567C33E23D122 (i.e., the Super Admin's cert thumbprint).