the HTML file, looking for statements written in the PHP language. It then executes these statements and spits out a possibly different-looking, final HTML page. The Web server then happily sends this page to the client machine. Figure 2-1 shows you this process. (Note that in this minibook I refer to the PHP “processor” simply because it’s a bit shorter than “preprocessor.”)

![](bbox=[0.12, 0.23, 0.21, 0.3])

As you study PHP, remember that you’re writing a file that is processed by the PHP preprocessor and that the output from the processor is a valid HTML file. Keeping this in mind will help you stay sane during your development, because at times you will start to feel like you’re working on some abstracted level several steps away from the actual HTML files. That’s because you are, and it can get a little mind-numbing at times. But fear not; I’m here to help you get through it.

![](bbox=[0.12, 0.37, 0.21, 0.44])

When you're doing a lot of PHP development, you should have access to the online PHP manual. This manual is an excellent supplement to the For Dummies book in your hands. You can find it at www.php.net/docs.php. From there, you can access the manual in many different languages in various file formats. For an English version in online HTML format, you can go right to www.php.net/manual/en/. And incidentally, you probably already noticed from these URLs that the main PHP home page is www.php.net.

Figure 2-1: The PHP processor reads in a file containing PHP code and spits out a valid HTML file.

![](bbox=[0.24, 0.52, 0.88, 0.9])