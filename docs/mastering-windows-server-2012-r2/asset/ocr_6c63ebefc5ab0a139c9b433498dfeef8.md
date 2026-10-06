# Step 5: Create a Central Access Policy and Deploy It via Group Policy

Perform the following steps to create a Central Access Policy:

+   1. From the main Dynamic Access Control window select Central Access Policies, and under Tasks Choose New > Central Access Policy.
2. Type Contoso Secure By Title / Office in the Name field.
3. In the Central Access Rules section click Add, and select the rule you created earlier.
4. Click OK to complete the policy.
5. Go to your machine that has the Group Policy Management console.
6. Open the Group Policy management console. Right-click the CAP-Contoso-demo group you created earlier, and click Edit.
7. Navigate to Computer Configuration > Policies > Windows Settings > Security Settings > File System.
8. Right-click Central Access Policy and click Manage Central Access Policies.
9. Add your new policy and click OK, and select the Group Policy Editor.

# Step 6: Apply the Policy to the Engineering Folder

Perform the following steps to apply the policy to the Engineering folder:

+   1. Navigate to the share, right-click it, and select Properties.
2. Click the Security tab and then click Advanced.
3. Click the central policy on the Advanced Security Settings for Engineering window.
4. Click Change and select the Contoso Secure By Title/Office policy.
5. Review the rules to ensure they are the correct rules.
Don't close the window!

# Step 7: Test with Effective Access

Perform the following steps to test with effective access:

+   1. Click the Effective Access tab.
2. Select a User and type Tom in the search field.
3. Check Names and then click OK.
4. View Effective Access.

Since Tom is an engineer and is located in the Empire State Building, he should get Full Control.

+   5. Now retry with Ken.
Since Ken is an engineer but is not located in the Empire State Building, he should have no access to the folder.