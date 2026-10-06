# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

2008 and higher. You don't have to run adrep.exe on a domain controller; you can run remotely on a Windows server that is a member of a domain or a workgroup server. If you execute adrep..exe /7, you get all the available options.

If you need to extend your schema from a 64-bit Windows 2008 server, you need to type the following command:

```
Adrep /forest w2kdomain.com /user administrator /userdomain w2kdomain.com /password P@ssword
```

After successfully extending the schema, you can run the following command to extend the domain:

```
Adrep /domainrep /gprep w2kdomain.com /user administrator /userdomain w2kdomain.com /password P@ssword
```

In order to extend your for Read-only Domain Controllers you need to execute the following command:

```
Adrep /rodcp /domain w2kdomain.com /user administrator /userdomain w2kdomain.com /password P@ssword
```

The better news is that you don't have to execute adrep.exe at. In Windows Server 2012 there is a new Active Directory Domain Services Configuration Wizard, which you used earlier in this chapter to promote your first domain controller. This wizard is available after you have the Active Directory Domain Services role installed. The wizard takes care of all necessary steps you need to take to successfully promote your Windows Server 2012 member to a domain controller. Microsoft has integrated adrep.exe into this wizard to make the promotion as comfortable as possible.

If you are going to promote your server and you have provided all the necessary information, once you click Install, the wizard checks the environment and prepares the forest, schema, and domain, as shown in Figure 7.48.

# FIGURE 7.48 ADDSCW preparing the target domain

![](bbox=[0.333, 0.612, 0.883, 0.933])