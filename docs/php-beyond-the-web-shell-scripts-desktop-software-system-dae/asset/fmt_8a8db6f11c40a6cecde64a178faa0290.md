
PHP for Windows also ships with `php-win.exe`, which is similar to the CLI build of PHP, except that it does not open a command line window. This is useful for running apps with a graphical interface (which will be covered later in this book) or daemon type software.

| ![information](Images/image00248.jpeg) || **Further Reading**An instructive comment on spawning `php-win.exe` processes on Windows  

[http://www.php.net/manual/en/features.commandline.php#62162](http://www.php.net/manual/en/features.commandline.php#62162) |

| --- | --- |

### 3.6 “Click to Run” your PHP

In the previous section we looked at the different ways the PHP commands can be formatted, and showed them in the context of the command line, i.e. typing them in. But lets make things easier on ourselves and give them clickable icons so that we can run them direct from the desktop. How we achieve this depends on the operating system.

#### 3.6.1 Clickable icons : Linux

On most Linux systems, specifically those that support the freedesktop.org “Desktop Entry Specification” standard, you can create a clickable “launcher” icon by simply creating a text file. Most main-stream Linux distributions and their window managers follow at least the basics of this standard.

To create a launcher for your app, create a text file in the folder where you want it to appear (e.g. in `/home/rob/Desktop`) called, e.g. `myscript.desktop`. It is important that it has the `.desktop` extension. In the file, add the following lines :

```
[Desktop Entry]
Type=Application
Name=My Funky App
Terminal=true
Exec=/usr/bin/php /home/rob/scripts/myscript.php
Icon=/usr/share/icons/gnome/32x32/actions/up.png
```

The first two lines tell the system what we are creating here. The `Name=` line gives your launcher a name which will be shown below the icon. The `Terminal=` line determines whether a terminal window is opened for this program. You will want to set this to `true` if you are creating a shell script that takes input from, or sends output to, the terminal. If your script interacts with the user via GUI elements, you will likely want to set it to `false`. `Exec=` specifies the command to execute when the user clicks the icon. This is the command to call your PHP script, as we discussed in the previous sections. Finally, the `Icon=` line points to the location of a pretty icon for your app. You can supply your own icon file, or use one of the system provided ones. Here we have use the Gnome “up” arrow icon, to indicate that our script will cause profits at your company to rise and rise. “Down” arrows are also available. You will usually need to also give the `.desktop` file execute permission, using `chmod u+x myscript.desktop` or similar.

There are many other options you can set in this file, see the following standards site for more info. Support for some options varies from distribution to distribution.

| ![information](Images/image00248.jpeg) || **Further Reading**Freedesktop.org Desktop Entry Specification standard  

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/) |

| --- | --- |

#### 3.6.2 Clickable icons : Windows

As mentioned previously there are two executables for Windows, the standard `php.exe` and the newer `php-win.exe` which allows windowless running of scripts. There are likewise two ways to make “clickable” scripts.

First is the simple Windows Batch File. This is a text file with a list of commands to execute. Batch files have the `.bat` extension in their name, and are executable by default. So if we have a PHP script called `display_stats.php` that displays a list of numbers and then exits, and we want to run it in Extended Information Mode, we can make it a clickable script by creating a file called, say, `our_stats.bat` with the contents :

```
"C:\Program Files (x86)\PHP\php.exe" -e "C:\users\Rob\PHP 
	Scripts\display_stats.php"
pause
```

If you click on `our_stats.bat` it will open a command prompt window, execute our PHP script and display our statistics, and finally wait for the user to press a key before closing the command prompt window. The last step, achieved here with the `pause` command, is important, as the command prompt window will close again as soon as the batch file finishes executing, and if you have output for the user to view you will want to keep it open. This can of course be achieved directly in your PHP script by pausing execution or waiting for user input, but the script above shows how you can mix PHP and other commands in the same batch file. Don’t forget to change the paths to `php.exe` and your script as appropriate. You can use relative filenames or rely on default search paths, but it is often best to use the full path name to ensure that the correct instance of `php.exe` is used and avoid problems if moving your PHP script relative to the batch file.

The second way of making a clickable PHP script is by calling it from within a Windows VBScript. The example above using a batch file will always open a command prompt window, even if you use `php-win.exe` rather than `php.exe`, as it does it by default to execute the commands in the file. A VBScript on the other hand needs no command prompt or other visual form by default. So if we want to use `php-win.exe` to run a script that either provides it’s own GUI interface or runs hidden in the background, we should create a script with a `.vbs` extension. Lets say we have PHP-GTK script (more on that in chapter 5) called `text_editor.php` that provides a visual text editor like Notepad. We can make it clickable by creating a file called, say, `our_text_ed.vbs` with the following contents:

```
Set WinScriptHost = CreateObject("WScript.Shell")

WinScriptHost.Run Chr(34) & "c:\Program Files (x86)\PHP\php-win.exe" & 
Chr(34) & " -e c:\Users\me\text_editor.php", 0

Set WinScriptHost = Nothing
```

Click on the `.vbs` file and your PHP script should spring into life, sans command line prompt. The `WinScriptHost.Run` line does the heavy lifting of running a command that we provide. We format that command in the same way we would if we were typing it in by hand at the command prompt, and pass it as a string. Note that in VBScript `&` is the string concatenation operator (the same as `.` in PHP), and that `Chr(34)` is the `"` double quote character (needed as the directory path to `php-win.exe` has a space in). Don’t forget to change the paths to the `php-win.exe` and your script as appropriate.

The final piece of the puzzle, whichever of the two methods you use, is to give your clickable file a better icon. The files will have the default icon for Batch Files or VBScripts, and it is not possible to change this directly without changing it for all files of the same type. There are however two workarounds. Windows allows you to change the icon of a short-cut (via `Right-Click -> Properties`), so the first workaround is to hide your script file somewhere out of sight, and create a short-cut icon where you want to be able to click it. Then change the icon of the short-cut. The other workaround is to change the file extension to one that Windows does not recognise, e.g. `.phpsc` and create a new file extension with the same actions as `.vbs` or `.bat` but with a different icon.

#### 3.6.3 Clickable icons : Ubuntu Unity

To add an icon to the Unity Launcher in Ubuntu, we create a `.desktop` file in a similar manner to the Linux launcher we created before, but with a few more options. So lets create a new `myscript.desktop` :

```
[Desktop Entry]
Name=My Super Script
Exec=/usr/bin/php /home/rob/scripts/myscript.php
Icon=/usr/share/icons/gnome/32x32/actions/up.png
Terminal=true
Type=Application
StartupNotify=true
Actions=Window;

[Desktop Action Window]
Name=Open me a new window please
Exec=/usr/bin/php /home/me/scripts/myscript.php -n
OnlyShowIn=Unity;
```
