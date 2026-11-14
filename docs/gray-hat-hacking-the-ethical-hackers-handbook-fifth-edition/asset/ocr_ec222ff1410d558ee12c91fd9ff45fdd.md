from the March 2017 update. The examples shown in this lab are from IDA 7.0 in x86 compatibility mode in order for the BinDiff 4.3 plug-in to be used.

The first step is to open up your licensed copy of IDA, or the free version 5.0 if you do not have a licensed version, and open up the “New” srv.sys file. Allow IDA to complete its analysis. Once finished, save the database and open up the “Old” version of srv.sys. Once analysis is finished, you are ready to perform the diff. With the “Old” srv.sys file loaded, press CTRL-6 to bring up the BinDiff menu and then click Diff Database.... If you are using turbodiff, press CTRL-F11 to bring up its menu and use the same method shown in Lab 17-1.

![](bbox=[0.358, 0.278, 0.642, 0.469])

After clicking the Diff Database... button, navigate to the “New” srv.sys IDB file and perform the diff. After a few moments the diff should be finished, and you should have some new tabs open inside IDA. The one we are interested in is “Matched Functions.” In the diff results shown next, we have selected the function SrvSmbTransaction(). Often, when there are more than a few functions with changes, you must look at the function names when determining potential functions of interest.

| Similarity | Confid | Change | EA Primary | Name Primary |
| :--- | :--- | :--- | :--- | :--- |
| 0.83 | 0.97 | GI---- | 000000000005C141 | SrvSnapParseToken(x,x,x) |
| 0.87 | 0.99 | GI--EL- | 00000000000150EF | SrvPerformCopyChunkWorker(x) |
| 0.89 | 0.99 | GI-JE-- | 0000000000027530 | SrvFsdDispatchFsControl(x,x,x) |
| 0.92 | 0.93 | -I-J--- | 0000000000028760 | _TlgEnableCallback(x,x,x,x,x,x,x,x,x) |
| 0.94 | 0.99 | GI--E-- | 0000000000058607 | SrvSmbTransactionSecondary(x) |
| 0.95 | 0.99 | GI---C | 000000000005717F | SrvRestartExecuteTransaction(x) |
| 0.95 | 0.99 | GI---C | 0000000000056837 | ExecuteTransaction(x) |
| 0.95 | 0.99 | GI--E-- | 000000000005787D | SrvSmbNtTransactionSecondary(x) |
| 0.96 | 0.99 | GI-JE-- | 0000000000057C84 | SrvSmbTransaction(x) |
| 0.96 | 0.99 | GI----- | 0000000000027300 | SrvFsdDispatch(x,x) |
| 0.96 | 0.99 | GI----- | 000000000001C7FA | SrvDisconnectHandler(x,x,x) |
| 0.96 | 0.99 | GI-JE-- | 000000000005192B | SrvSmbWriteAndX(x) |

Press CTRL-E to perform a graphical diff. If using turbodiff, be sure to use the method