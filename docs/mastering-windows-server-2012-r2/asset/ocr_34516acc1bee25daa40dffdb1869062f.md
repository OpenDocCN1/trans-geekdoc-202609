# Installing the Operating System

Your first installations of Windows Server 2012 R2 in your live or laboratory environment will probably be either a clean installation or an upgrade installation. There are some other, more advanced ways to install Windows:

+   - An unattended installation: We'll talk about a little later in this chapter.
- A cloned installation using ImageX from the Windows Automated Installation Kit.
- One of Microsoft's deployment solutions uses Windows Deployment Services (WDS): This is an advanced installation performed over the network with functionality that is included in Windows Server 2012 R2.
- Third-party solutions: Ghost is the classic example of a third-party cloning solution that works in conjunction with Microsoft's sysprep tool.

We're going to look at the clean installation and the upgrade installation processes now. We've already mentioned that the installation process is pretty simple.
The installation process is very simple in Windows Server 2012 R2. You're pretty much only being asked to do the following:

+   1. Select a time and currency format, and keyboard method.
2. Choose an edition and build of Windows Server.
3. Agree to the license agreement.
4. Choose between a manual and upgrade installation.
5. Configure the disk.
6. Set the default administrator password.
7. Log in.

There are some options during this flow:

+   - Install a driver if needed
- Repair an existing installation of the operating system on the computer.

In the next section, we'll cover this flow for a clean installation and an upgrade installation. We'll cover some of the options that are presented during the installation and follow up with showing how to customize the installation of the operating system.

# Performing a Clean Installation

A clean installation refers to installing the operating system onto a computer that does not have an installation present or one that you want to keep. In our example, we are dealing with a computer that has no previous installation. We are assuming that you have not done any of this before, so we are going to get back to basics. More advanced readers might be tempted to skip ahead to another section, but we recommend that you at least skim this section to see what has changed.