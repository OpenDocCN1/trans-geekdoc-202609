# CHAPTER 24 CREATING LARGER ACTIVE DIRECTORY ENVIRONMENTS: BEYOND ONE DOMAIN

There doesn't seem to be a way to enable success/failure logging to the event log. But there is a diagnostic program that you can use to figure out whether you're connected to a useful time server. On all Windows machines, the program is called w32tm. Although it's not as pretty as netquery, it's free and integrates with the Time service.

To find out a system's time server is working, open a command prompt, and w32tm /resync. It'd look like this:

```
c:\w32tm /resync
Sending resync command to local computer...
The command completed successfully.
```

Or, if it didn't work, you'd see:

The computer did not resync because no time data was available.
This service requires that port 123 be open to the outside world, so set your firewalls appropriately.

# Trusts

As discussed in the chapter, computers within a domain allow users domain controllers to access their resources. The computers trusted the domain controllers. For users outside the domain, an explicit trust was created between the domain controllers to authorize the users to access the computers' resources. This section will go into more detail on concepts behind these explicit trusts and how to administer them.

The trusts have characteristics that can be configured when they are created. They can have one direction or two. They can be transitive or nontransitive. Each of these characteristics is considered in the type of trust that it will be created.

You can create and administer the trust using the Active Domains and Trusts snap-in. In addition, the netdom utility can perform the same operations.

# Defining the Domain: "Trust"

So now if you have a server that can authenticate a user, a DC. But for whom will it do authenticating? Not just system. A PC (whether workstation or server) can only use a domain's DCs to authenticate if PC "joins" a domain to become a "member". Systems that are not members of any domain can authenticate using the user accounts in their local SAM database; systems that domain members can either authenticate a user with those local SAM accounts or one of their domain's DCs to authenticate the user. In the world of Microsoft networking, we say that systems in any domain trust only their local SAM but systems in a domain trust their SAM and their domain's DCs. Joining a domain creates a relationship between the PC and the DCs. Before a will trust a domain controller to provide login services, and a domain controller trust a workstation enough to provide those login services, Microsoft software requires the agreement of both a domain-level administrator and of a workstation-administrator.

When you join a machine to a domain, you are typically logged in using an account that workstation recognizes as a local administrator, but when you try to join the machine to a domain, you'll see that the domain then comes back and says, "Now I need to see an administrative account that the domain recognizes." Just as a treaty between two countries