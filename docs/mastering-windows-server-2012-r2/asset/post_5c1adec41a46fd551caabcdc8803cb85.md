
HR OU? Well, this is one of the delegated tasks that GPMC can control. Let's take a look at each delegation and the scope.

GPOs, by default, can be created by a member of the Administrators for the domain or by members of the group classed Group Policy Creator Owners. However, although members of Administrators have full control of GPOs, members of Group Policy Owners can only modify policies they have created, unless they have been specifically granted permission to modify a policy. So, if you put a delegated Group administrator into the security group Group Policy Creator Owners (that's almost as awkward as Active Directory Users and Computers), then that person can create new policy objects and modify them.

To delegate to create a GPO in your domain, you will head down to the Group Policy Objects in GPMC. Once you click this node, you will select the Delegation tab in the right pane to view the list of users and groups that have been granted the ability to create GPOs in the domain, as shown in Figure 9.35.

Figure 9-35
Delegation of creating GPOs using GPMC

![](img/41a83208e6906a3732620203b836cea7_554_0.png)

It's one thing to create a GPO; linking GPO to a site, domain, or OU is another matter. Administrators have this power by default, but a special delegation can be configured, per AD node, to grant other administrators this capability. Here, the copying is very important to follow.

# CHAPTER 9 GROUP POLICY: AD'S GAUNTLET AND ACTIVE DIRECTORY DELEGATION

Unlike the ability to create a GPO, which is per the entire domain, the ability to link an AD node is per AD node, which makes logical sense. How about the configuration of this delegation?

To configure who can link a GPO to an AD node, you need to select the target AD node in the GPMC. There, in the right pane, select the Delegation tab. Each AD node has one history. The default list of users and groups can link a GPO to this node, as shown in Figure 9.36. One key to keep in mind is that the delegation of linking to an AD node does not inherit down through the AD structure. Therefore, if you delegate the ability to link a GPO to the domain node, this does not grant the ability to all OUs in the domain.

# Figure 9.36

![](img/41a83208e6906a3732620203b836cea7_555_0.png)

Delegation to link a GPO to the domain

The three delegations have the same scope, which is per GPO. Again, sometimes logic does not always make it to the keyboard for some people. If this is logical, you should be able to select a GPO in the GPMC; then, in the right pane, you can select the Delegation tab to see the delegations per GPO. This is exactly the case, and you can see the three levels of delegation per GPO in Figure 9.37. Here, you need to right-click the GPO to see the full list of delegations.

The interface does not say “Manage GPO.” Instead, it says “Edit settings, delete, modify security” for the GPO.

# FIGURE 9.37
Delegations to manage, edit, and read a GPO

![](img/41a83208e6906a3732620203b836cea7_556_0.png)

## Delegating Control Using Organizational Units

Certainly one of AD's strengths is that it can let you grant partial or complete administrative powers to a group of users, meaning that it would be possible for a one-domain network to subdivide into, say, Uptown and Downtown, Marketing and Engineering and Management, or whatever. Let's look at a simple example of how to do that.

Let's suppose there are five people in marketing: Adam, Betty, Chip, Debbie, and Elaine. They want to designate one of their own, Elaine, to be able to reset passwords. This is because "I forgot my password—can you reset it for me" is probably the number-one thing that calls IS support folks. The central IS folks are happy to have someone local to marketing take the problem off their hands, freeing them up to fight other fires. Here's the process:

- 1. Create an OU called Marketing. You can call it whatever you like, of course, but Marketing is easier to remember.
- 2. Move Adam's, Betty's, Chip's, Debbie's, and Elaine's-already-existing user accounts into the OU.
- 3. Create a group called MktPswAd, which will be the people who can reset passwords for people in the Marketing OU. Again, you can actually give it any name you want.
- 4. Make Elaine a member of the MktPswAd group.
- 5. Delegate password reset control for the Marketing OU to the MktPswAd group.

If you want to follow this along as an exercise, get ready by creating accounts for Adam, Betty, Chip, Debbie, and Elaine, except don't make them administrators. Or do it from the command line; type `net user username /add`, and you'll get a basic user account built in the Users folder. For example, create Adam like so:

```
net user Adam$$ /add
```

You've got to be sitting at the domain controller to do this.

```
net user Adam$$ /add
```

## Creating a New Unit

In ADUC, right-click the domain and then select New > Organizational Unit. A dialog box will prompt you for a name. Enter Marketing, and click OK.

## Moving User Accounts into OU

In ADUC, open the Users folder. You can move Betty, Chip, Debbie, and Elaine from the right pane to the Marketing OU. You can also use the drag-and-drop capability. Select the users and drag them.

## Creating a MktPwAdm Group

Next, create a group for the folks who can reset passwords. Again, work in ADUC. First click the Marketing OU to highlight it, and then select Action > New > Group. (You can also right-click the OU and select New > Group.) You'll see a dialog box like Figure 9.38.

You see that the dialog gives you the options of creating any of the three types of groups in Active Directory. A global group will serve our purposes well, although in this particular case—the case of a group in a given domain getting control of an OU in that domain—either a domain local or universal group would suffice. We've called the group MktPwAdm. Click OK, and it's done.

# FIGURE 9.38

Creating a new group

![](img/41a83208e6906a3732620203b836cea7_558_0.png)

Next, put Elaine in the MktPswAd group. Right-click the group for MktPswAd, and choose Properties. Click the Members tab, then the Add button, Elaine's account, Add, and then OK. You'll see that Elaine is a member of MktPswAd. Click OK to clear the dialog box.

## Delegating the Marketing OU's Password Reset Control to MktPswAd

Now let's put them together. In ADUC again, right-click the Marketing OU. Choose Delegate Control, and the first screen of the Delegation of Control Wizard will appear. The wizard is a simplified way to delegate, and it'll work fine for this first example. Next, and you'll see Figure 9.39.

# FIGURE 9.39

Before selecting a group

![](img/41a83208e6906a3732620203b836cea7_558_1.png)
