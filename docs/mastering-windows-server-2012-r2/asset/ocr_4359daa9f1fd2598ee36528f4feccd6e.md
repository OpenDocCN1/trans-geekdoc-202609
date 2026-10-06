19. Select the policy Contoso Test CAP, and it will display the Central Access rules you have configured for allowing/restricting access to resources.

20. Click the down arrow beside the Central Access rule, you will see the options configured earlier.

# TESTING THE NEW POLICY

You have now applied a preconfigured Central Access Policy to your server share. If you look at Figure 15.48 and Figure 15.49 again. For the permissions, you will see that the Everyone group has read-access to the folder and share after the Central Access Policy has been applied. This isn't really ideal, but it's a common problem in environments.

Technically speaking anyone should be able to access this share and retrieve the valuable information contained within. Let's test it:

+   1. On Contossof01 navigate to where your share is located.
In this example your share is located on C: \share
2. Right-click C: \share and select Properties.
3. Click the Security tab, and then click Advanced to open the "Advanced Security Settings for share" window. See Figure 15.50.

FIGURE 15.50
"Advanced Security Settings for share" window

![](bbox=[0.285, 0.477, 0.905, 0.814])