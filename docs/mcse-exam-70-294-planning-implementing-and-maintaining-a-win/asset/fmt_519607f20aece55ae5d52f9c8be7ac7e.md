
![wrong](images/wrong.png) Answer A is incorrect because the `Properties` of the server will not show any `GC` settings. Answer D is incorrect because the `GC` role is manually enabled or disabled, and no automatic reassignments happen during addition of `DCs`.

### 3. You have a new attribute that needs to be added to the GC. You have the `Schema Admin` snap-in open. How you do make sure an attribute is included in the GC?
A. Expand the `Attributes` section, right-click the attribute you want to include, and select `Properties`. On the `General` tab, make sure that `Replicate this attribute to the GC` is selected.
B. Expand the `Attributes` section, right-click the attribute you want to include, and select `Properties`. On the `General` tab, make sure that `Allow this attribute to be shown in advanced view` is selected.
C. Expand the `Attributes` section, right-click the attribute you want to include, and select `Properties`. On the `General` tab, make sure that `Index this attribute for containerized searches in the Active Directory` is selected.
D. Expand the `Attributes` section, right-click the attribute you want to include, and select `Properties`. On the `General` tab, make sure that `Index this attribute in the Active Directory` is selected.

☑ A. Answer A is correct and will include the attribute in the GC as long the check is in the box that says `Replicate this attribute to the GC`.

![wrong](images/wrong.png) Answer B is incorrect because allowing the attribute to be shown in advanced view doesn’t add the attribute to GC. Answers C and D are incorrect because those options deal with indexing the object for faster queries.

### 4. You recently made your new staff member a member of the Universal Group named Enterprise Admins. The new staff member is located at a branch office. When the user logs off and then back on, he notices that he cannot get to some of the Administrative tools. You recently added the user to the Universal Group and you have a 56 K link between your branch office and your main office. Your GC server is at the main office. What could be the problem? (Choose all that apply.)
A. You cannot add users to Universal Groups, only to Global and Domain Local groups.
B. You have Universal Group caching turned on and the cache information hasn’t refreshed since this morning.
C. Transmission of GC data is failing across the WAN link.
D. GC replication doesn’t support 56 K links.

☑ B and C. You could have Universal Group caching enabled, which could cause old information to be retrieved from the cache on the DC at the branch office. The GC has to be able to transmit data on port 3268, and this might be failing if the workstations or DCs have no way to transmit information between the corporate office and branch office.

![wrong](images/wrong.png) Answer A is incorrect because users can be members of Universal Groups. It is not a recommended method to keep users organized, however. Generally, you would make Domain Local or Global Groups members of the Universal Group. Answer D is incorrect because the speed of the link doesn’t prevent replication or sending of data. However, the slower the link, the slower the query process will be.

### 5. You have a network with a main office and a satellite office. The functional level of your network is Windows 2000 Native. The satellite office has a DC. The main office has a DC and a GC server. You encounter a problem with the link between the main office and the satellite office. You are concerned that users will not be able to log on at the satellite office because they cannot access the GC. To your surprise, they are still able to log on to the domain. How is this possible?
A. The DC at the branch office could be set to cache Universal Group information, allowing clients to still log on.
B. The GC isn’t required for logon, simply for searching the directory after you are logged on.
C. The DC at the satellite office is operating in the role of Schema Master and can authenticate without a GC server.
D. The users are logging on locally and not authenticating to the domain.

☑ A. The caching of Universal Group information can be cached on the DC at the satellite office, allowing authentication to still function.

![wrong](images/wrong.png) Answer B is incorrect because the GC has a lot to do with logging on. Answer C is incorrect because the role of Schema Master has nothing to do with accessing the GC. Answer D is incorrect because as the questions states, the users are logging onto the domain.

### 6. You have multiple locations that are part of the Default-First-Site-Name site. These locations are in Florida, Oregon, and Iowa. You have instituted GC servers at each location. While monitoring your network, you are noticing a lot of replication traffic between the locations. How can you remedy the amount of replication traffic and how that traffic is handled?
A. Implement the use of Subnet objects
B. Implement the use of Object classes
C. Implement the use of sites
D. Implement the use of site connectors

☑ C. The use of sites will help optimize the replication of traffic by using compression for intersite replication.

![wrong](images/wrong.png) Answers A, B, and D are incorrect. These are other objects in the Active Directory, but not the type of objects we were looking for. The Subnet object defines a subnet on your network. The Object class is a component of the schema that defines the object type. Site connectors help in connecting two different site objects.

### Working with the Active Directory Schema

### 7. You are working with the Schema Admin snap-in and cannot make any changes. You created a network administrator equivalent account in the forest root domain but cannot modify the schema. Why?
A. You must be a member of the Enterprise Admin group to modify the schema.
B. You must be a member of the Schema Admin group to modify the schema.
C. You must be a Domain Admins member in each domain in the forest to modify the schema.
D. Only the initial Administrator account during forest creation can modify the schema.

☑ B. You must be a member of the Schema Admins groups to make changes to the schema.

![wrong](images/wrong.png) Answer A is wrong because the Enterprise Admins group cannot modify the schema. Answer C is incorrect because even if you are a Domain Admin in every domain, you still cannot modify the schema without being a member of Schema Admins. Answer D is incorrect because, although the initial Administrator account is part of the Schema Admins by default, it isn’t the only account allowed to make schema changes; other accounts can as long as they are members of the Schema Admins group.

### 8. You are a network administrator and you want to modify an attribute that is associated with one of your user accounts. How do you do this?
A. Open Active Directory Users and Computers and change to advanced view. This will allow you to modify the properties of the attributes in the user account for which you need to make the change.
B. Open Active Directory Sites and Services. Open the Properties for the site containing the attribute and make the modifications.
C. Open the Schema Snap-in, expand Objects, and select the User object to modify the associated attributes.
D. Open the Schema Snap-in, expand Attributes, and find the attribute you want to modify.

☑ D. The Schema snap-in is used to make changes to attributes, by selecting the attribute you want to modify and selecting Properties.

![wrong](images/wrong.png) Answers A and B are incorrect because ADUC and ADSS do not allow for schema modifications. Answer C is incorrect because it references the Objects section instead of the Attributes section.

### 9. You are explaining the various attributes to a fellow network administrator. You are showing her the properties of a User account, and your new network administrator asks what the Other button means with regard to various attributes. What do you tell her?
A. Those attributes are multivalued attributes.
