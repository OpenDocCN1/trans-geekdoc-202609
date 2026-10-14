As firewall processing power increases, firewalls will be able to do ever more sophisticated processing. For example, we will see later in this chapter that intrusion prevention systems (IPSs) can stop some very subtle attacks by examining all layers in each packet and by examining complex relationships within streams of packets.

More importantly, we are likely to see the growth of unified threat management (UTM) firewalls, which handle traditional firewall processing, antivirus filtering, and even spam filtering. (As we will discuss later, traditional firewalls do not do antivirus filtering and other application-level malware filtering.)

Of course, traffic is also continuing to grow, and this will use up at least some of firewalls’ increasing processing power.

# Test Your Understanding

+   2. a. What does a firewall do if it cannot keep up with the traffic volume?
+      b. Why is this action good?
+      c. Why is this action bad?
+      d. Why can a firewall keep up with traffic in general but fail to do so during a major attack?
+      e. As processing power increases in the future, what will this mean for firewall filtering?
+      f. What is unified threat management (UTM)?
+      g. What does it mean that a firewall should operate at wire speed?

# Firewall Filtering Mechanisms

We have used the term *filtering* without defining it specifically. The reason for this lack of precision is that there are several **filtering methods** for examining packets. These methods include (1) stateful packet inspection filtering, (2) static packet filtering, (3) network address translation, (4) application proxy filtering, (5) intrusion prevention system filtering, and (6) antivirus filtering. We will look at these filtering methods in this chapter.

Although it is important to understand all of these mechanisms, it is also important to understand that nearly all main border firewalls use stateful packet inspection (SPI) as their primary inspection mechanism. However, they use some of the other filtering mechanisms we will see as secondary filtering mechanisms to supplement SPI.

> Nearly all main border firewalls use stateful packet inspection (SPI) as their primary inspection mechanism.

# Test Your Understanding

+   3. a. Is there only one firewall filtering mechanism?
+      b. What filtering mechanisms do almost all main border firewalls use?
+      c. Do SPI firewalls only do stateful packet inspection?