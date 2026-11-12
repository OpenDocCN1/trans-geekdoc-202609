# Checking out files anonymously

If you use an open-source product, and you want to download the entire source tree but aren't a member of the development team, most open-source projects allow anonymous checkout through CVS. This means that you can check out the files as you normally would, but you don't have a username and therefore can't commit any changes that you make. That doesn't mean you can't make any changes; it just means that for now your changes are for your own purposes only and don't become a part of the official source. (However, most open-source projects welcome new developers, which means you can later get a username and check in your changes.)

To check out files anonymously, you follow the instructions on the open-source Web site. For example, SourceForge includes instructions with each project on how to check out the files anonymously. However, the instructions assume you're familiar with CVS. The instruction includes a line for logging in, such as this:

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp login
```

When you're prompted for a password with SourceForge, you simply press Enter. Other open-source sites give you instructions for the password.

But that only logs you in. Next you have to check out the files and then log out. (Please remember to log out.) Some people use the alias co instead of checkout; co means the same as checkout. The SourceForge page includes a line for checking out the files, but you need to know the project name:

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/dev-cpp checkout V5
```

In this example, the project name is V5. How did I know that? The developers of each project in SourceForge choose their project names. (The official term is *module*, not *project*, so don't be surprised if you see the word *module* on the SourceForge site.) To figure out what module name the developers used, click the Browse CVS Repository link found on the CVS page of each SourceForge project. (The CVS page is available from the CVS link at the top of each project page.) The Browse CVS Repository link opens a browser version of the repository, where you can see the name of the project. You see several names here, such as the following:

```
Attic/
CVSROOT/
V5/
copying.txt
```