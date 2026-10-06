+   6. Locate the CAP-Contoso-Demo group policy you created earlier to deploy Central Access Policies to file servers.

+   7. Right-click and select Edit.

+   8. Navigate to Computer Configuration Policies > Windows Settings > Security Settings > File System > Central Access Policy.

+   9. Right-click and select Manage Central Access Policies.

+   10. Add CAP-AutoClassify, and choose the Group Policy from an elevated command prompt.

+   11. On your file server run gupdate/force to refresh

+   12. Apply the CAP-AutoClassify to the Accounts under C:\ \share.

+   13. Now on the client machine as a user who is not in HR or Accounts, try to access the information in Accounts.

Can you see it?

+   14. If you can see't see it, then you have Access Based Enumeration turned on, and which hides files and folders for which it knows you don't have permissions.

+   15. Try logging on with a user in Accounts or HR, and experience the difference.

+   16. Finally, create a new RTF file file5 in the Accounts folder, and put any information inside that is not protected by your classification rules.

+   17. Now try to access it from the client with both an Accounts user and a non-Accounts user.

How cool is that!

# The Bottom Line

Secure your data using conditions. Understand how you can secure your data without being a hundred of groups. Using this knowledge, you will understand the building blocks of Dynamic Access Control.

Master It In your lab and the examples we have shown at the start of this chapter, create a new share called Projects, and secure it so that only people in the Engineering and IT groups can access it. Make sure you test it. Do you remember?

Create a new claim type and resource property. As you move away from using groups and bloated Kerberos tokens, you need to understand how to ensure that only the right people can access your data. Using claim types and resource properties allows you to secure your data with new elements.

Master It How can you ensure that only employees from Ireland can access the data located on your shares? What do you need to do in order to be able to use Country as an authorization token?