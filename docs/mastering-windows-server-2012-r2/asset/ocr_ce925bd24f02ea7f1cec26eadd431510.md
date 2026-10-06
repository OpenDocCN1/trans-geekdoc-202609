# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

You'll be using PowerShell to make the profile share available in the DFS namespace. You can see this happening in Figure 26.17. You'll be using the new-dfsnfscmd cmdlet

```
new-dfsnfscmd -path "\Bigfirm.com\BigfirmShares\Profiles" -TargetPath "\BF2\Profiles$" -EnableFailback $True -Description "Users profile directory"
```

# FIGURE 26.17
Adding Profiles$ to the DFS namespace

![](bbox=[0.273, 0.207, 0.843, 0.368])

By using DFS you will be able to replicate the folder or move it when you need to make any huge adjustments when the system is in production.

When you've completed the wizard, you should specifically verify that you can browse to \bigfirm.com\BigfirmShares\Profiles. If you can, you're ready to move on to the next step. If not, then you probably have an issue with permissions on the share, or you need to wait for or force the updated DFS namespace settings to replicate between controllers.

Deploying the folders for this approach is easy. You simply configure the user account objects and let Windows do the rest. In Figure 26.18, we've selected all the user accounts and opened their properties to set the profile property.

# FIGURE 26.18
Configuring many users with a roaming profile

![](bbox=[0.313, 0.597, 0.613, 0.856])

Alternatively, you can do this by editing a single user object, as you can see in Figure 26.19.