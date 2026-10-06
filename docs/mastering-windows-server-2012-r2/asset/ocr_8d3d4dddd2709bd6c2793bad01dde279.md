# Understanding Transitive Forest Trusts

Since we can't graft forests together, we can't add a forest to another one. The best we can do is create a trust. The external trust is adequate for sharing resources across one domain. The forest trust is best for multiple domains. Forest trusts can only be utilized by domains running at least the 2003 forest functional level.

Like the automatic trust relationships, the forest trust provides a gateway for all domains in forest to trust the domains in other. Thus, Test.com buys Apex.com, both of which have an existing forest. Test.com wants its forest to work with Apex.com, so it creates a single forest-to-forest root trust, and trust is universal.

This is good news, but there are a few reasons why this may not be all that Test.com and Apex.com want. Here's:

+   - First, this is only if Test.com and Apex.com are upgraded to at least the Windows 2003 forest functional level. Ideally you would want to upgrade all of your domains and domain controllers to Windows Server 2012 R2 so that you get to use all of the great features provided by the most up-to-date technology.
- Second, two transitive forests do not exactly equal a single forest as far as AD-aware software is concerned. (Read: Exchange Server. Although it's not the only one, it is the most important one:) That's because there is not very important bit of "glue" binding forests together in addition to their transitive trusts: the global catalog.
- Third, and this is probably a smaller issue, forest-to-forest trusts are, believe it or not, transitive _across forests_ . _forests_ . By that we mean if forest 1 trusts forest 2, then as as you've seen, all of forest 1's domains all of forest 2's domains, and vice versa.

Exchange serves your enterprise as a big firm no how many domains it has because Exchange Server thinks "all domains sharing a global catalog equal one another." So, here's the problem: two separate transitive forests still have two separate global catalogs.

But now let's say you set up a transitive trust between forest 2 and forest 3. Now all of forest 2's domains trust all of forest 3's domains (and vice versa). But what about forest 1 and forest 3—what relationship do they have? Now, it turns out. Forest-to-forest trusts do not "flow through." You'd have to build a separate trust between forest 1 and forest 3 in order to have every forest around every other one.

# Manually Creating Trusts

The primary tool for managing trusts is the Active Directory Domains and Trusts (ADDT) console. Although those "old-school leatherneck admins" think wizards are for "latex-sipping pencil-neck admins," the ADDT's New Trust Wizard gets the job done when you consider the complexity of the netdom command.