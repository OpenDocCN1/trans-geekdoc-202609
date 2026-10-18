are well designed and written, and are not easily broken. In addition, you should be aware of the various security mechanisms which you can implement in order to fortify your applications. You should also be aware of the different forms of ‘attack’ which can be implemented and thus know how to defend against them.

# 20.1 Web application security and robustness

Hopefully, our earlier chapters have demonstrated that creating PHP applications is relatively easy but unfortunately that is not the end of the story. In Chapter 19, we introduced the concepts of ensuring that any (X)HTML and CSS scripts conform to W3C standards and that designing systems for accessibility should be considered right from the start. As PHP is used to generate (X)HTML output, these considerations are an integral part of the PHP script design and implementation phases. However, in addition to this, PHP developers need to consider other aspects of their design, namely the robustness of their software and the security of its data.

Because your web application has been installed on a secure web server is not enough to ensure that your application is as secure and robust as possible. You need to implement a strategy to raise the quality and security of your applications. This strategy consists of:

+   - Developing good programming practice to ensure your applications are well implemented.
+   - Being aware of the different forms of attack which could be ranged against your application and ensuring that you have defended against them.
+   - Ensuring you have authenticated a valid user and have implemented a good secure password mechanism.

We begin by examining some good PHP development practices.

# 20.2 Good PHP development practice

# Report all errors

The first, and perhaps the most important, tip for good PHP development practice is to ensure that you are aware of all errors and warnings that the PHP interpreter generates. Interestingly, by default PHP does not do this and you need to edit the PHP configuration file, called ‘php.ini’, in order to change this.

The ‘php.ini’ file can be most easily accessed from the wamp icon on the Windows application bar, assuming this is how you installed PHP. If you did not, then you will need to search Windows for the ‘php.ini’ file. To access the ‘php.ini’ file through wamp, left click on the wamp icon on the right of the application bar at the bottom of your desktop and select ‘config files’. Finally, from the menu that appears, click on ‘php.ini’. The file is illustrated in Figure 20.1.

Notepad launches with a copy of the ‘php.ini’ file loaded ready for you to edit. The file is quite long and complex and in order to find the correct section to edit you need to scroll down until you come to the section labelled ‘Error handling and logging’, as