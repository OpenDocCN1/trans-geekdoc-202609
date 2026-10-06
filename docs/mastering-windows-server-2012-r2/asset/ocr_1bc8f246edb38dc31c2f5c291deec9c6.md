# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

to raise the domain functional level to Windows Server 2008. To raise the domain functional level to Windows Server 2008, perform the following steps:

+   1. Open Active Directory Administrative Center.
2. Right-click the domain, and click Raise Domain Functional Level.
3. In the Domain Functional Level box, select Windows Server 2008.
4. Click OK.
5. In the message box, click OK.
6. In the confirmation box, click OK.

Each time you move from one state to the next, you will do a series of verification activities. Once these activities are complete, you move to the next state. In this case, you have verified Active Directory and SYSVOL for functionality. You have checked the Registry Editor and raised the domain functional level. There is one detail left before you make the migration to the prepared state, that's making a backup. At this point, it is time to make certain that you have a good backup of your system state data. If things go really, wrong, you will be able to get back to this point. So, take a few minutes to make, and verify your system backup. Then you will be ready to migrate to the prepared state.

# PERFORMING THE MIGRATION

The process of migrating from the starting state to the prepared state is a short one. You will need to open a command prompt and type the following command (see Figure 7:33):

```
dfsmig /getstate 1
```

At this point, you will need to verify that the global migration state has been updated. For this, you will again use the command prompt and the following command:

```
dfsmig /getstate
```

FIGURE 7-33
DFS-R get global state 1

![](bbox=[0.176, 0.658, 0.905, 0.873])