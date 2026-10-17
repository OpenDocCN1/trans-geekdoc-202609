Beyond using the built-in queries, we can also directly request paths between specific objects in Bloodhound. This is useful when we have a specific account that we have control over and want to identify how to gain further access. In the scenario of Game Of Active Directory, the account samwell.tarly is a low-privilege user whose password is within the description of LDAP. To identify paths, click on the PATHFINDING button and then enter the starting and ending nodes. Bloodhound will search for ways this can be leveraged to gain access to the target.

![](bbox=[0.1, 0.2, 0.9, 0.5])

FIGURE 7.39 Using Pathfinding to find how to leverage relationships between two specific objects.

In this scenario, we’ve identified a way for samwell.tarly to link a few different permissions together to gain access to the Domain Administrators group. This relies on some permissions to a GPO which can be used on the domain. Actual abuse of this link will be left to the reader as an exercise. Our skills from the start of this chapter will start to pay off and help us explain the risk of this type of attack to a customer.

It is highly recommended to play with the various built-in queries to try and understand what activity can be uncovered in the domain. Many additional custom queries can be supplied for further analysis within BloodHound, there are several excellent community ones available at https://github.com/CompassSecurity/BloodHoundQueries. This author has additionally written a comprehensive setup and configuration guide for BloodHound Community Edition available at https://medium.com/@m4lwhere/the-ultimate-guide-for-bloodhound-community-edition-bhce-80b574595acf.

# Providing Value

BloodHound is an excellent tool that can be leveraged in many ways from identifying and exploiting attack paths to helping visualize risk to customers. Becoming familiar with this tool will make you an excellent tester to reduce risk across an enterprise. To stay up to date and understand the tool, it is recommended to visit and read the documentation for BloodHound at https://bloodhound.readthedocs.io/en/latest/. Remember, your tools are only as good as you know how to use them!