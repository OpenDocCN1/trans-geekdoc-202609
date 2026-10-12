
## Next Steps After Adding UPN Suffix

After adding the UPN suffix, you can now continue by downloading Azure AD Connect and installing it directly upon the DC of your on-prem AD domain. You can use a spare server as well, but for me, and this book, I'm installing it right onto the Domain Controller. The download can be found at `http://go.microsoft.com/fwlink/?LinkId=615771`.

After you run it, you'll start out with a welcome screen. The next screen can be seen in [Figure 2.44](#c02.xhtml#figure2-44) explaining Express Settings.

![Figure 2.44 Use Express Settings to connect your (simple) on-prem AD to Azure AD.](images/c02f044.jpg)

**[Figure 2.44](#c02.xhtml#figureanchor2-44)** Use Express Settings to connect your (simple) on-prem AD to Azure AD.

I would also say that Express settings are good for the book exercises and to get you up and running but might be suboptimal for "real life." Typically you want to point it toward specific OUs, so you don't sync all accounts to Azure AD, like your admin and/or service accounts.

That said, so I don't have to go down every rat hole with the tool, and I can get you on the road with examples quickly, the Express Settings should be fine for our use.

On the next screen, you'll provide your Azure AD creds (as seen in [Figure 2.45](#c02.xhtml#figure2-45)); this is what you used to set up your E5 trial. Then you'll provide your on-prem AD creds as seen in [Figure 2.46](#c02.xhtml#figure2-46).

![Figure 2.45 Give it the credentials you used when setting up your E5 account.](images/c02f045.jpg)

**[Figure 2.45](#c02.xhtml#figureanchor2-45)** Give it the credentials you used when setting up your E5 account.

![Figure 2.46 Provide the on-prem AD domain administrator credentials.](images/c02f046.jpg)

**[Figure 2.46](#c02.xhtml#figureanchor2-46)** Provide the on-prem AD domain administrator credentials.

Now when you get to the Azure AD sign-in configuration page, you should see the UPN name you added to on-prem AD marry up to the Azure AD domain name as seen in [Figure 2.47](#c02.xhtml#figure2-47). Also in [Figure 2.47](#c02.xhtml#figure2-47), a small bug in the Azure AD Connect program requires you to select the "Continue without any verified domains" check box, even though you do have a verified domain. It might be fixed by the time you read this.

![Figure 2.47 Be sure your UPN and Azure names match as Verified.](images/c02f047.jpg)

**[Figure 2.47](#c02.xhtml#figureanchor2-47)** Be sure your UPN and Azure names match as Verified.

Click Next and then start the process going. You will be notified when the process is complete, as seen in [Figure 2.48](#c02.xhtml#figure2-48).

![Figure 2.48 The AD Connect sync wizard is complete.](images/c02f048.jpg)

**[Figure 2.48](#c02.xhtml#figureanchor2-48)** The AD Connect sync wizard is complete.

Wait a few minutes. Then, you can refresh the Azure AD Admin Center and see the results. I found that the best way to get results was not to hit the refresh button, circled as seen in [Figure 2.49](#c02.xhtml#figure2-49), but rather to refresh the whole page (see the arrow), then click Users then "All users." And, bingo.

![Figure 2.49 Refresh the page to see the newly synced users. Note new users are coming from Windows Server AD.](images/c02f049.jpg)

**[Figure 2.49](#c02.xhtml#figureanchor2-49)** Refresh the page to see the newly synced users. Note new users are coming from Windows Server AD.

You'll also see in [Figure 2.49](#c02.xhtml#figure2-49) in the Source column which users were created from which source: Azure Active Directory versus Windows Server AD.

### Changing Over the Users' Suffixes

But, wait a second! After the synchronization occurs, synchronized users from on-prem AD will not have the nice, pretty `fabrikam1000.com` as part of their username but instead still have the ugly `fabrikam1000.onmicrosoft.com` as part of their username.

Why would this be? Because your on-prem AD users need to already be expressly using the suffix, *and only then* will you see it after synchronization.

To change it, for one user, use Active Directory Users and Computers, find an account, like EastSalesUser1, like what's seen in [Figure 2.50](#c02.xhtml#figure2-50). Then click the Account tab so you can perform two steps:

*   **Step 1:** Actually enter in a name in the "User logon name" field. Usually this will be the name they already use, know, and love.
*   **Step 2:** Pull down and select the custom domain name you specified within Active Directory Domains and Trusts earlier. In my case, it's `Fabrikam1000.com`.

![Figure 2.50 Each user needs to have the correct suffix in on-prem AD for it to be synchronized to Azure AD.](images/c02f050.jpg)

**[Figure 2.50](#c02.xhtml#figureanchor2-50)** Each user needs to have the correct suffix in on-prem AD for it to be synchronized to Azure AD.

You can wait a while, and the changes will naturally occur.

Or you can see the changes happen in real time. To see them, find the Azure AD Connect folder and launch Synchronization Service as seen in [Figure 2.51](#c02.xhtml#figure2-51).

![Figure 2.51 Launching the Synchronization Service](images/c02f051.jpg)

**[Figure 2.51](#c02.xhtml#figureanchor2-51)** Launching the Synchronization Service

Then, the tool itself doesn't seem to have a big "Click Here to Sync" button. But there's a PowerShell way to do it.

You should be able to push up just the changes, or deltas. That command is:

```
Start-AdSyncSyncCycle -policytype delta
```

If that doesn't do the trick, wait until the first command finishes and just try pushing it all up again. That command is:

```
Start-AdSyncSyncCycle -policytype initial
```

You can see the result of these two commands running in [Figure 2.52](#c02.xhtml#figure2-52).

![Figure 2.52 Using PowerShell to force an AD to AAD sync](images/c02f052.jpg)

**[Figure 2.52](#c02.xhtml#figureanchor2-52)** Using PowerShell to force an AD to AAD sync

When it's complete, refresh Azure AD and look again at all users. Carefully notice that the one user you specified now has the right username: [EastSalesUser1@fabrikam1000.com](mailto://EastSalesUser1@fabrikam1000.com) and not the `onmicrosoft.com` one any longer, as shown in [Figure 2.53](#c02.xhtml#figure2-53).

![Figure 2.53 See that your one user has successfully come over from on-prem AD to Azure AD.](images/c02f053.jpg)

**[Figure 2.53](#c02.xhtml#figureanchor2-53)** See that your one user has successfully come over from on-prem AD to Azure AD.

### Mass Updating the UPN for On-Prem AD (Instead of Clicking Through to Each User)

Of course you don't want to spend your whole weekend updating each and every user's UPN name by hand just so it synchronizes correctly to Azure AD.

The secret to mass updating all users' UPN names is quickly revealed in a blog entry here:

`https://blogs.technet.microsoft.com/heyscriptingguy/2013/08/13/add-user-principal-names-in-active-directory-via-powershell/`

If you named your on-prem domain `fabrikam.com`, and if your custom Azure name is say, `Fabrikam.com`, then this one-line script ought to populate each user's UPN attributes in a jiffy. In my case, specifically in the Sales OU.

```
Get-ADUser -Filter * -SearchBase 'ou=Sales,dc=fabrikam,dc=com'
-Properties userPrincipalName | foreach
{ Set-ADUser $_ -UserPrincipalName
("{0}@{1}" -f $_.name,"fabrikam1000.com")}
```

Then, use the technique earlier to re-sync on-prem AD to Azure AD, and bingo.

Everyone now has the exact right username in Azure AD, populated from on-prem AD, as seen in [Figure 2.54](#c02.xhtml#figure2-54).

![Figure 2.54 After the on-prem AD PowerShell command, then a sync to Azure AD, all accounts now show your custom domain name.](images/c02f054.jpg)

**[Figure 2.54](#c02.xhtml#figureanchor2-54)** After the on-prem AD PowerShell command, then a sync to Azure AD, all accounts now show your custom domain name.

### Deleting Accounts in Azure AD
