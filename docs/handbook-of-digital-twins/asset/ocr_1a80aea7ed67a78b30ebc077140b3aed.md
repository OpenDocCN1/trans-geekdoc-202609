![](bbox=[0.11, 0.12, 0.9, 0.45])

# FIGURE 13.1
Subject-oriented abstraction layer architecture.

Although it is described in a top-down way, it can be applied through a middle-out or bottom-up approach, e.g., in case a specific CPS component, such as a robotic device for production, is the starting point of CPS development. Figure 13.1 shows the fundamental idea and mechanism of subject-oriented layering of digital CPS twins.

The architecture is based on specifying a SID:

+   • At least one layer (SID on a single layer of abstraction) needs to be given, providing a SID representing value-generating subjects and their interaction.

+   • Each subject of a SID on a specific layer of abstraction can be refined under the given constraints of interactions (passing of messages) on a lower layer.

+   • The last subject refined (‘leaf’ subject) needs to be detailed by a SBD. Layering means the following for SBDs:

+   • At least one layer needs to be given, ...
+   ...providing a set of SBDs derived from the SID,...
+   ...with each SBD derived from a SID subject,...
+   with each SBD being part of at least one interaction with another SBD.