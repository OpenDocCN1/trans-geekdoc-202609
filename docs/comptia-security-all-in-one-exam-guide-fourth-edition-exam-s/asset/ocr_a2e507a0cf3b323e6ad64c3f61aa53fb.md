# # Secure Network Design

In this chapter, you will

+   - Study network design elements
+   - Explore network components
+   - Discover how subnets are created
+   - Learn how to implement common protocols
+   - Learn how to implement common services

Secure network design is an objective that has component elements in hardware, software, and policies and procedures. Proper design begins with understanding the objectives of the network. The proper implementation and use of protocols are discussed with respect to achieving the design objectives.

# ## Network Design Elements and Components

Unlike single servers, networks exist as connections of multiple devices. A key characteristic of a network is its layout, or topology. A proper network topology takes security into consideration and assists in “building security” into the network. Security-related topologies include separating portions of the network by use and function, strategically designing in points to monitor for IDS systems, building in redundancy, and adding fault-tolerant aspects.

![](bbox=[0.052, 0.72, 0.13, 0.77])

> **EXAM TIP** This chapter is about designing networks with components. During the exam, it is expected that you will be familiar with basic network design elements and components.

# ## DMZ Security Zones

The first aspect of security is a layered defense. Just as a castle has a moat, an outside wall, an inside wall, and even a keep, so, too, does a modern secure network have different layers of protection. Different zones are designed to provide layers of defense, with the outermost layers providing basic protection and the innermost layers providing the highest level of protection. A constant issue is that accessibility tends to be inversely