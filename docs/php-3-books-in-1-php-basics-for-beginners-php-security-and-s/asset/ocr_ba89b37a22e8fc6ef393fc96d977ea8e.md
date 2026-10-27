You must delete everything from C:\Users\YOUR_USER_NAME\AppData\Local\Temp\ before beginning.

+   1. Launch a command prompt tab. and Run it as Admin.

+   2. Execute these preceding commands Independently (one at a time, only once):

```
```text
pear channel-discover pear.PHPUnit.de
pear channel-discover components.ez.no
pear channel-discover pear.symfony-project.com
pear clear-cache
```
```

+   3. Now run:

```
```text
pear install PHPUnit/PHPUnit
```
```

# ***Installation of PHPUnit on Windows on XAMPP Environment***

You must install Xampp in C:\xampp before performing the preceding steps.

+   1. launch a cmd.exe, then navigate to the folder C: now open Xampp folder, and you’ll find a folder named PHP. Open it.

+   2. Execute these preceding commands Independently (one at a time, only once):

```
```text
pear update-channels
pear upgrade
pear channel-discover components.ez.no
pear channel-discover pear.symfony-project.com
pear channel-discover pear.PHPUnit.de
pear clear-cache
pear install --alldeps PHPUnit/PHPUnit
```
```

Remember: whenever you get a memory issue, you must alter the "memory limit" setting in your PHP.ini; simply change it to something incredibly huge and then change it back after you’re finished.

# **Install PHPUnit on Macbook**

For the installation of PHPUnit on a Macbook assuming that you’ve followed the PEAR installation procedures for Mac OS in the previous chapter, just execute the preceding command in the prompt:

```
```text
$ sudo pear channel-discover pear.PHPUnit.de
```
```

After that, execute this line on the prompt:

```
```text
$ sudo pear install PHPUnit/PHPUnit
```
```

It’s done. We have installed PHPUnit and you can navigate it by opening user folder then open local where you’ll find the PEAR folder. Within that you’ll see the PHPUnit. Now you can add