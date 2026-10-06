
## FSMO Roles

Active Directory has five FSMO roles:

- Schema Master
- Domain Naming Master
- Relative Identifier (RID)
- PDC Emulator
- Infrastructure Operations Master

There is only one Schema Master FSMO in the entire forest and similarly only one Domain Naming Master FSMO. Each domain in the forest, however, has its own RID, PDC, and Infrastructure Operations Master.

We look at each role's function and consider any requirements relating to its assignment to domain controllers.

## Schema Master

Schema is the structure for the AD database—the fields. It is the definition of things in the database, such as the usernames, passwords, and so on. In senses, the directory to your Active Directory.

## EXAMINING THE SCHEMA WITH THE SCHEMA SNAP-IN

You can look at the schema with the Active Directory Schema snap-in. However, you'll have to follow these steps to run it:

- 1. Open a command prompt, and type regsvr32 schemamgmt.dll. You should get a message box that says "DllRegisterServer in schmmmgmt.dll succeeded." Click OK to clear it.

- 2. Open a Run dialog box, enter mmc /a, and then press Enter to start the Microsoft Management Console in Author mode.

- 3. Click File and then Add/Remove Snap-in.

- 4. Select the Active Directory Schema snap-in, click Add, and then click OK. The Active Directory Schema snap-in is now loaded and ready for use.

You'll see a similar Figure 24.11.

Here, we've highlighted the part of the schema that tells you that there is an attribute called userPrincipalName, which is one of the login names available to the user.

- 5. Double-click, and you'll see a dialog box describing its properties, they'll probably grayed out, even if you're a member of the Enterprise admins group.

Recall that even enterprise admins can't modify the schema—you must be a member of the Schema admins group to do that. But if you're a schema admin, then you'll see the properties page with everything enabled, as in Figure 24.12.

## FIGURE 24.11
Active Directory Schema snap-in

![](img/41a83208e6906a3732620203b836cea7_1249_0.png)

## FIGURE 24.12
Properties page for UPN

![](img/41a83208e6906a3732620203b836cea7_1249_1.png)

Like the enterprise admin, a schema admin is a user account that is a member of a group within the forest root domain. The group is named Schema Admins. By default, the Administrator account of this domain pop this.

Notice the "Replicate this attribute to the Global Catalog" check box. You can, using this check box, control which attributes can replicate in the GC.

## UNREGISTERING A DLL

To remove the Active Directory Schema snap-in from your server for security reasons, perform the following command:

```
REGSVR32 /u C:\Windows\System32\schmmg.dll
```

## The SCHEMA AND YOUR AD

Will you change the schema much or very often? Probably not. But there are few things you should bear in mind.

First, remember that there is only one schema for the entire forest; it's not meaningful to talk changing the schema for a particular domain, because any changes to the schema are changes to the schema of an entire forest. So, a bit of innocent-schema dazzling will affect every domain controller in every domain in the forest, because all of DCs will have to be notified of the changes and will have to make room for the new schema items in their copy of the schema, which burns up some CPU and disk time.

Second, will you change the schema? Usually the only thing you'll do is when adding new server-based applications such as Exchange Server 2013 or other server-based apps that were designed with Active Directory in mind. Microsoft products will manage the schema update for you as part of the installation. You don't have to do it manually. In Chapter 25, you will read about using adprep for preparing earlier domains for Windows Server 2012 R2 This will modify the schema as well.

## KEEPING SCHEMA CHANGES ORDERLY

Inasmuch as changing schema affects the whole forest, it's reasonable to say that the schema change. You want to change it in an orderly fashion, and it'd be really bad if two people modified the schema at the same time.

For reason that there's only one schema for the entire forest. That computer can approve schema changes in the entire forest. That computer is said to have the schema FMSO role. By default, the AD places the schema FSM role on the first domain controller that you install in the first domain of the forest. So, the first DC that you set up should be a well-protected one!

You can see which computer is the schema FMSO computer like so:

- 1. Right-click the Active Directory Schema object.

- 2. Choose Operations Master to see a dialog box like the one shown in Figure 24.13.

You must be a schema admin to move the schema FMSO role.

## 1216 CHAPTER 24 CREATING LARGER ACTIVE DIRECTORY ENVIRONMENTS: BEYOND ONE DOMAIN

## FIGURE 24.13
Viewing the FSMO

![](img/41a83208e6906a3732620203b836cea7_1251_0.png)

## PLANNING FOR SCHEMA CHANGES...AND CONFLICTS

Before leaving the subject of schema, we will offer a thought about how it will affect your organization. There are few AD-aware applications. But now let's consider what happens if conflicts arise. Let's imagine that you are at a university with lot of departments. The university's forest has many domains—Chemistry, English, Microbiology, and Geology—that all live in a single forest. Now imagine that Astronomy just wants a new application that will aid its professors, and so they put it in AD. It adds a few things to the schema, including a field, which stores brightness. Suppose Geology needs a new application that will help them in seismology, which also adds a few things to the schema—such as a field, where they store power. What happens when Geology tries to install an application that already exists? Well, to make a long story, not all conflicts are possible. Our point is this: Geology did not know when it installed its app would conflict with an existing one. Well—and here's the part—every forest should consider having a test and running all the time, with a DC or two are running independently. Prior to rolling out any server-based apps, you should test them on a lab to see whether they changes will make AD be. This is how total cost of ownership doesn't seem quite compelling when Windows Server 2012 R2 offers Hyper-V. This gives you a reason to play around with. Basically, AD is just another piece of software that says if you want to use me, you'll have to modify the way you do, and seems fairly backward—sort of design doesn't fit your hand.

## Domain Naming Master FSMO

You've already made this one—we used this FSMO as the example of why you'd need an operations master in the first place. There is only one of these for the entire forest. As with the schema operations master, the AD places the Domain Naming Master role on the first controller in the first domain.

## DOMAIN NAMING MASTER PLACEMENT

The Domain Naming FSMO role should be placed only on a DC that is also a global catalog server. Apparently the AD developers got a little lazy and decided that, inasmuch as the global catalog knows about things from all over the forest, the Domain Naming FSMO exploit the GC's knowledge.

## RID Pool FSMO

One of the things a native AD domain controller can do is to create accounts (user and machine) without having to find some "central" or "primary" DC. In the Windows Server world, everything has a unique identifier, called its security ID (SID). SIDs look like this:

S-5-21-D1-D2-D3-RID

The 5-21 to all SIDs. What we've called D1, D2, and D3 are actually three randomly generated 32-bit numbers. When AD creates a domain, it generates these three unique 32-bit numbers, and they remain constant for any SID generated in that. And it's not just a matter of a separate D1/D2/D3 for a domain—the local SAM on a workstation or member server also has its own set of three unique 32-bit numbers.

So, for example, if you created a domain named Bigfoot and it happened to come with D1=55, D2=1044, and D3=7, then SID in Test would look like S-5-21-55-1044-7-something, where something is a 32-bit number. In all words, all SIDs in a domain are identical except for the last bits. These bits are the relative difference between SIDs; bits before are called the relative identifier (RID). RIDs are fixed, such as the SID for the default administrator account on a computer.

Anyway, if a DC needs to generate a new SID, then it knows the first part of the SID. It then pools up 500 RIDs in a list. Each DC can then create up to 500 accounts before it has to go back to one central DC, which then doles out 500 RIDs. The computer handles the 500 RID bunches using the RID operations master. By default, it is the first DC installed in a domain. Note that there is an RID FSMO for each domain, not just one per forest.

You can view the RID FSMO assignment in the Active Directory Users and Computers snap-in. In the snap-in, right-click the domain object, and choose Operations Master from the context menu. The dialog displayed in Figure 24.14 shows the RID Operations Master assignment as BF1.Test. The other tabs, PDC and Infrastructure, show the assignment of the PDC Emulator and Infrastructure Master roles for the domain.
