# 6.7.2.2. Types of signatures

There are two types of signatures:

+   - atomic: an attempt has been made to access a specific port on a specific host and the malicious content is in a single packet;
+   - composite: a sequence of operations distributed over multiple hosts over an arbitrary period.

# 6.7.2.3. Characteristics of this detection mode

In general, signature-based detection is the most commonly used method to identify malicious software in the Cisco intrusion-prevention/detection systems.

Advantages:

+   - easy to configure and implement;
+   - by default, an IPS has several pre-installed signatures;
+   - other, additional signatures, can be downloaded and implemented to mitigate new types of attacks.

Disadvantages:

+   - does not detect attacks that fall outside the predefined rules.
+   - may generate “false positive” alarms;
+   - signatures must be periodically updated.

# 6.7.3. Other modes of detecting malicious traffic

# 6.7.3.1. Strategy-based detection

Strategies are created and configured onto the IPS based on the network security policy. Any traffic that is detected as being outside this policy will generate an alarm and/or be blocked.

Advantages:

+   - simple, reliable and highly customizable;
+   - only allows traffic based on the network security policy, which may prevent unknown attacks.