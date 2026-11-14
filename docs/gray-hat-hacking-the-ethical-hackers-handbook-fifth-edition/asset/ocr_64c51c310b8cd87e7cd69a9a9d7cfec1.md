decompilation can cause functionality to be missing from the output. When you're dealing with malicious code, it is always recommended that you double-check the disassembly for any suspicious code and functionality that might have been hidden from the decompiler. In cases where JD cannot determine the decompilation code, it will output the disassembly of a class file. The following is JD disassembly output for a function that couldn't be decompiled:

```
/* Error */
private String DownloadText(String paramString)
{
    // Byte code:
    // 0: aload_0
    // 1: aload_1
    // 2: invokespecial 63
    com/example/smsmessaging/TestService:OpenHttpConnection
    (Ljava/lang/String;)Ljava/io/InputStream;
    // 5: astore_3
```

# DEX Decompilation

The problem with the previously mentioned DEX decompilation is that the file first has to be converted to JAR format and then decompiled using Java tools. In such a scenario, there are two locations for failure: the conversion of DEX and the decompilation of JAR. The JEB decompiler<sup>6</sup> aims to solve this problem by performing decompilation directly on DEX files. It comes with a handy GUI that's very similar to IDA, making it a familiar user experience. Unlike the JD decompiler, JEB is a commercial product, and a single license costs US$1,080.<sup>7</sup> Following is some of the functionality offered by JEB:

+   • Direct decompilation of Dalvik byte code
+   • Interactive analysis GUI with capabilities for cross-refencing and renaming methods, fields, classes, and packages
+   • Exploring full APK, including manifest file, resources, certificates, strings, and so on
+   • Supports saving the modifications made during analysis to disk and sharing the file for collaboration
+   • Support for Windows, Linux, and macOS

Figure 18-2 shows a decompiled DEX file using JEB. The same DEX file was used to generate decompiled Java code with the JD in the previous section.