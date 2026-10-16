
The first place to start is using built‑in tools. Built‑in tools are especially available on Windows systems, but there are Unix‑like utilities as well. We will also look at a number of plugins available for `nmap` to gather information. Metasploit, not surprisingly, has several modules for scanning SMB systems. There are also some other utilities you can use, and we'll take a look at some of those.

### Built‑in Utilities

If you are on a Windows system, there are a number of utilities that you can make use of to gather information using SMB. Analogs exist for Linux as well. One thing to make note of with regard to the built‑in utilities is that you need to be on the same broadcast domain to make use of them. NetBIOS was originally developed to be used in a local area network, rather than with the concept of wide area networks built in. As a result, some of the functions work because systems rely on broadcasting information to the network. The implication of this is that you need to have a presence on the local network before these utilities will work.

Gathering NetBIOS statistics can be accomplished by using the program `nbtstat`. This allows you to gather data about the local network. In the following example, you can see the use of `nbtstat` to acquire data about a remote system. Using `nbtstat ‐a` presents the name table for the hostname provided. If all we knew was the IP address of the remote system, we could use `nbtstat ‐A` instead. What you'll see is that we get different pieces of information. You get a list of names down the left side, followed by a code. The code indicates the context in which the name exists, followed by the status of each name.

**nbtstat Output**

```
C:\Users\kilroy> nbtstat -a billthecat

Local Area Connection:
Node IpAddress: [192.168.86.50] Scope Id: []

           NetBIOS Remote Machine Name Table

        Name               Type         Status
     ---------------------------------------------
     BILLTHECAT     <00>  UNIQUE      Registered
     BILLTHECAT     <20>  UNIQUE      Registered
     WORKGROUP      <00>  GROUP       Registered

     MAC Address = AC-87-A3-36-D6-AA                    

```

The codes shown are from NetBIOS, and you can look up the code to determine what the name is associated with. Systems that use SMB have a number of contexts in which they can exist. What you see here is a system that is both a workstation and a file server. This means that file sharing has been enabled on this system. Additionally, though, the system acts as a workstation or client on the network. It's important to distinguish the capabilities because then each system can know the types of questions that can be asked of each of the other systems. In technical terms, each set of functionalities has procedures associated with it. We can't call procedures that don't exist, so before procedures are called on the remote systems to initiate an action, we have to know what procedures are available. `nbtstat ‐a` essentially provides that information.

What we've seen so far simply asks for all the functions (names) associated with a hostname on the network. That's one individual system. If we want to see all the hostnames that are talking SMB/NetBIOS, we need to ask for something else. We can still use `nbtstat`, we just pass a different parameter in on the command line. We are looking for resolved names. This list can come from broadcast messages when there is no centralized database for name lookups—systems announce their names and their presence when they come online and then periodically after that. It can also come from the Windows Internet Name Server (WINS), which is a central repository of names of systems on an enterprise network. Windows servers will have WINS functionality, so systems register with the WINS and all names can be resolved.

In the following code listing, you can see a list of names on the network. Since there is no Windows server and, as a result, no WINS on the network, these are all names that have been identified through broadcast messages. These systems are all macOS, but they are sharing files on the network using SMB. To do that, they need to behave like any other system that communicates using SMB.

**Listing Resolved Names with nbtstat**

```
C:\Users\kilroy
> nbtstat -r

         NetBIOS Names Resolution and Registration Statistics
         ----------------------------------------------------
  
         Resolved By Broadcast     = 47
         Resolved By Name Server   = 0

         Registered By Broadcast   = 8
         Registered By Name Server = 0

         NetBIOS Names Resolved By Broadcast
         ---------------------------------------------
                 YAZPISTACHIO   <00>
                 BILLTHECAT     <00>
                 YAZPISTACHIO   <00>
                 YAZPISTACHIO   <00>
                 LOLAGRANOLA    <00>
                 LOLAGRANOLA    <00>
                 YAZPISTACHIO   <00>
                 YAZPISTACHIO   <00>                

```

There are other functions that `nbtstat` offers, but they are more related to functionality of the local system and less relevant for enumeration. While `nbtstat` has a lot of functionality, it is, as noted earlier, only on Windows systems. There are other tools you can use if you aren't running on Windows. If you have a Linux system and have the Samba package installed, which provides services that allow Linux to communicate using SMB, you can make use of the tool `nmblookup`. This can be used to do lookups of names on the network. It can be used to query WINS as well as look up names where the systems are just broadcasting their information. For example, to get the details about the system `billthecat` as we did earlier, you would use `nmblookup ‐S ‐B billthecat`, as you can see here.

**nmblookup for Enumeration**

```
kilroy@savagewood$ nmblookup -S -B 192.168.86.255 billthecat
 Can't load /etc/samba/smb.conf - run testparm to debug it
 querying billthecat on 192.168.86.255
 192.168.86.32 billthecat<00>
 Looking up status of 192.168.86.32
      BILLTHECAT      <00> -         H <ACTIVE>
      BILLTHECAT      <20> -         H <ACTIVE>
      WORKGROUP       <00> - <GROUP> H <ACTIVE>

      MAC Address = AC-87-A3-36-D6-AA

```

Using `‐B` tells `nmblookup` to use the broadcast address that is supplied, which is just the broadcast address on the local network. To use WINS, you could use `‐R` to do a recursive lookup on the name. The flag `‐S` tells `nmblookup` to get a node status in addition to just the name status. This is the flag that provides us with the other uses. Just as we did earlier, we can see that we have a workstation (<00>) and also a file server (<20>). You'll also see from this output, just as we did earlier, that the system belongs to the workgroup WORKGROUP. Workgroups are used for ad hoc Windows networks where there is no domain controller to manage all of the systems.

#### Using the net Utility

One program that's built into Windows is the `net` utility. This is widely used for several purposes. If you wanted to connect to a shared drive on the network, you would use `net use` to connect to that shared drive. The `net` command allows you to query the network using SMB messages. As an example, the output that follows shows statistics from the workstation service on a Windows server. This shows information about network communication primarily, including bytes transferred. It can also show you the number of sessions that have been started and the sessions that have failed.
