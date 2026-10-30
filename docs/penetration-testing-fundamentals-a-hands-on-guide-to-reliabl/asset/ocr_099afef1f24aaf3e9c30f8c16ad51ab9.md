# Chapter 10

# Linux Hacking

# Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

+   - Understand the security features of Linux
+   - Extract Linux passwords
+   - Understand basic Linux hacking techniques

The Linux operating system is a fairly secure system. However, it is not perfectly secure; no system is. And if your network has Linux computers, then they too must be tested. Thus, any good penetration test must include testing Linux. In this chapter, we will be looking at Linux and at Linux security in more detail. Then we will look at specific hacking techniques for Linux.

# More on the Linux OS

Chapter 9, “Introduction to Linux,” gave you a working overview of the Linux operating system. It is important that you are very comfortable with all the material in that chapter before proceeding in this chapter. We will start with some more details on the Linux operating system, including places to get information.

# sysfs

sysfs is a virtual file system provided by Linux 2.6 that is used to gather information about the system. sysfs exports information about devices and drivers from the kernel device model to userspace. The organization of the file system directory hierarchy is based on the internal organization of kernel data structures. The files that are created in the file system are usually ASCII files that have one value per file.