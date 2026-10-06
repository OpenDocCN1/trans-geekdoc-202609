
This is the basic syntax for the repadmin tool:

```
repadmin <command> <arguments>
```

When using the replsingleobj command or switch, the syntax is as follows:

```
repadmin /replsingleobj sourceDC destinationDC ObjectDN
```

Both the source and destination controllers are identified with their name (such as BFI) or with their fully qualified domain name (such as BF1.Bigfirm.com).
The distinguished name (DN) follows the LDAP DN rules. For example, a computer named TestCPU in the Sales OU of the Bigfirm.com domain would have the following DN: DN=TestCPU,OU=Sales,DC=bigfirm,DC=com.
If the DN has any object from BF1 to BF2, you can use the following command:
the command wraps to multiple lines in the book, but it should be entered on a single line:

```
repadmin /replsingleobj BF1.bigfirm.com BF2.bigfirm.com
CN=TestCPU,OU=Sales,DC=bigfirm,DC=com
```

## Configuring Clients to Access the Next Closest Site

A great capability available with Windows Server 2012 R2 is the ability to teach clients what site to access if the domain controller in their site is down. Consider the Bigfirm.com enterprise shown in Figure 22.20.

FIGURE 22.20
Next closest site

![](img/41a83208e6906a3732620203b836cea7_1181_0.png)

Each site has at least one domain controller, and normally users will log onto a domain controller in their own site. But what if the domain controller in the crosstown office site goes down?
You probably wouldn't want the users to have to use a slower connection and log onto DCs in the remote office site. However, this is exactly what might happen if the next closest site isn't enabled. The DC Locator service first tries to locate a DC in the same site as the client. If unsuccessful, it then looks for any DC regardless of the location unless the next closest site setting is enabled.

The term closest site is somewhat of a misnomer. Active Directory doesn't have any concept of distance, but it does understand the cost configured in the site link properties. Although it's likely that the closest sites will have the fastest WAN links and will be configured with the lowest cost, an organization could be configured differently.

An example, the remote office could be one mile from the crosstown office but five miles from the headquarters location. The link between the remote office and HQ has a cost of 25, and the link between the crosstown office and the remote office is 100. If distance used, the crosstown office would be considered closest, since cost is considered, HQ would be identified as the closest site since its cost is the lowest.

## NEXT CLOSEST SITE NOT AVAILABLE ON PRE-WINDOWS V CLIENTS

The next closest site feature will work on Windows 7, Windows 8, and Windows Server 2008 or greater clients and servers. This feature will not affect how Windows XP, Windows Server 2003, or previous clients behave.

You can configure Windows 7, Windows 8, and Windows Server 2012 R2 servers to use the cost to locate the next closest site. These are the two methods that can be used to configure this feature:

- Group Policy
- Registry modification

## Configuring Next Closest Site with Group Policy

If you want to configure multiple clients to use the cost to determine which sites are the closest, you can modify Group Policy to do so. You can use the following steps to configure all clients in the domain.

| SITE, DOMAIN, OR OU |
| :--- |
| The following procedure takes you through the steps to configure all clients in the domain by modifying the default domain policy. However, you could slightly modify these steps to create or alter any GPO and link it to a site, domain, or organizational unit (OU) depending on which computers you want to affect. |

1. Launch the Group Policy Management console by selecting Server Manager > Group Policy Management.
2. Browse to the Default Domain Policy object within the Forest > Domains > Domain Name folder.
3. Right-click Default Domain Policy, and click Edit.

## CHAPTER 22 ADDING MORE LOCATIONS: SITES IN ACTIVE DIRECTORY

4. Browse to the Computer Configuration > Policies > Administrative Templates > System > Net Logon > DC Locator DNS Records policy folder.

5. Double-click the Next Closest Site setting, and click Enabled. Your display will look similar to Figure 22.21. Click OK.

![](img/41a83208e6906a3732620203b836cea7_1183_0.png)

6. Close the Group Policy Manager Editor and the Group Policy Management console.

You can wait until Group Policy is applied through the normal refresh cycle or use the gupdate /force command from the command to update any individual clients.

## Configuring Next Closest Site through the Registry

Group Policy allows you to configure a setting once and affect many clients. However, if you want only a single client to use the next closest site, you can modify the registry.

> BE CAREFUL WITH THE REGISTRY

You should be cautious anytime you modify the registry. Incorrectly editing the registry may severely damage your system. It is recommended that you back up all data on your computer before modifying the registry.

## CONFIGURING CLIENTS TO ACCESS THE NEXT CLOSEST SITE

You can use the following steps to enable the Try Closest Site setting for Windows 7 or 8.

1. Launch the Registry Editor by clicking Start, typing regedit in the Start box, and pressing Enter.
2. Select HKEY_LOCAL_MACHINE.
3. Browse to System\CurrentSet\Services\Netlogon\Parameters.
4. Look for a key named Try Closest Site. If it doesn't exist, follow these steps to create it:
   a. Right-click Parameters, and select New > DWORD (32-bit) Value.
   b. Rename the key as Try Closest Site.
5. Double-click Try Closest Site. Change the value to 1. Your display will look similar to Figure 22.22.

FIGURE 22.22
Modifying the registry
![](img/41a83208e6906a3732620203b836cea7_1184_0.png)

6. Click OK. Close the Registry Editor.

As a reminder, this setting is referenced only if a domain controller is contacted on the same site as the client. If the value is 1 for this key, the DC Locator process will use the cost value.

## Using PowerShell

PowerShell cmdlets are covered in many chapters throughout this book, so you've already seen many. This section highlights a few cmdlets you can use and combine to retrieve information from Active Directory. It includes some basics on the Active Directory searcher tool built into PowerShell, which can be very useful if your organization is big enough to support multiple sites.

## USING DISTINGISHED NAMES

These steps talk about distinguished names (DNs), which were covered in much greater depth in Chapter 7 and mentioned earlier in this chapter. It will take a little bit of practice before you can create a DN on the fly, but you'll find the ability to create and identify the DN useful, especially when scripting or digging into Active Directory.

1. Launch an instance of Windows PowerShell.
2. Get some information about your environment by first creating a variable to represent the domain with the following cmdlet. It populates the variable $dom with the DN of the domain. Note LDAP must be caps:
`$dom=[adsi]LDAP://RootDSE`
3. You can query any information about the domain using the $dom variable with these commands:
   a. View the naming context of the root domain:
   `Write-Host $dom.RootDomainNamingContext`
   Our result: DC=bigfirm,DC=com
   b. View the naming context of all domains in the forest:
   `Write-Host $dom.NamingContexts`
   Our result: DC=bigfirm,DC=com
   c. View the default naming context (or the partial DN of your domain):
   `Write-Host $dom.DefaultNamingContext`
   Our result: DC=bigfirm,DC=com
