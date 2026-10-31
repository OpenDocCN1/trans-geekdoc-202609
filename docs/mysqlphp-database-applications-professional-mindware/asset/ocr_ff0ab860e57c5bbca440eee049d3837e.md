really not necessary, because the open-source world has provided all of us developers with a utility that powerfully and easily manipulates images. It’s called PBMplus.

![](bbox=[0.18, 0.2, 0.26, 0.26])

You can find the PBMplus package on the CD-ROM that accompanies this book.

PBMplus contains several utilities that come in two basic flavors. One set of utilities transfers images to and from an intermediary format. So, whether you have a gif, a jpg, or a png, it must first be converted to the intermediary format, pbm. Another set of utilities alters the pbm files. These utilities do a variety of things: check the README file and the man pages that come with PBMplus to learn about them. Once you have made the .pbm file, you can convert it to whatever format you need.

To use these utilities, you need to run shell commands from within your PHP script. For the purposes of this application, the system() function will be the best choice. More on that when we get to it in the code.

![](bbox=[0.18, 0.49, 0.26, 0.56])

There is potential danger when using functions that run shell commands. If and information supplied from the user is transported to the shell commands, you should take great care to ensure that damaging commands cannot be executed. The escapeshellcmd() function will help http://www.php.net/manual/function.escapeshellcmd.php examine shell commands. In this application only people who are logged in will reach commands that access the shell.

![](bbox=[0.18, 0.65, 0.26, 0.72])

If you wish to output the results of PBMplus utilities directly to the browser, use the passthrough() function.

# Code Breakdown

In OO coding, good documentation is your best friend because, as already stated, it almost shouldn’t matter how the classes you are using accomplish their tasks. You just need to know that they work.