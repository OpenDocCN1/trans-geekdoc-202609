Notice the "Replicate this attribute to the Global Catalog" check box. You can, using this check box, control which attributes can replicate in the GC.

# UNREGISTERING A DLL

To remove the Active Directory Schema snap-in from your server for security reasons, perform the following command:

```
REGSVR32 /u C:\Windows\System32\schmmg.dll
```

# The SCHEMA AND YOUR AD

Will you change the schema much or very often? Probably not. But there are few things you should bear in mind.

First, remember that there is only one schema for the entire forest; it's not meaningful to talk changing the schema for a particular domain, because any changes to the schema are changes to the schema of an entire forest. So, a bit of innocent-schema dazzling will affect every domain controller in every domain in the forest, because all of DCs will have to be notified of the changes and will have to make room for the new schema items in their copy of the schema, which burns up some CPU and disk time.

Second, will you change the schema? Usually the only thing that you'll do is when adding new server-based applications such as Exchange Server 2013 or other server-based apps that were designed with Active Directory in mind. Microsoft products will manage the schema update for you as part of the installation. You don't have to do it manually. In Chapter 25, you will read about using adprep for preparing earlier domains for Windows Server 2012 R2 This will modify the schema as well.

# KEEPING SCHEMA CHANGES ORDERLY

Inasmuch as changing schema affects the whole forest, it's reasonable to say that the schema change. You want to change it in an orderly fashion, and it'd be really bad if two people modified the schema at the same time.

For reason that there's only one schema for the entire forest. That computer can approve schema changes in the entire forest. That computer is said to have the schema FMSO role. By default, the AD places the schema FSM role on the first domain controller that you install in the first domain of the forest. So, the first DC that you set up should be a well-protected one!

You can see which computer is the schema FMSO computer like so:

+   1. Right-click the Active Directory Schema object.

+   2. Choose Operations Master to see a dialog box like the one shown in Figure 24.13.

You must be a schema admin to move the schema FMSO role.