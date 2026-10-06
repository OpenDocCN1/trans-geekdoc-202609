+   2. Check what the task is running under Action—that's right, it's running PowerShell.

Since you want to run this right away and not wait until 1:00 a.m., you will want to run the manual classification and select Complete as a background task, but not yet.

+   1. First, you need to check the document for which you want to test if file classification is working correctly. Open the file that you want to use as a test.

In our lab environment we have under C:\share\accounts a single file instance of Private Data.rtf. The contents of the file are shown in Figure 15.78.

FIGURE 15.78
Contents of
Private
Data.rtf

![](bbox=[0.313, 0.291, 0.903, 0.653])

Remember that our classification rule is configured to classify on Content and on finding one instance of the expression Finance. This should classify the document as an Accounts document.

+   2. Next, check the existing classification of the document by right-clicking it and selecting Properties and then clicking the Classification tab.

As you can see in Figure 15.79, our file currently has no classification.