# UNDERSTANDING SERVER VIRTUALIZATION

Clearly, it's a balancing act. For most organizations (but not all), the advantages far outweigh the disadvantages. The main point is that server virtualization is here to stay. If your organization has not deployed it yet, chances are that it will be soon. Another compelling point is that Hyper-V comes bundled as part of the Windows Server 2012 R2 operating system license, if you've purchased Windows Server 2012, then you already own the virtualization piece and don't need to purchase anything else to get up and running.

# Getting Started with Hyper-V

Not surprisingly, there are hardware and software requirements for running Hyper-V. In addition, there are some licensing issues involved, which we'll discuss later in this chapter.

# HARDWARE REQUIREMENTS

The base requirements for running Hyper-V are quite simple, and these outlines outline what you need:

**CPU and BIOS** You need an x64-based CPU and a BIOS that supports both CPU-assisted virtualization and Data Execution Prevention (DEP). A common problem is that these features are offered by the system, they are not typically enabled in the BIOS of older server hardware. Make sure these features are turned on. If you need to change the BIOS settings, be aware that a cold boot is required; the computer must be completely off. A reset or reboot is not sufficient. Not that any applicable server hardware may need a BIOS upgrade from 2008 or all modern servers now have these features enabled in the BIOS by default, but it is something to double-check before you get started with Hyper-V.

**Certified for Windows Server 2012** If you want to be really sure that the servers you can can run Hyper-V, you should check directly with your vendor. They are responsible for testing that Hyper-V actually runs on their hardware. Most vendors also participate in the "Certified for Windows Server 2012" program, which requires them to test their hardware using Microsoft-standard procedures. After the server passes the test, the vendor can check the configuration for inclusion in the public catalog. However, no vendors submit all of their hardware. That's why you should ask them directly. At http://windowservercatalog.com, you can search for Hyper-V-compatible systems.

Now that you know what features to look for, let's talk about the specifics. There are several things to keep in mind when selecting hardware for virtualization. For your VMs to run optimally, they like a lot of memory (RAM) and fast disk I/O bandwidth, and the more NICs you have,

**RAM** When deploying Hyper-V, you must ensure that your server has the minimum requirements for running Windows Server 2012 R2 as outlined in Chapter 2. Once you have enough RAM to keep the operating system running smoothly, you need to work out how much additional memory is needed for each of your virtual machines. For a low-end personal testing server dedicated to virtualization, you should probably select something with least 8 GB of memory and a single- or dual-socket CPU motherboard with quad-core CPUs.