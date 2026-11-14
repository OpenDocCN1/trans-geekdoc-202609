
C:\peach3>Peach.exe rm_fuzz.xml Default

```
[ Peach v3.1.124.0
[ Copyright (c) Michael Eddington
```

[*] Test 'Default' starting with random seed 41362.

```
[1,-,-] Performing iteration
```

```
[1,-,-] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: DataElementSwapNearNodesMutator
```

```
[2,-,-] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: BlobDWORDSliderMutator
```

```
[3,-,-] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: BlobMutator
...
```

Sometimes it is necessary to stop the fuzzer and perform maintenance on the machine it’s running on. For such cases, Peach allows for easy stopping and resuming of the session. To stop the current Peach session, just press CTRL-C in its terminal window. Suspending the session will result in the following Peach output:

```
[11,-,-] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: BlobBitFlipperMutator
--- Ctrl+C Detected ---
```

```
C:\peach3>
```

The results of a terminated session can be examined in the session folder under the Peach “logs” directory. Folders in the logs directory use a naming scheme in which a timestamp with the current time at the moment of directory creation is appended to the filename of the Pit XML configuration used for fuzzing (for example, rm_fuzz.xml_2017051623016). Inside the session directory is the status.txt file, which contains the information about the session, such as the number of cases tested and information about times and filenames that generated crashes. If the session was successful, an additional folder named Faults would exist in the session folder. The Faults directory contains a separate folder for each class of crash detected. Inside each of these crash clusters are one or more test cases that contain the following information:

- The mutated test case that triggered the crash.
- A debugging report collected about the program state at the time of the crash. This report includes information about the state and values of the processor register, a portion of stack content, and information gathered from the WinDbg plug-in !exploitable, which provides automated crash analysis and security risk assessment.
- The original test case name that was mutated to create this specific mutation.

The session can be resumed by skipping the already performed test. Information about which test case was the last performed by the fuzzer can be seen in the Logs folder under the session name in the file status.txt:

```
Peach Fuzzing Run
===================
Date of run: 5/29/2017 2:19:30 PM
Peach Version: 3.1.124.0
Seed: 31337
Command line: rm_fuzz.xml
Pit File: rm_fuzz.xml
. Test starting: Default
. Iteration 1 : 5/29/2017 2:19:32 PM
. Iteration 1 of 131795 : 5/29/2017 2:19:33 PM
. Iteration 200 of 131795 : 5/29/2017 2:39:57 PM
. Iteration 300 of 131795 : 5/29/2017 3:14:24 PM
...
```

Another way to see the progress and number of iterations performed by Peach is in the command-line output during fuzzing, which will show in the first entry of a list iteration number. In the following example, the iteration number of the current test is 13:

```
...
[13,131795,1515:0:24:09.925] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: BlobBitFlipperMutator
...
```

One thing to keep in mind is that resuming the fuzzing session only has real value if the fuzzing strategy chosen is deterministic. When you use the “random” strategy, resuming the previous session doesn’t make much difference.

To resume a session, it is enough to run the Pit file, as previously shown, and use the --skipto option to jump to a specific test case number. An example of skipping 100 tests is shown here:

C:\peach3>Peach.exe --skipto 100 rm_fuzz.xml

```
[ Peach v3.1.124.0
[ Copyright (c) Michael Eddington
```

[*] Test 'Default' starting with random seed 31337.

```
[100,-,-] Performing iteration
```

```
[100,9525022,1660:5:55:40.38] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: BlobBitFlipperMutator
```

```
[101,9525022,2950:17:47:42.252] Performing iteration
[*] Fuzzing: TheDataModel.DataElement_0
[*] Mutator: BlobBitFlipperMutator
...
```

## Lab 3-1: Mutation Fuzzing with Peach

In this lab, we look at mutation fuzzing with Peach using Pit files. To successfully complete the lab, follow these steps (which assume the 64-bit version of Windows 10):

- 1. Download and install the VLC application from https://www.videolan.org/vlc.
- 2. Install Windows Debugger Tools for your version of Windows (for Windows 10): https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk. During installation, select the Debugging Tools for Windows option and uncheck the others.
- 3. Download and install Peach 3 from the links at www.peachfuzzer.com/resources/peachcommunity using the instructions at http://community.peachfuzzer.com/v3/installation.html. Right-click the file peach-3.1.124-win-x64-release.zip. Install Peach 3 into the C:\peach3\ directory.

![](img/5f597c6a70133069118d9e804ace3775_92_0.png)

> NOTE On Windows 10, you have to “unblock” the downloaded .zip file (right-click under the security option Unblock) before you unzip it on Windows by default. Otherwise, you get “Error, could not load platform assembly ‘Peach.Core.OS.Windows.dll’. This assembly [sic] is part of the Internet Security Zone and loading has been blocked.”

- 4. Find about six .rm (RealMedia) test files and download them into the (new) directory C:\peach3\rm_samples using the following Google search query:
- intitle:"index of /" .rm

CAUTION Be careful with .rm files you get on the Internet. It is best to perform this exercise on a throwaway VM or at least to revert after completing and/or push the .rm files up to virustotal.com prior to use.

- 5. Copy the rm_fuzz.xml file from book download site to C:\peach3\ folder. Test your Peach Pit file:
- C:\peach3\peach -t rm_fuzz.xml

- 6. Confirm and fix the locations of your VLC application and the other paths as needed.

- 7. Run your Peach Pit from an administrator’s command prompt (required for heap monitoring on Windows 10):
- C:\peach3\peach rm_fuzz.xml Default

- 8. Let this Pit run a while (overnight) and see if you have any bugs listed in the log. (We’ll cover crash analysis later in this chapter.)

## Generation Fuzzing with Peach

As you have seen already, Peach is a capable mutation fuzzer; however, it turns out to be an even better generation fuzzer. In this section, we attempt to discover vulnerabilities in Stephen Bradshaw’s vulnserver—a vulnerable server created for learning about fuzzing and exploits.

The vulnserver application comes with precompiled binaries. Alternatively, you may compile them from source code by following the instructions provided. After launching the vulnserver on a Windows machine, you will get the following greeting:

```
C:\Users\test\Downloads>vulnserver.exe
Starting vulnserver version 1.00
Called essential function dll version 1.00
```

> This is vulnerable software!
> Do not allow access from untrusted systems or networks!

This advice should be well heeded: do not run this software on anything but an isolated test system or virtual machine in host-only mode. You have been warned!

You can test the vulnerable server by connecting via netcat (in another window) as follows:

```
C:\Users\test\downloads\nc111nt_safe>nc localhost 9999
Welcome to Vulnerable Server! Enter HELP for help.
HELP
Valid Commands:
HELP
STATS [stat_value]
RTIME [rtime_value]
LTIME [ltime_value]
SRUN [srun_value]
TRUN [trun_value]
GMON [gmon_value]
GDOG [gdog_value]
KSTET [kset_value]
GTER [gter_value]
HTER [hter_value]
LTER [lter_value]
KSTAN [lstan_value]
EXIT
```

Now that you know a little about the vulnserver application and what commands it takes, let's create a Peach Pit targeting this application. Because you are already familiar with Peach, we will jump right into the Peach Pit. However, this time we will change the DataModel to show the structure of the valid application commands. To keep things simple, we will fuzz the TRUN command (for no reason other than it sounds cool). As part of the lab for this section, you may fuzz the other commands. Note that this Peach Pit is based on an example from David Um's excellent post, which itself was based on an earlier post by Dejan Lukan (see the “For Further Reading” section for more information).
