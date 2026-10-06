
# Forests

When considering additional domains in Active Directory, we get back to nature using familiar terms such as forests and trees. Although you can't start a forest without a tree, we'll begin with the concept of a forest.

After creating the first domain, you can create additional domain controllers for the same domain or create domain controllers for new domains in relation to this first domain. When additional domains are created in relation to this first domain, as you will do later in the "Creating Multiple Domains" section, not all the Active Directory database is replicated to those domain controllers. The domain partition and schema patterns will be replicated to every domain controller in the forest. The phase in the forest means a group of domains that replicate the configuration and schema patterns.

In addition, being in the forest means that the domains are built in relation to each other. The relation is the trust between the domains when you add multiple domains to a forest. A nonconfigurable "two-way transitive" trust is built automatically between the new domain and one in the forest. This means groups of domain can access resources such as files and printers in the other domain, and vice versa. In fact, any domain can access resources in any other domain in the forest.

Getting back to nature, when you create the first domain on the first domain controller, you created a one-domain, one-tree forest. It is important to understand that building a domain from scratch, as you did in Chapter 7, "Active Directory in Windows Server 2012 R2", will create a stand-alone pristine forest that doesn't interact with anything else. It is just like you find in nature. A forest is a collection of trees. It is a security boundary for all the furry woodland creatures to remain hidden and safe. They can peacefully forage for food under the shade of the trees whose branches and roots are interconnected. The furry woodland creatures don't go around into other forests ("Don't go out into the meadow, Bambi. It's not safe"). So, separate forests don't share information unless manually configured to do so, and users don't venture into the other forests on their own. In addition, you can add more trees to a forest. Roots of trees do not extend to the other forests next to each other and expect them to be unified. The back-to-nature analogy works.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# Trees

When creating a new domain in an Active Directory forest, you have to name it. Primarily, there is a group of domains in the forest with the same name, or namespace.

# THE ROOT OF A FOREST

You would think we were finished with this back-to-nature analogy. However, we have to modify it. The root of a tree is the new namespace for a group of domains such as the Test.com namespace. The root domain of a forest of Active Directory domains is the first domain that you installed in the forest. Occasionally, it will be referred to as the forest root. It is commonly depicted at the top of the tree.

For example, the first domain or root domain was named Test.com. Thus, you can assign a name to the next domain as East.Test.com. Thus, it shares the same name Test.com, and it is part of the same tree. If you create another domain named Consolidated.com, it doesn't have the same name as East.Test.com. Consolidated.com is considered a child domain to Test.com. Consolidated.com is a new tree within the forest. Consolidated.com is also a root tree even though it has no child domains.

In an Active Directory forest with just a couple of domains, this doesn't make much difference, specifically when it comes to accessing resources through the trust relationships. Things are pretty much alike. With several domains, the effect of how the domains are impacts the trust relationships.

# KERBEROS AND TRUSTS

Kerberos authentication is similar to dating in high school. Savvy guys learn getting a date can't be done by simple pick-up lines or cute smiles; they learn to network. They have to get someone for them.

Say you see a potential date in the halls of your school, but you don't know her. You can't talk to her directly, and there's security device name Mother who gets hot and bothered when you call her house. But by your security device, Mom knows the other security device; they're friends. So, you ask your mom to talk to her mother to initiate conversations between the user (you) and the resource (cute potential date).

When your mom isn't friends with the other security device, she knows of another friend who is. This is the forest root of the neighborhood; she's a friend to everyone. Your mom talks with her friend, who talks to the mother of the cute date. Ba-da-bing, you're there!

Logically, the trust relations between the domains are either parent-child or forest-tree relation. As we mentioned, East.Test.com is a child domain to Test.com, so it has a parent-to-child relation. Consolidated.com has a forest root–tree root relation. Figure 24.1 illustrates the trust relationship of the forest.

# CHAPTER 24 CREATING LARGER ACTIVE DIRECTORY ENVIRONMENTS: BEYOND ONE DOMAIN

FIGURE 24.1
Active Directory forest example

![](img/41a83208e6906a3732620203b836cea7_1225_0.png)

Kerberos works in this fashion across the domains' trust relations. A user account starts with its domain controller for a voucher (ticket). If the resource is in another domain, it has to travel across the trust relations to the resource domain. It needs to go up the parent-child trust, across and, needed, down the other tree's parent-child path. If the user is in Eacoast.Test.com, this means the user must contact the Eacoast.Test.com domain controller. If the resource is in Consolidated.com, the Eacoast.Test.com domain controller contacts one in Test.com. The Test.com domain controller needs to contact a domain controller in Consolidated.com. It takes time to get to the resource because that is the path the automatic trusts provide. Having taller trees means more traffic, more delay. If you find yourself within a large organization that houses many domains, instead of hopping from one domain to another, you could always create a shortcut trust, providing a direct link between two domains that are far away from the.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You Must Build Trees and Forests

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You CAN'T GRAFT OR PRUNE

The security boundaries in place by both domains and forests help you control access and security within the environment. objects. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You CAN'T GRAFT OR PRUNE

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You CAN'T GRAFT OR PRUNE

The security boundaries in place by both domains and forests help you control access and security within the environment. help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You CAN'T GRAFT OR PRUNE

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You MUST BE AN ENTER ADMIN

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# You MUST BE AN ENTER ADMIN

The security boundaries in place by both domains and forests help you control access and security within the environment. Each domain and forest acts as a security toll booth for objects that want to traverse between and share information. These checks and balances help keep the environment secure. It's the forest's responsibility to be the overlapping security umbrella for objects that live inside the forest. If you want to ensure one portion of your network is locked down, you may consider using a separate forest to prevent sharing resources with others.

# PLANNING YOUR ACTIVE DIRECTORY ENVIRONMENT

Before you promote the first domain controller, you need to consider the overall vision of the Active Directory network. In addition to the organizational unit structure, DNS namespace, domain controller placement, and replication, which are all part of a single-domain plan, you
