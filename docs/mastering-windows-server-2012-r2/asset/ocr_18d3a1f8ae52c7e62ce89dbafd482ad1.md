3. Set it to Enabled, and this policy will grant Administrators Full Control to any newly cre-ated profile.

Remember that policies don't apply straightaway. In a production scenario, you will prob-able to wait for the length of the refresh period.

4. In a test or lab scenario, run the following command to force a computer to apply a com-puter configuration from inherited GPOs:

```
gpupdate /target:computer /force
```

Figure 26.23 showing that when you test this, you will see that Administrators will have Full Over the profile. This will make user management and troubleshooting a lot easier for administrative staff and allows services that run as an administrator user to access the contents.

FIGURE 26.23 Administrators have access to roaming profile folders.

![](bbox=[0.313, 0.335, 0.636, 0.646])

You managed to deploy roaming profiles by just creating a shared folder and configuring the user accounts. That was pretty simple. However, we did mention that the security of the Profiles isn't as tight as you might think like the permissions required for this ‘self-service’ technique. A sneaky user could start creating folders in the Profiles$ share and storing data there. You might want to look at an alternative way to deploy user profiles.

# Creating a Roaming Profiles Share: The Hard Way

You can adopt this solution if you want 100-percent control over the contents of the folder containing roaming profiles. You manually create every folder and set the permissions.

+   1. Create the Profiles folder in the same location as you did in the previous sections.

+   2. Disable inheritance, but do not copy the inherited permissions.