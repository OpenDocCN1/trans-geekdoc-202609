
Don’t forget to make it executable with `chmod`. This should work in its current location as with the previous Linux example. However, if you drag it to the Unity Launcher (or “pin” it while the script is running), it will remain there and add a new feature, the “action” menu. Notice the `Actions=Window` line and the `[Desktop Action Window]` section in the code above. These define a new action, (in this case opening a new window, if our script had that capability via the `-n` flag) which is accessible by right-clicking on the icon. Through this you can add any actions you want, by for example calling your script with different parameters, or even calling a completely different script in the `Exec` line. If you want to automatically add Unity entries, or make them available to all users, I suggest the following articles.

| ![information](Images/image00248.jpeg) || **Further Reading**“Unity: adding items to the dock” by Daan van Berkel  

[http://themagicofscience.blogspot.co.uk/2011/05/unity-adding-items-to-dock.html](http://themagicofscience.blogspot.co.uk/2011/05/unity-adding-items-to-dock.html)Unity Launcher Documentation and Guide at Ubuntu.com  

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles) |

| --- | --- |

All of the methods described above can be executed in any number of scenarios. You can use them directly from a command line, as part of a shell script, as a cron job, as a system call from other PHP (and non PHP) scripts, as default file type handlers and so on. With appropriate precautions and permissions, you can even use these methods to call scripts from web based PHP pages (there is usually a better and safer way to invoke them than via a web page, so we’ll leave the details of how to implement and secure it as an exercise for the reader if you really must do so).

### 3.7 Quitting your script

We’ve looked at starting your scripts, but what happens when it comes time to finish running them?

Like web based PHP scripts, CLI scripts will terminate happily when we hit the end of the script file, and will tidy up all the resources used in the same way. Likewise, if we want to end early, we can call the `exit` (or equivalent `die`) language construct.

However in the world of CLI scripts this isn’t considered very polite. Because CLI command are designed to work together, often in chains of commands, most shell programs and scripts will provide an “exit code” when they terminate to let the other programs around them know *why* they finished. Were they done? Did they encounter an error? Were they called incorrectly? Enquiring minds want to know.

It is particularly important to supply an exit code when your script may be the last item in a shell script, as the exit code of the script as a whole is taken to be the last exit code returned within it. We can make our PHP script provide an exit code, simply by including it as a parameter to `exit` or `die`. An exit code is an integer, and there are a number of common exit codes :

*   **0** : Success - we’ve exited normally.

*   **1** : General Error - usually used for application/language specific errors and syntax errors

*   **2** : Incorrect Usage

*   **126** : Command is not executable - usually permissions related

*   **127** : Command Not Found

*   **128+N** (up to **165**): Command terminated by POSIX Signal number N - e.g. In the case of `kill -9 myscript.php` it should return code 137 (128+9)

*   **130** : Command terminated by Ctrl-C (Ctrl-C is POSIX code 2, so as above 128+2 = 130)

| ![information](Images/image00248.jpeg) || **Further Reading**POSIX Signals on Wikipedia  

[http://en.wikipedia.org/wiki/Unix\_signal#POSIX\_signals](http://en.wikipedia.org/wiki/Unix_signal#POSIX_signals) |

| --- | --- |

Any other positive integer is generally construed as exiting due to an unspecified error. So, for instance, if you decide the command line arguments provided by your user are not in the correct format, you should terminate your script using `exit(2)`. If instead all goes well and your script continues to the end of its script file, you can actually let it exit by itself (or by calling `exit` without a parameter), as it returns status code 0 by default.

As with web scripts, you can register functions to be executed when your PHP script exits using the `register_shutdown_function()` function. One use for this may be to check that all is well and evaluate which exit code should be returned. The exit code used as the parameter to `exit` or `die` within a registered shutdown functions overrides the code used in the initial exit call that initiated shutdown. This means that you can happily `exit(0)` everywhere, then `exit(76)` from your shutdown function if you detect that the foo conflaganation isn’t aligned with the bar initispations in your metaspacialatific object. Or similar.

## 4\. Development tools

So far we’ve outline some of the basics of using PHP without a web server, but before we really get into the nitty-gritty details of developing useful non-web software we’re going to take a slight detour into the world of PHP development tools. This is for two reasons. Firstly, before deciding which techniques and methods you are going to use (Interactive CLI script or GUI interface) it is important to understand what tools are available to help support your choice of programming methodology. Secondly, you will often need to adopt a different workflow when developing a new type of software that you may not be familiar with, so you may need to find new tools to fit your new way of working.

In general, you can use the same development tools for general purpose programming as you do for web development, after all PHP syntax is the same wherever it’s executed. The main differentiator is your workflow, and you may find yourself being more productive with different tools.

Of course one of PHP’s dirty secrets is that many PHP programmers don’t use debuggers, unit testing, build systems or code profilers, and in many cases don’t even know what they are. Usually it’s because many PHP scripts are developed as small, uncomplicated, low-risk projects by single developers, and the overhead of learning and deploying extra tools is an unnecessary burden (particularly for those without a formal computer science or programming education). Don’t worry if you fall into this camp, we’ve all been there (and like to visit from time to time!).

However when you start venturing into general purpose programming, you’ll find that the complexity of projects often increases. Rather than a selection of short lived scripts with limited shared state executing in less than a second, you’ll get into larger code bases with longer running processes and more complex dependencies. In such scenarios, the effects of bugs can be magnified and tracking them down becomes increasingly hard. Code is revamped less often and can be relied upon by an organisation and remain deployed for much longer, increasing the burden of maintaining code in the future. If you’re not a regular user of the type of tools described in this chapter, you might find this the ideal opportunity to delve into the wider world of PHP development tools, and give yourself a good foundation on which to start building real software.

We’ll look in turn at different classes of tool, and give some examples of, and links to, popular tools of each type.

### 4.1 PHP REPLs
