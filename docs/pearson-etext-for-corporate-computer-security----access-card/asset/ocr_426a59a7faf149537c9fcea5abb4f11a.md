still need access to internal resources. Employees working remotely and partnerships with other corporations are both instances where individuals outside the perimeter would need access to internal systems. Conversely, it’s all too common that a bad guy ends up being an existing employee.

# RISE OF THE CITY

A better paradigm for network security is the **city model**.² The city model has no distinct perimeter, and there are multiple ways of entering the network. Like a real city, who you are will determine which buildings you will be able to access.

The security requirements for a city are much more complex than the security requirements for a castle. Additional police, buildings, doors, fences, and locks will be needed in a city. In technical terms, this will mean more internal intrusion detection systems (IDS), virtual LANs, central authentication servers, and encrypted internal traffic.

Technological advances will change the way we *use* networks. The ways we *secure* networks will, out of necessity, also change. The following sections will look at a few of the more well-known ways of attacking networks.

# Test Your Understanding

+   1. a. Explain the four general goals for secure networking.
+      b. How can information be gathered from encrypted network traffic?
+      c. Give an example of how new technology has made networks less secure.
+      d. How does the castle model relate to secure networking?
+      e. What is meant by “death of the perimeter”?
+      f. How does the city model relate to secure networking?

***Warning***: The following material is difficult. Slow down and make sure you understand each concept before moving on. If you are unfamiliar with networking terminology, you should review Module A.

# In the News

# Reflected DoS Attack

In 2018 a new vulnerability was found in a popular caching utility called *memcached*. Memcached was designed to speed up websites by temporarily caching data. A vulnerability in memcached allowed external attackers to make their attack 51,000 times more powerful.³ The result was a reflected DoS attack capable of generating more than 1 Tb per second. Memcached was only supposed to be used internally, but many servers have memcached facing the Internet. Attackers send the server running memcached a UDP request for statistics from a spoofed IP address belonging to the intended victim. The amplified responses produce an enormous wave of packets that overwhelm the victim.

² Bruce Schneier, “The People Paradigm,” CSOOnline.com, November 1, 2004. www.csoonline.com/article/219787/bruce-schneier-the-people-paradigm.

³ Richard Chirgwin, “Popular Cache Utility Exploited for Massive Reflected DoS Attacks,” The Register, February 28, 2018. www.theregister.co.uk/2018/02/28/memcached_reflected_dos_attacks.