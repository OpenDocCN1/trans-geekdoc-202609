Or you can set CVSROOT in the environment variables page of the system properties.

If you're using a remote system, your CVSROOT will more likely look like this: pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp. (That's one I lifted from the SourceForge open source site, for a project called Dev-C++.)

Alternatively, you can pass the directory name with each CVS command. For example, to log into SourceForge, you can do this:

```
```
CVSROOT=pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp
export CVSROOT
cvs login
```
```

Or you can combine it all on one line, by putting the CVSROOT right on the command line. To do so, you use the -d option:

```
```
cvs -d pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp login
```
```

The command format is the same: the word cvs followed by the word login. In between, I include the -d option and the information on the repository. (In the next section, I talk more about the login procedure.)

# Logging in to CVS

Before you can use CVS, you need to log in to the remote CVS server. You can use your local client CVS program anytime you want, but before you can check out any files from the CVS server, the server must allow you access.

One thing about CVS that might strike you as strange or awkward is that to log in to CVS, you run the CVS command with the login parameter. Then the CVS command ends, and you end up back at the shell prompt. But you're still logged in. Yes, that's a bit strange: The server remembers who you are, and you can run more CVS commands from the prompt until you have finished you work, after which you can log out.

![](bbox=[0.13, 0.75, 0.23, 0.82])

If you are using CVS for your own local work and aren't connecting to a remote CVS server, you don't need to log in. See “Creating a CVS Repository and Project,” later in this chapter, for more information on using CVS locally.

Logging in is easy as long as the format of the command is correct. The login command needs to know the following information: