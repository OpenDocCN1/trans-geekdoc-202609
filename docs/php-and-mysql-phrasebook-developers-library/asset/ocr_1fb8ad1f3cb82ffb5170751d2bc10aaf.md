![](bbox=[0.22, 0.1, 0.88, 0.52])

Figure 5.4 Information about the uploaded file

NOTE: Some caveats apply when working with form fields. There is the possibility to provide a maximum file length for the uploaded files in a hidden form field; however, this check is then executed server side, so it is definitely better if you do that on your own in your script, using the "type" array subelement.

Also, do not rely on the "name" array subelement because this information (the original filename) can be forged. Even worse, some browsers do not always send the original filename, but the complete path to it. Therefore, always call basename() to extract the filename only.

In our code, we run htmlspecialchars() before outputting any of these two pieces of information.