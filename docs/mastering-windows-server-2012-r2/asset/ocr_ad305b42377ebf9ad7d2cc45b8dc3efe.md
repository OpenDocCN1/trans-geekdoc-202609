# Finding Out Which Delegations Have Been Seen, or Undelegating

It's time for not-so-good news and some bad news.

Suppose you're the administrator who set up Active Directory. Suppose, you're the second administrator—the person hired to clean up the mess that the first administrator made. You know these kinds of administrators; they're the "mad scientist"—variety who just check things in the administrative tools they solve the problem...think they and document? Heck, real administrators do not document; there is never time to document. After all, this network was hard to design; it would be hard to understand!

So, you're wondering why this did. How did he change the company's AD from the default AD when you get run DCPromo? That's a hard question to answer. First, of course, OS what he created—just in Active Directory Users and Computers, you'll see the new folders. But what delegations did he do?

Here's the not-so-good news. Sad to say, but there is no program that you can run to compare the standard AD structure and delegations to the current AD structure and split out "this is what changed" report. Considering this limitation, we'll reveal a beautiful piece of advice: always document delegations. Try to control how you can delegate, and make each delegation only sparsely. So, why is this news about not-so-good news, instead of bad news? The reason is a small tool called dscls.exe. This tool, part of the Windows Server 2012 R2 command-line utilities, provides you with detailed listings of the directory service (ds portion of the tool name) ACLs (the acls portion of the tool)

To use the tool, you must get to a command prompt:

+   1. Select Start > Run.

+   2. From there, type cmd, and a prompt window will open up.

+   3. From here, type dscls to get the full list of help that accompanies the tool.

As the help will indicate, the tool requires that you input the path to the OU you want to view in the LDAP search file. This will be something like ou=marketing,dc=bigfirm,dc=com for our example.

You can just type dscls ou-marketing,dc=bigfirm,dc=com > c:marketing_OU_delegation.txt to output the prompt window, which is not all that helpful or useful to analyze.

When you open the marketing_OU_delegation.txt file, you will see a result like that in Figure 9.48.

Now, here's the really bad news. The Delegation of Control Wizard is a little tool, but it's only a delegation wizard, not an undelection wizard. If you want to remove MkPswAdm's ability to change marketing group passwords, you have to go into the Security tab, find the references to MkPswAdm, and rip them out. We warn you, if there are some delegations you want to remove and others, you will have to manually determine which one corresponds to the delegated task you configured.