
## Initial Steps

1. Open a command prompt, and change to the Rename Tools directory.
2. Enter the command `rendom /upload`.
3. Verify the existence of the state file `dclist.xml` in the Rename Tools directory and that it contains an entry for every DC in your forest.

In addition to generating the domain rename instructions and uploading them into the Active Directory, the `rendom /upload` command also generates a state file called `dclist.xml` and writes it to the current directory of Rename Tools. `Rendom` uses this state file to track the progress and state of each DC in the forest. This tracking continues throughout the remaining steps of the domain rename procedure. Refer to [Figure 4.55](#B9781931836944500106_1.xhtml#f0275) for an example of the `dclist.xml` file. It contains the states for two DCs in the Zoo.net domain called `DC1` and `DC2`, and two DCs in the Fish.zoo.net domain called `DC3` and `DC4`.

![Figure 4.55 Examining the dclist.xml State File Used for Tracking the Progress of Domain Rename](images/B9781931836944500106/f04-55-9781931836944.jpg)

Figure 4.55 Examining the dclist.xml State File Used for Tracking the Progress of Domain Rename

Every DC in the forest must have an entry in the `dclist.xml` state file. The state of each DC is delineated by the tags `< State></State >`. At this point in the rename process, all DCs are initialized to the `Initial` state. As the procedure progresses, these states will change.

## STEP 6: Push Instructions to DCs

In [Exercise 4.23](#B9781931836944500106_1.xhtml#b0130), you will trigger a forced Active Directory replication. This pushes out the domain rename instructions that you previously uploaded to the Domain Naming Master to all DCs in the forest. Then, you should verify that the DC Locator SKV records registered in DNS by each DC for the new domain names have replicated to all DNS servers that are authoritative for those records.

### EXERCISE 4.23

#### FORCING THE SYNCHRONIZATION OF CHANGES MADE TO THE DOMAIN NAMING MASTER

1. Open a command prompt, and change to the Rename Tools directory.
2. Type the command `repadmin /syncall /d /e /P /q DomainNamingMaster`. Note that Domain Naming Master is the DNS host name of the current Domain Naming Master for the forest.

![b04-20-9781931836944](images/B9781931836944500106/b04-20-9781931836944.jpg)Note

You do not have to force replication, but it will accelerate the replication of the changes to the Partitions container in the configuration directory partition to all DCs in the forest. Alternately, you can wait for replication to complete according to the delay characteristics and replication intervals of your forest.

![b04-21-9781931836944](images/B9781931836944500106/b04-21-9781931836944.jpg)Note

Use the `dsquery` utility to determine which host is the Domain Naming Master, or perform [Exercise 4.12](#B9781931836944500106_1.xhtml#b0075). In addition, be aware that the `repadmin` command-line options are case sensitive.

It is critical that all DCs successfully replicate before continuing. If `repadmin` completes successfully, the Domain Naming Master DC will have replicated to every other DC in the forest. If you get an error for some of the DCs in the forest, you must try again until all DCs in the forest have successfully received the changes from the Domain Naming Master.

## STEP 7: Verify DNS Readiness

During domain rename, the Net Logon service of each DC pre-publishes the SRV resource records to the authoritative DNS servers associated with their new domain name. The DC Locator will malfunction if these are not successfully published. Other records must also be in place for authentication and replication to take place. Refer to [Exercise 4.24](#B9781931836944500106_2.xhtml#b0135) to verify that the various DNS records for the new domain names were successfully created.

### Exercise 4.24

#### VERIFYING THE DNS SERVICE LOCATOR RECORDS

1. Click Start | Programs | Administrative Tools | DNS to start the DNS administrator console.
2. Expand the server name.
3. Expand the Forward Lookup Zones.
4. Expand the domain you want to verify.
5. Verify that the DNS records listed in [Table 4.7](#B9781931836944500106_2.xhtml#t0040) are present for all your DCs within each domain. These records are crucial to the operation of the domain.

![b04-39-9781931836944](images/B9781931836944500106/b04-39-9781931836944.jpg)Note

Do not, under any circumstances, proceed with domain rename if any of the DNS records listed in [Table 4.7](#B9781931836944500106_2.xhtml#t0040) are missing. They are all required for normal operation of the forest.

Table 4.7

Required SRV Resource Records

| Location of DNS Record | Type of Record | Purpose |
| --- | --- | --- |
| `DsaGuid._msdcs.DnsForestName` | `CNAME` | There must be one CNAME record pertaining to every DC in all authoritative DNS servers. Without it, replication will not take place from that DC. |
| `_ldap._tcp.pdc._msdcs, DnsDomainName` | `SRV` | There must be one SRV record associated with the PDC FSMO on all authoritative DNS servers. Without it, the authentication of users and computers will not function correctly. |
| `_Idap._tcp.gc._msdcs. DnsForestName` | `SRV` | There must be at least one record pointing to at least one GC on all authoritative DNS servers in the forest. This record also ensures the proper functioning of authentication for users and computers. Minimally, at least one record of this type must be present on all authoritative DNS servers. Records for the other GCs should eventually replicate. |
| `_ldap._tcp.dc._msdcs. DnsDomainName` | `SRV` | There must be at least one record for at least one DC on all authoritative DNS servers for each domain. This is another record required for the functioning of authentication of users and computers. Minimally, at least one record of this type must be present on all authoritative DNS servers. Records for the other DCs should eventually replicate to the other authoritative DNS servers. |

Now you need to check the status of every DC in the forest to verify that the Active Directory database is in a healthy state and ready to perform the domain rename instructions. Use [Exercise 4.25](#B9781931836944500106_2.xhtml#b0140) to accomplish this. The Rendom tool will issue a Remote Procedure Call (RPC) individually to each DC in the forest and update the state file `dclist.xml`.

### EXERCISE 4.25

#### VERIFYING THE READINESS OF ALL DOMAIN CONTROLLERS

1. Open a command prompt, and change to the RenameTools directory.
2. Type the command `rendom /prepare`. The `rendom` utility will check for the following:
3. Verify the existence of the state file `dclist.xml` in the RenameTools directory and that it contains an entry for every DC in your forest showing a state of `Prepared`.

| Active Directory Container | Attribute | Is Replicated To |
| --- | --- | --- |
| `Partitions` | `msDS-UpdateScript` | Every DC in the forest |
| `Partitions` | `msDS-DnsRootAHas` | Every DC in the forest |
| `Partitions` | `servicePrincipalName` | Every DC in a domain and the GC servers |

The control station computer issues an RPC to every DC in the forest when you run the `rendom /prepare` command. The results are tracked by the state file `dclist.xml`. This RPC executes on each DC to verify that its directory replica is in a healthy state and that it is ready to run the domain rename instructions. `Rendom` updates the state field in each DC section of the `dclist.xml` file to the `Prepared` status as shown by (`< State>Prepared </State >`) if it is successful. If not, check the command execution log called `rendom.log` in the current working directory. It contains valuable information about the actual tasks performed by the tool, and at what stage or on which DC the problem occurred.
