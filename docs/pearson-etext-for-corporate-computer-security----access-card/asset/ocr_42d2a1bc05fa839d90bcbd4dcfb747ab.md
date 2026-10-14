# Test Your Understanding

+   2. a. What are the functions of an access router? Explain each function in one sentence.
+      b. Describe the technology of 4-pair UTP wiring.
+      c. What is an Internet access line?
+      d. What is a broadband modem?
+      e. Why is wireless transmission dangerous?

# A Building LAN

The home network shown in Figure A-1 is a local area network (LAN). A LAN is a network that operates on a customer’s premises—the property owned by the LAN user. (For historical reasons, premises is always written in the plural.) In the case of the home network, the premises consist of the user’s home. Figure A-3 shows a larger LAN. Here, the premises consist of a corporate office building.

On each floor, computers attach to a workgroup switch via UTP cords or a wireless access point. Workgroup switches are switches that connect computers to the network. Each workgroup switch (there is one on each floor) connects directly to a core switch in the basement equipment room. (A core switch connects switches to other switches.) When a computer on one floor sends a frame to a computer on another floor, the frame goes to the workgroup switch on the sender’s floor, down to the core switch in the basement, up to the workgroup switch on the receiver’s floor, and then to the destination computer.

UTP is easy to wiretap, allowing attackers to read all packets flowing through the cord. To prevent wiretapping, telecommunications closets should be kept locked at all times, and UTP cords should be run through thick metal wiring conduits wherever possible.

UTP also generates weak radio signals when traffic flows through it. It is possible to read these signals from some distance away. However, this is a rare threat because expensive equipment is needed to read wire radiation.

Typically, attackers do not even need to tap wires in order to break into networks physically. In most building LANs, anyone entering the building can plug a notebook into any wall jack with a UTP cord. To thwart such an attack, most switches today have 802.1X capability that requires any device connecting to a wall jack to authenticate itself before being allowed to transmit beyond the switch. However, this authentication is ineffective without a sophisticated access and identity management control system.

# Test Your Understanding

+   3. a. What is a local area network?
+      b. What is the customer premises?
+      c. Distinguish between workgroup switches and core switches.
+      d. Why is UTP dangerous?
+      e. Why is 802.1X needed?