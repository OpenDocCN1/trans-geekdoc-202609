
When you restructure a domain to become a new tree root, you must pre-create two one-way, transitive trust relationships with the forest root domain. For example, suppose you have a three-level deep tree and you want to shorten it by creating a new tree. This will move the lowest domain to become a new tree-root domain. [Figure 4.50](#B9781931836944500106_1.xhtml#f0250) shows the two one-way shortcut trusts you create, and [Figure 4.51](#B9781931836944500106_1.xhtml#f0255) shows the tree-root trust relationship after the restructuring. `Stripedangel.fish.zoo.net` becomes the tree-root domain `Angelfish.net`.

![Figure 4.50 Pre-Creating a Tree-Root Trust Relationship Before the Forest Restructure](images/B9781931836944500106/f04-50-9781931836944.jpg)
Figure 4.50 Pre-Creating a Tree-Root Trust Relationship Before the Forest Restructure

![Figure 4.51 Tree-Root Trust Relationship After the Forest Restructure](images/B9781931836944500106/f04-51-9781931836944.jpg)
Figure 4.51 Tree-Root Trust Relationship After the Forest Restructure

### Preparing DNS
Any time a client requires access to Active Directory, it activates an internal mechanism called the DC locator for locating DCs through DNS. It uses SRV records for this. If no SRV records are found in DNS, the access fails. To prevent this failure, before renaming an Active Directory domain you need to be sure that the appropriate zones exist for the forest and for each domain.

After you create the DNS zones for the new domain name, your DCs will populate each zone through dynamic update. This is one of the reasons for the reboot after the execution of the renaming script. Configure the zones to allow secure dynamic updates as a good security practice. Repeat the zone creation for each domain you plan to rename.

Everything needed to support your existing Active Directory domain must be recreated to support the domain after renaming. Usually, this is accomplished by mirroring your current DNS infrastructure. As an example, say you want to rename an existing domain called [Labs.dog.com](http://www.Labs.dog.com) to [Retrievers.dog.com](http://www.Retrievers.dog.com). If the zone containing your current SRV resource records is called [Labs.dog.com](http://www.Labs.dog.com), you will need to create a new DNS zone called Retrievers, dog. com.

To analyze and prepare DNS zones for domain rename, first compile a list of DNS zones that you need to create. Second, create the forward lookup zones using the DNS tool and configure them to allow dynamic updates. The section Configuring DNS Servers for Use with Active Directory gives more detailed information.

#### Head of the Class…
##### What Happens to My Distributed File System When I Rename My Domain?
First, those of you who are not using DFS should think seriously about it. DFS allows you to redirect specific folders like My Documents out to a high-availability network location where each user’s files can be backed up and protected. Folder redirection is a Group Policy extension that allows you to identify a connection between network servers or DFS roots and the local folders that you want to redirect.

What happens to DFS when you rename a domain ail depends on how you have it configured. Think about it, If you use a domain-based DFS path like `\\domainName\\DFSRoot`, then when the domainName goes away, what happens to the path?

It goes dead, and everyone’s documents disappear, or become inaccessible. As far as the users know, all of their data is gone. Your telephone will ring by 5 a.m. the next day—guaranteed. What does it depend on, and how can you keep your telephone from ringing? If your Folder Redirection policy specifies the NetBIOS name of the domain in your domain-based DFS path, and you keep the NetBIOS name of your domain the same instead of changing it along with the DNS name, then you’re okay.

What if you want to change your NetBIOS name along with your DNS name? You could push out a new group policy and move the files to another location. Temporarily, you could point your folder redirection to a stand-alone DFS path, or even to a simple server-based share. You should do that a couple of days before the rename just to be sure it works before shaking things up again—you’ll be too busy renaming to worry about DFS at that point. Since `\\hostName\\DFSRoot` stays rock solid through a domain rename, your documents should still be available the next morning. When things settle down, restore the user files back to your domain- based DFS root and push out the old DFS policy again. That isn’t without risk, but it keeps things working.

What about home directories and roaming profiles? Same thing. Look at the pathname you specify in your policy to determine whether they’ll break when you rename the domain. Make sure to fix those beforehand.

### Configuring Member Computers for Host Name Changes
Because Active Directory is tightly integrated with DNS, member computers are designed to automatically change their primary DNS suffixes when the domain membership of the computer changes. If you rename the domain, this is treated like a membership change and the fully qualified DNS host name changes automatically to match. This is the default behavior, and you can check for it by following the steps in [Exercise 4.18](#B9781931836944500106_1.xhtml#b0105).

#### Exercise 4.18
##### Using the Control Panel to Check for Primary DNS Suffix Configuration
1. On a member computer, open the System Control Panel.
2. Click Computer Name | Change.
3. Click More, and verify if `Change primary domain suffix when domain membership changes` is selected (as shown in [Figure 4.52](#B9781931836944500106_1.xhtml#f0260)), If it is, then the computer will automatically adjust to the new primary DNS suffix.

![Figure 4.52 The System Control Panel, General Tab, More Button](images/B9781931836944500106/f04-52-9781931836944.jpg)
Figure 4.52 The System Control Panel, General Tab, More Button

4. Click OK until all dialog boxes are closed.

As an example, if you want to rename an existing domain called [Labs.dog.com](http://www.Labs.dog.com) to [Retrievers.dog.com](http://www.Retrievers.dog.com), the full DNS host name of the member computers of this domain will also change from [host.Labs.dog.com](http://www.host.Labs.dog.com) to [host.Retrievers.dog.com](http://www.host.Retrievers.dog.com) if the default behavior is in effect.

![b04-38-9781931836944](images/B9781931836944500106/b04-38-9781931836944.jpg)Note
You should check to see if this default behavior has been changed in your domain, because your rename will fail if you are not using the default setting.

The full DNS name and therefore the primary DNS suffix of a member computer changes when the domain is renamed if both of the following conditions are true:
- The primary DNS suffix of the computer is configured to update when domain membership changes. See [Exercise 4.18](#B9781931836944500106_1.xhtml#b0105) for instructions on how to check this setting.
- The member computer has no group policy applied that specifies a primary DNS suffix. See [Exercise 4.19](#B9781931836944500106_1.xhtml#b0110) for instructions on how to check this setting.

#### Exercise 4.19
##### Using the Registry to Check for Primary DNS Suffix Domain Rename Computer Readiness
1. Click Start | Run.
2. Type `regedit` and click OK.
3. Navigate to `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\System\DNSclient`.
4. If the `Primary DNS Suffix` key contains a value, then the computer will not automatically adjust to the new primary DNS suffix.
5. Navigate to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`.
6. Verify whether the value of `REG_RWORD` `SyncDomainWithMembership` is `0x1`. This value indicates that the primary DNS suffix changes when the domain membership changes. Any other value means that the computer will not automatically adjust to the new primary DNS suffix.
