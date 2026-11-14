![](bbox=[0.12, 0.08, 0.88, 0.48])

You can still see the ExecuteTransaction function in the middle block, but flow must first pass through the memset function calls before hitting that block. Feel free to follow the couple of blocks in this path. The memset function calls are likely taking care of the information leak associated with CVE-2017-0147.

# Patch Diffing for Exploitation

In the previous Microsoft patch diff with MS17-010, we identified code changes that resolved an information disclosure issue; however, this did not lead us to exploitation of the bug. In this next example, we will take a look at a DLL side-loading bug that may allow for remote code execution and get a working exploit up and running. Both MS16-009 and MS16-014 claim to resolve CVE-2016-0041, which relates to a “DLL Loading Remote Code Execution Vulnerability.”3 This author found that the actual file we are interested in was made available in the MS16-009 patch. To remain consistent, the bug was discovered by Greg Linares, who wrote the previously covered PatchExtract tool.

# DLL Side-Loading Bugs

When checking online, you may get various definitions as to what constitutes a DLL side-loading bug. From a high level, depending on settings in the registry, as well as arguments passed to a DLL-loading function, such as the LoadLibrary() suite of functions, there may