# The Actual Test

The PCI Penetration testing standard defines a specific process that must be used for a PCI penetration test. The overview of that process is provided here.

First, PCI DSS has three concepts that must be explored prior to the test engagement. Then there are three phases of the test itself. Figure 2-2 shows the three conceptual areas that must be addressed.

![](bbox=[0.06, 0.26, 0.35, 0.48])

FIGURE 2-2 PCI DSS Testing Concepts.

The first issue is to determine the scope of the test. This is important in any penetration test. It is not the case that you will always test everything. In fact, in many situations, this will be infeasible. So first determining what systems will be tested, and to what degree they will be tested, is critical.

One of the things I truly admire about the PCI DSS standard, and something I believe should be incorporated into all penetration testing, is the issue of qualifications. In Chapter 1, I discussed the issue of exaggerated credentials, and that is part of what is meant here by qualifications. But beyond that, it must be determined what level of qualifications are needed for this specific pen test. Some people would argue that you simply always hire the best qualified person who is both available and within your budget. However obvious that might seem, it is incorrect. A good way to illustrate why this approach is wrong is to consider a medical analogy. You don’t need a world-renowned surgeon to set a broken arm.

In determining the qualifications for a given penetration test, several factors need to be considered. The first is complexity. A simple test for web attacks on an e-commerce site is less complex than tests on supervisory control and data acquisition (SCADA) systems, for example. Another issue is the nature of the target network. A homogeneous network, for example a Microsoft Windows only network, is simpler to test than a network that has Microsoft Windows workstations, Linux web servers, and Mac laptops. The aforementioned scope is also an issue in determining the requisite qualifications. The broader the scope of the test, the more skills will be required.

Finally, the third concept is methodology. In Chapter 1, I discussed a variety of methodologies. Closely related to that topic are the standards being discussed in this chapter. Of course, for a PCI DSS