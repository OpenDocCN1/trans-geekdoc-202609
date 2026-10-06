# CHAPTER 22: ADDING MORE LOCATIONS: SITES IN ACTIVE DIRECTORY

1615

Master It Create a site to represent a new business location in Virginia Beach.

Solution Launch Active Directory Sites and Services. Right-click Sites, and select New Site. Name the site VB, select an active site link, and click OK.

Add subnets to sites. Active Directory uses users' subnets to determine which site they are. For this work, subnet objects need to be created and associated with subnets.

Master It Create a subnet to represent the 10.15.0/16 subnet that exists in the Virginia Beach location. Associate the subnet object with the VB site.

Solution Launch Active Directory Sites and Services. Right-click Subnets, and select New Sub. Enter 10.15.0/16 as the prefix, and select the VB site. Click OK.

Configure a site to replicate during certain times. It's often desirable to restrict when replication occurs between sites. If the defaults are used, replication will occur every 180 minutes. If the WAN link is heavily used during certain periods, you can configure the site so it replicates only during certain times.

Master It Configure the Default-First-Site-Name (or other site) to replicate between midnight and 5 a.m.

Solution Launch Active Directory Sites and Services. Right-click the DefaultIPSite link, and select Properties. Click the Change Schedule button. Click Replication Not Available to change the schedule that so replication isnt scheduled. Use your mouse to highlight the 5 a.m. to midnight for all seven days of the week. Click Replication Update, and click OK.

Configure Group Policy for the next nearest site. If a domain controller cannot be reached in a client's site, the client will look for any domain controller without regard how close it is. This can negatively impact logins for enterprises with several locations connected with different WAN links. You can configure Windows Vista (and newer clients) to locate and log on a DC in the next nearest site if a DC can't be located in their site. This can be done using Group Policy or the Registry Editor

Master It Which of the following Group Policy settings can be manipulated to enable the next nearest site?

+   1. Computer Configuration > Policies > Administrative Templates > System > Logon DC Locator DNS Records

+   2. Computer Configuration > Policies > Administrative Templates > System > Net Logon > DC Locator DNS Records

+   3. User Configuration > Policies > Administrative Templates > System > Logon > DC Locator DNS Records

+   4. User Configuration > Policies > Administrative Templates > System > Net Logon > DC Locator DNS Records