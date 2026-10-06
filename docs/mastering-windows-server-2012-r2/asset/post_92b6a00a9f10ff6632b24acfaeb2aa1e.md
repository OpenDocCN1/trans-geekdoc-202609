
## CHAPTER 15 DYNAMIC ACCESS CONTROL: FILE SHARES, REIMAGINED

# FIGURE 15.14
Group Policy Management
Tool showing the Default Domain Controllers Policy

![](img/41a83208e6906a3732620203b836cea7_807_0.png)

# FIGURE 15.15
Group Policy Management Editor

![](img/41a83208e6906a3732620203b836cea7_807_1.png)

- 5. In the tree structure on the left, navigate to Computer Configuration > Policies > Administrative Templates > System, as shown in Figure 15.16.

# FIGURE 15.16
Location of policy to edit to enable KDC support

![](img/41a83208e6906a3732620203b836cea7_808_0.png)

You must edit the policy in the right side of the screen "KDC support for claims, compound authentication and Kerberos." Double-click the policy, and the policy editor will pop up and give you options to configure. See Figure 15.17.

# FIGURE 15.17
Configuring "KDC support for claims, compound authentication and Kerberos armoring"

![](img/41a83208e6906a3732620203b836cea7_808_1.png)

- 6. Select Enable (notice how the drop-down box gets populated with Supported) and click OK.

There are other options available in the drop-down box, and the Help window will right give you further information about the options available.

- 7. Take some time to read through the Help screen, to simply enable supported just leave it in the drop-down box and click OK.

- 8. Close the Group Policy Management tool.

- 9. Open an enabled command prompt and type gpupdate /force to propagate the group policy you configured, or you could just wait for standard replication and Group Policy refresh.

Earlier in this chapter we showed the Active Directory Administrative Center. This is where you will configure Dynamic Access Control.

## Pieces of an Access Policy

You learned that in DAC to work you have several prerequisites to configure: the claim types, the resources, and the central access rules. We also mentioned that we want to minimize the management overhead. This is where Access Policies comes into play. They bring all of configuration work together to easily administer and control access to the information within our environments. In the following pages we will show you how to secure your file servers using DAC centrally and how this can be applied across your organization. The best way to get to grips with this new technology is to dive in. Let's build a simple access policy.

## CREATING A Dynamic Access POLICY

Open the Active Directory Administrative Center and click Dynamic Access Control, as shown in Figure 15.18.

![](img/41a83208e6906a3732620203b836cea7_809_0.png)

At this point, if you create a Central Access Policy, you will not be able to. As we mentioned, you have to create resources, claim types, and central access rules to create a policy.

One thing to notice is the various options in the center window. When you click through them, the Tasks menu on the right changes to suit the option you have selected. First, you will create a new claim type.

- 1. In the center window click Claim Types, and notice how the Tasks menu changes to suit.
- 2. On the Tasks menu, under Claim Types select New > Claim Type, as shown in 15.19.

# FIGURE 15.19
Creating a new claim type

![](img/41a83208e6906a3732620203b836cea7_810_0.png)

A new window will open for creating the new claim type.

- 3. Take some time to look at the options; you will see all the attributes that you can potentially select to create a claim type. The different attributes are for both user and device claims.

For example, browse to the attribute dNSHostName, and you will notice that it belongs to Computer, as shown in Figure 15.20.

# FIGURE 15.20
Displaying the dnHostName property

![](img/41a83208e6906a3732620203b836cea7_811_0.png)

- 4. In the Source Attribute list, select Department.

- 5. Modify the "Display name" field on the right to department_Contoso; See Figure 15.21.

# FIGURE 15.21
Modifying the department attribute to create a claim type

![](img/41a83208e6906a3732620203b836cea7_811_1.png)

- 6. Scroll down to Suggested Values; this is where you will find the information relevant to Contoso; for example, Microsoft has already configured the Department claim type but has not listed any departments.

We are creating a claim for Contoso, which has four departments: Sales, IT, Accounts, and HR. You will use these later on control access to the demo shares. For example, Sales will be allowed access only to Sales data, HR will be allowed access only to HR data, and so on.

- 7. “When a user assigns a value to this claim type,” select “The following values are suggested,” as shown in Figure 15.22.

# FIGURE 15.22
Assigning values to claim types

![](img/41a83208e6906a3732620203b836cea7_812_0.png)

- 8. Click the Add button; this will bring up the “Add a suggested value” window.

- 9. Enter Sales in both the Value and “Display name” fields, as shown in Figure 15.23, and click OK.

# FIGURE 15.23
Adding a suggested value

![](img/41a83208e6906a3732620203b836cea7_812_1.png)

- 10. Repeat these steps for IT, Accounts, and HR, and click OK when finished.
Your first claim type is finished. Well done.
Now you need to create a resource property:

- 1. Choose Resource Property, and as before select New from the Tasks menu.
You will see two options listed: the resource property and the reference resource property.

- 1. Since we've already created a claim type, we're going to use a reference resource property. Select Resource Property if you do not have a claim type created.

In Figure 15.24 you can see the claim type we created earlier. The "Display name" field is also populated, and you will have a choice under "Value type" between Single-valued and Multi-valued Choice.

# FIGURE 15.24
Create Reference Resource Property

![](img/41a83208e6906a3732620203b836cea7_813_0.png)

- 3. Choose Single-valued Choice because most companies allow only one department at a time.
- 4. Click OK when finished.

- 1. On the Dynamic Access Control screen, under Tasks, select New > Resource Property.
- 2. In the Display name enter department_contoso, and in the Value type choose Single-valued Choice.
- 3. Take time to browse the options in the Value type field; notice you have a few to select from.
- 4. Scroll down to Suggested Values and add the suggested values as you were creating the claim type.
- 5. Click OK. You have now created your resource property.
At this point you will return to the Resource Properties screen, as shown in Figure 15.26.

# FIGURE 15.26
Resource Properties

![](img/41a83208e6906a3732620203b836cea7_814_1.png)

## CHAPTER 15 DYNAMIC ACCESS CONTROL: FILE SHARES, REIMAGINED

Remember when we mentioned that Microsoft has already done a lot of work to allow companies to deploy Dynamic Access Control quickly? Part of the overall goal was to make Dynamic Access Control quick to deploy, and although you had to put some thought into what rules/properties/claims types you need to create you will see from the next guide that there are a lot done for you.

- 1. Browse through the Resource Properties to see what is configured and what you could potentially reuse.

Now let's do a quick check:

- You've created a new claim type for Contoso departments.
- You've created a referenced resource property based on the Contoso claim.

Next, you have to configure a resource property list. A resource property must be part of a resource property list. The resource property list will be downloaded by the file servers. As you can see in the main Dynamic Access Control window in Figure 15.27, the resource property list is type of Container.

- 2. Double-click Resource Property Lists, and you will see the screen in Figure 15.28.

The Global Resource Property List that is shown is the default list all file servers receive.

- 3. For informational purposes, double-click the Global Resource Property List. Notice all the resource properties that are by default, as shown in Figure 15.29.
