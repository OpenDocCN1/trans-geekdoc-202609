# Chapter 4

# Secure Networks

# Learning Objectives

# Chapter Outline

*After studying this chapter, you should be able to:*

+   - **4.1** Describe the goals of creating secure networks.
+   - **4.2** Explain how denial-of-service (DoS) attacks work.
+   - **4.3** Explain how ARP poisoning works.
+   - **4.4** Know why access controls are important for networks.
+   - **4.5** Explain how to secure Ethernet networks.
+   - **4.6** Describe wireless (WLAN) security standards and potential attacks.

+   - 4.1 Introduction
+   - 4.2 DoS Attacks
+   - 4.3 ARP Poisoning
+   - 4.4 Access Control for Networks
+   - 4.5 Ethernet Security
+   - 4.6 Wireless Security
+   - 4.7 Conclusion

# 4.1 Introduction

**4.1 Describe the goals of creating secure networks.**

Chapter 3 looked at how cryptography can be used to protect communication by ensuring confidentiality, authenticity, and integrity (CIA) of messages. This chapter will shift focus and look at how networks themselves are attacked. It will look at how attackers can maliciously alter the normal operation of a network.

Before modern telecommunication networks, messages were primarily delivered by hand, spoken over a telephone, or sent via radio waves. The primary security goals at that time were (1) keeping the message secret (confidentiality), (2) making sure the message came from the true sender (authenticity), and (3) making sure the message wasn’t altered (integrity). Cryptographic systems could, and still can, achieve each of these goals.

However, with the advent of modern telecommunication networks, it became apparent that new security concerns need to be addressed. The *means* of delivering the messages could be stopped, slowed, or altered. The *route* the messages took could be altered. Messages could be *redirected* to false recipients. Attackers could also gain *access* to communication channels that were previously considered closed and confidential.

# Creating Secure Networks

There are four broad goals to consider when creating a secure networking environment. These goals are an extension of the CIA (confidentiality, integrity, and availability) framework mentioned in Chapter 1. They include availability, confidentiality, functionality, and access control. Attacks against networks are typically focused on defeating one or more of these common goals.