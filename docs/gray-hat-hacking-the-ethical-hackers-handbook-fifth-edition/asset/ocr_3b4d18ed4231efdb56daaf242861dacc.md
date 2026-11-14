You can follow along with the preceding example by performing the following lab steps:

+   1. Download the vulnerable server application (the .exe and .dll) to your test lab or build it yourself (https://github.com/stephenbradshaw/vulnserver). Then place the executable in C:\vulnserver.
+   
+   2. Launch the vulnerable server, like so (note the warning in the output):
+   C:\vulnserver>vulnserver.exe
+   
+   3. Download and install the A/V safe version of netcat (without -e) for Windows (https://joncraton.org/blog/46/netcat-for-windows/).
+   
+   4. From another window, test the vulnerable server, like so:
+   C:\Users\test\downloads\nc111nt_safe>nc localhost 9999
+   
+   5. Copy the fuzz_TRUN.xml file listed previously (available from the book download site) to the C:\peach3\ folder.
+   
+   6. From an administrator command prompt, start your Peach agent:
+   C:\peach3> peach -a tcp
+   
+   7. From a new administrator command prompt, launch the Peach Pit:
+   C:\peach3> peach fuzz_TRUN.xml TestTRUN
+   
+   8. Monitor and review the Logs folder (C:\peach3\logs).

![](bbox=[0.14, 0.47, 0.24, 0.53])

CAUTION Depending on your version of Windows, you may experience warnings or the vulnerable server may crash and you need to restart testing again. Depending on how lucky (or unlucky) you are, you may need to generate many test cases—even as many as a thousand—before the program generates faults.

# Genetic or Evolutionary Fuzzing with AFL

When it comes to genetic or evolutionary fuzzing, the best option is AFL, particularly for file-based parsers written in C or C++. When source code is available, the application may be instrumented with AFL during compilation with either clang or g++. For this section, we will take a look at this file-parsing application, which would pose a significant challenge to a mutation fuzzer. This program has been adapted from an example given by Gynvael Coldwind (Michael Skłodnikiewicz) during an excellent video blog on genetic fuzzing (see “For Further Reading”). As Gynvael explains, when an application has many nested if/then blocks, it is often difficult, if not impossible, for a mutation fuzzer to reach full code coverage, at least in our lifetime. Consider this simple example: