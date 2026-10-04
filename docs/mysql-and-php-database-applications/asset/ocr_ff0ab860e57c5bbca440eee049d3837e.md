# Chapter 10: Catalog

really not necessary, because the open-source world has provided all of us develop-ers with a utility that powerfully and easily manipulates images. It's called PBMplus.

![](bbox=[0.181, 0.196, 0.256, 0.246])

You can find the PBMplus package on the CD-ROM that accompanies this book.

PBMplus contains several utilities that come in two basic flavors. One of utili-ties transfers images to and from an intermediary format. So, whether you have a gif, a jpg or a png, it must be converted to the intermediary format, pbm. Another set of utilities alters the pbm files. These utilities do for variety of things: check the README file and the pages that come with PBMplus to learn about. Once you have made the .pbm file, you can convert it to whatever format you need.
 use these, you need to run shell commands from your PHP script. For the purposes of this application, the system() function will be the best choice. More on when we get to it in the code.

![](bbox=[0.181, 0.495, 0.256, 0.545])

> There is potential danger when using functions that run shell commands. If and information supplied from the user is transported to the shell commands, you should take great care to ensure that damaging commands cannot be exe-uted. The escapeshellcmd() function will help http://www.php.net/manual/function.escapeshellcmd.php examine shell commands. In this application only people who are logged in will reach commands that access the shell.

![](bbox=[0.181, 0.674, 0.256, 0.724])

If you wish to output the results of PBMplus utilities directly to the browser, use the passthrough() function.

# Code Breakdown

In OO coding, good documentation is your best friend because, as already stated, it almost shouldn't matter how the classes you are using accomplish your tasks. You just need to know that they work.