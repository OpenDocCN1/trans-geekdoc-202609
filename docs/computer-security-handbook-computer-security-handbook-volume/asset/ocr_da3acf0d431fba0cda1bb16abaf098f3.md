+   - Although ActiveX security measures are available in Internet Explorer, other client software may run controls without necessarily implementing such security. Internet Explorer security levels tend to be all or nothing, making it difficult to allow a specific control without allowing all controls of that type. Remote activation of controls can bypass normal security perimeters such as those imposed by firewalls.
+   - There is no basis for deciding whether a particular control is safe to execute or not, in any particular context.
+   - Scripting Concerns
+     - Lacking a general basis for limiting the actions of controls, ActiveX programmers must effectively determine their own precautions to prevent harmful actions. It is difficult enough to develop a good set of boundaries on program activity, even if one uses a general model such as the sandbox described later; it is extremely difficult to see how individual developers can be expected or, more importantly, trusted to create their own equivalent of the sandbox for each individual control. In light of these hazards, the authors of the CERT/CC report stated that “there is a large number of potential failure points.”

# 17.2.4 Case Studies.

Several security breaches or demonstrations mediated through ActiveX have occurred since the introduction of this technology in the mid-1990s.

# 17.2.4.1 Internet Exploder.

In 1996, Fred McLain wrote Internet Exploder, an ActiveX control designed to illustrate the broad degree of trust conferred on an ActiveX control by virtue of its having been signed. Exploder, when downloaded for execution by Internet Explorer, will shut down the browser’s computer (the equivalent of the Shut down | Shut down sequence from the Start menu on a Windows system). This operation is operationally disruptive but does not actually corrupt the system. McLain notes in his frequently asked questions (FAQ) on Exploder that it is easy to build destructive or malicious controls.28

Exploder raises an important question: Who and what are the limits on trust when using signed code? In normal commercial matters, there is a large difference between an inauthentic signature, a forgery, and a properly signed but unpayable check. In software, the difference between an inauthentic control and a dangerous one is far less clear.

# 17.2.4.2 Chaos Computer Club Demonstration.

On January 27, 1997, a German television program showed members of the Chaos Computer Club demonstrating how they could use an ActiveX control to steal money from a bank account. The control, available on the Web, was written to subvert the popular accounting package Quicken using what amounts to an electronic version of tailgating. A victim need merely visit a site and download the ActiveX control in question; the control then automatically checked to see if Quicken was installed. If so, the control ordered Quicken to issue a transfer order to be saved in its list of pending transfers. The next time the victim connected to the appropriate bank and sent all pending transfer orders to the bank, all the transfers would be executed as a single transaction. The user’s personal identification number (PIN) and transaction authorization number (TAN) would apply to all the transfers, including the fraudulent one in the pile of orders. Most