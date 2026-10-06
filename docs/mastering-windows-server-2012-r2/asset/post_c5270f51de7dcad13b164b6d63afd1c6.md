
# 524 CHAPTER 9 GROUP POLICY: AD'S GAUNTLET AND ACTIVE DIRECTORY DELEGATION

Next, you will have to tell it that you're about to delegate some power to a particular group, so you have to identify the group. Click Add, and choose the MkPswAdm group. After choosing MkPswAdm and clicking OK to dismiss the AD dialog box, the screen looks like Figure 9.40. Now click Next, and you'll get a menu of possible tasks to delegate; as you see in Figure 9.41.

FIGURE 9.40
MkPswAdm selected

![](img/41a83208e6906a3732620203b836cea7_559_0.png)

FIGURE 9.41
Options for delegation

![](img/41a83208e6906a3732620203b836cea7_559_1.png)

Once you do a bit of exploring here, you will see that there are, many functions that can be delegated. Rather than force you to wade through a long list of things that you'll never care about, however, Microsoft picked the top dozen or so things that you'd be most likely to want to delegate, one of which is the ability to reset passwords. We've selected that in the figure, click Next, and the final screen in the wizard appears, as you see in Figure 9.42. Click Finish, and it's done.

# FIGURE 9.42
Confirming your choices

![](img/41a83208e6906a3732620203b836cea7_560_0.png)

Remember, delegation lets designate a set of users who have some kind of control over a set of users and/or computers. You accomplish that by putting the controlling users into a group, putting the things you want them to control into an OU, and then delegating the OU to the group.

## Advanced Delegation: Manually Setting Permissions

Although the previous scenario is nice—useful—example, it only hints at the power of delegation. You actually needn't need the wizard to delegate; it makes things simpler for a range of common tasks.

### BEST PRACTICES FOR DELEGATION

Delegation is a powerful tool for administering your network. If it is used carefully, it will prove quite helpful. So far in this section we have mentioned a few good practices to use when delegating; we'll expand on these and explore more: This facilitates security as well

- Create groups and OUs that have delegation applied to them: This facilitates security as well administration.
- Avoid assigning permissions directly to a user: Create a group (see the earlier discussion), and place the user in that group. Creating a group to house one user is not burdensome as it might seem initially; in fact, it will make your administrative life much easier than trying to track why this one individual can still perform actions that she shouldn't.
- Assign the least amount of permissions to users and groups. This will help make your network secure. Users might think they are entitled to full control for everything, but they rarely, ever, require it.
- Use full control sparingly: Full control can backfire on when users or groups taking advantage of your legacy. Full control gives the user an opportunity to work with an object's permissions. This means the users could give themselves greater permissions than the administrator intended. In addition, if someone gains control of this account, that person could cause more mayhem than they would otherwise.
- To further ensure security and enhance good administration techniques, delegate object creation and object management to different groups: This is known as two-person integrity (TPI). If you split the responsibility between two individuals or groups, there is less likelihood of mismanagement by either. For example, you give one group of administrators the ability to create groups in an OU, where you give a different group of administrators the ability to control the group's members.
- Create Tasks: Task views are great when you want to delegate tasks to help-desk personnel or other groups that require some permissions but don't have access to the full console. This technique can help train new administrators before you give them the keys to the domain.

You can delegate at levels higher than an OU, but avoid doing this as a rule. If you delegate permissions at the domain level, that user or group could have a potentially far greater impact on your network than you anticipated.

## STICK AROUND

Even if you're not interested in delegation, stay with this example. It shows how to navigate the three levels of progressive complexity in Windows Server 2012 R2 security dialog boxes.

Here's how you can directly manipulate delegation:

1. First, open ADUC, and select View ➤ Advanced Features. New items will appear on the screen, as in Figure 9.43.
2. Right-click the Marketing OU, and choose Properties.

You'll get a properties sheet with a Security tab. (By the way, without Advanced Features enabled, you'll not have the Security tab available).

3. Click on it, and you'll see something like Figure 9.44.

I've scrolled down a bit to show what the dialog box tells you about the MkPwAdmin group. It appears that the group has powers that can only be described as “special”

# FIGURE 9-43
ADUC with
View Advanced
Features enabled

![](img/41a83208e6906a3732620203b836cea7_562_0.png)

# FIGURE 9-44
Security tab on Marketing OU

![](img/41a83208e6906a3732620203b836cea7_562_1.png)

In theory, you should be able to click any of the ACEs in the top part of the dialog box, and in the bottom part you see what powers ACE gives the thing name in the ACE. For example, you will see in Figure 9.44 that MkPwAdm has “special” powers. That’s one reason we don’t like this dialog box all day, because “special” doesn’t say much. The other reason is that this dialog box only shows a really simplified list of possible powers, so what you will see is sometimes misleading. That’s why it’s nice that you can zoom in one level by clicking the Advanced button.

4. Do that in ADUC, and you'll see a screen like Figure 9.45.

FIGURE 9.45
Advanced settings for Marketing OU

![](img/41a83208e6906a3732620203b836cea7_563_0.png)

5. Scroll down to highlight MkPswAdm and you see two entries for it: One lists the “special” permission, while the other does not list anything for the permissions, which is not very helpful at all.

6. Click on Edit when you have one of the entries highlighted, and you'll see something like Figure 9.46.

Here that we have given MkPswAdm the ability to read and write “Descendant User objects” properties, but only the pwdLastSet property—AD along for being able to select the box that indicates “User must change password at next login,” which is available in the Reset Password dialog.

7. Now, go back and look at the other record for MkPswAdm and edit it, and you'll see Figure 9.47.

As you can see from there, [text cut off or incomplete based on OCR source provided]...

# FIGURE 9-46
Specific to swAdm abilities

![](img/41a83208e6906a3732620203b836cea7_564_0.png)

# FIGURE 9-47
Giving the power to reset passwords

![](img/41a83208e6906a3732620203b836cea7_564_1.png)
