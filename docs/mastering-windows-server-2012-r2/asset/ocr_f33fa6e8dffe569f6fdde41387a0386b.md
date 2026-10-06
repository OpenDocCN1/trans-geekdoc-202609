In our example, Group Policy Management console is located on our domain controller.
(We assume at this point that you are familiar with this.)
nYou are now going to create a group policy under the root level of the domain contoso.ie and target it to just your file servers. here's some best practice advice:

+   - Create the necessary groups to properly target the file servers.

+   - Create organizational units in a structured hierarchical fashion and assign the group policy to the desired organizational unit and never at the root domain.

Let's begin:

+   1. Right-click contoso.ie, as shown in Figure 15.38, and Create a GPO in this domain and Link it.

![](bbox=[0.163, 0.335, 0.803, 0.65])

+   2. In the New GPO window, give it a name.

In our scenario we're using CAP-Contoso-Demo.

+   3. Click OK, as shown in Figure 15.39.

It should now appear in the list under contoso.ie.

+   4. Click the group policy, and under Security Filtering on the Scope tab of the Group Policy Management screen, as shown in Figure 15.40, select Authenticated Users and click Remove.