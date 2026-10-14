# Chapter 7

# Host Hardening

# Learning Objectives

After studying this chapter, you should be able to:

+   7.1 Define the elements of host hardening, security baselines and images, and systems administration.
+   7.2 Know important server operating systems.
+   7.3 Describe vulnerabilities and patches.
+   7.4 Explain how to manage users and groups.
+   7.5 Explain how to manage permissions.
+   7.6 Explain how to create strong passwords.
+   7.7 Describe how to test for vulnerabilities.

# Chapter Outline

+   7.1 Introduction
+   7.2 Important Server Operating Systems
+   7.3 Vulnerabilities and Patches
+   7.4 Managing Users and Groups
+   7.5 Managing Permissions
+   7.6 Creating Strong Passwords
+   7.7 Testing for Vulnerabilities
+   7.8 Conclusion

# 7.1 Introduction

**7.1 Define the elements of host hardening, security baselines and images, and systems administration.**

Although firewalls stop most Internet-based attacks, they will never stop them all. Consequently, protecting individual servers and other hosts is critical. In fact, if you install a server "out of the box," that is, use the operating system’s installation media and installation defaults and then connect the server to the Internet, a hacker is likely to "own" it within minutes or even seconds.

# What Is a Host?

In networking, any device with an IP address is a **host**. That simple definition works in security as well because any device with an IP address can be over a network. Consequently, the term *host* includes servers, clients, routers, firewalls, smartphones, and a variety of IoT devices. Although we do not usually think of firewalls and routers as hosts, think of the damage a hacker could do if he or she took over a firewall or router.

> Any device with an IP address is a host.

# The Elements of Host Hardening

The process of protecting a host against attacks is called **host hardening**. Hardening is not a single protection but rather a number of protections that often have little in common with each other. Among these protections are the following: