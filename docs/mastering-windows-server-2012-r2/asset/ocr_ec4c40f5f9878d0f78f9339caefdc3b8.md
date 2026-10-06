administrative template policy settings give your domain controllers the ability to support port claims and compound authentication for Kerberos armoring and Dynamic Access Control. This new policy setting is also available at the client level for Windows 8. Kerberos Authentication and Dynamic Access Control are discussed more in depth in Chapter 15, "Dynamic Access Control: File Shares, Reimagined."

There's another important reason to get at least 2003 functional level or above. You can't upgrade your forest functional level until all the domains in the forest are at 2003 functional level. You can also not take advantage of read-only domain controllers unless your environment is at least a 2003 functional level.

# Forest Functional Levels

When you upgrade DCs in an existing forest or if you create a new forest, 2012 ensures for safety that not all DCs and domains are entirely 2012 based, and so will not stretch your strings to use all the new capabilities that 2012 offers all the domains in the forest are operating at domain functional level of 2012. Unless you are creating a new-forest using Windows Server 2012 R2 organizations will need to go through an upgrade process from 2008 to 2012 R2. After that process, you will need to raise the forest's functional level.

You raise a forest functional level with Active Domains and Trusts (Server Manager ▷ Active Domains and Trusts). Right-click the icon in the left labeled Active Directory Domains and Trusts, and you will see the dialog box in Figure 24.9. Notice that you don't right-click the domain icon. If you right-click the domain icon, you'll see the Raise Forest Level option.

FIGURE 24.9

Raising a forest's functional level

![](bbox=[0.315, 0.523, 0.725, 0.733])

In Figure 24.9, this example, the forest functional level is as high as it can just go with the domain functional level. In addition, you can't lower the functional level.

The nice thing is you can have domains running at a lower operating system functional level in a forest that is operating on a higher operating system functional level. It's uncommon to see a Windows Server 2008 domain in a Windows Server 2012 R2 forest. They work together and on different levels to leave room for migrations and interoperability between operating systems. As long as the functional level is Windows Server 2003 or higher, the domain can be part of a Windows Server 2012 R2 forest.