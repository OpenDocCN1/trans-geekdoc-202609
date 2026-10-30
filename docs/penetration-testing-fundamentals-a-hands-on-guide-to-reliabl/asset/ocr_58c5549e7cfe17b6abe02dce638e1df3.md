Now if you navigate on your Kali machine to the default directory, you will find mypayload.exe as shown in Figure 14-13.

![](bbox=[0.07, 0.17, 0.57, 0.4])

FIGURE 14-13 mypayload.exe.

Earlier I mentioned that we were ignoring the architecture. It is required that the payload be tailored to a specific computer architecture. If you do not select one, msfvenom will default to x86 architecture.

Now that you have a basic understanding of how to use msfvenom, let us take a closer look at the flags. Here are the most important flags:

+   - **-p** designates the Metasploit payload you wish to deliver.
+   - **-f** designates the output format (.exe, .avi, .pdf, etc.).
+   - **-e** designates the encoder you wish to use.
+   - **-a** designates the architecture to target (default is x86).

These are not the only flags, but these are the most critical and most commonly used flags. One more flag we have not yet used is -Platform. This targets the specific platform you are trying to attack. There are a number of options for this flag, a few of which are given here:

+   - Windows or windows
+   - OSX or osx
+   - Solaris or solaris
+   - BSD or bsd
+   - OpenBSD or openbsd
+   - Unix or unix