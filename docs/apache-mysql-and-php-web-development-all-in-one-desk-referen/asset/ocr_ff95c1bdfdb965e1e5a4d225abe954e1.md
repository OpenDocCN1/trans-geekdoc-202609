may realize that you don't like the change you put in, and you can revert back to an older version, effectively undoing the change. By this regard, CVS is a version control system. A typical setup consists of one CVS running on a server, which holds the repository. All users on a development team have a client software program through which they can check out the latest copies, upload their changes, and so on.

If you want to use CVS for your own local projects, you can just run CVS locally. In this mode, your own local copy handles the dirty work of managing the repository; in this mode, you're not using the software in a client/server manner but rather as a stand-alone program.

CVS includes a feature called _branching_. Here's the idea and most common use behind branching: If you release version 1.0 of your product and are well into version 2.0 of your product, and you find a bug in version 1.0, you can go back to version 1.0, fix the bug, and branch off to create a revised version of 1.0, without affecting version 2.0.

Here's another way to look at this example: You finished 1.0 and shipped the product, and all your source code for 1.0 is pretty stable. After the obligatory trip to the Bahamas, you get back and begin work on version 2.0. After two months of work, you and your team members have checked in piles of files to the repository, so the current state of the repository is very different from the way 1.0 was.

But you then discover a bug in version 1.0. You decide you want to fix the bug and ship a patch for version 1.0, without including all the new 2.0 features you've been working on. You check out the entire project for version 1.0, make a change, and start a new branch from version 1.0, where you upload your new files. Now you have two projects that have spawned from version 1.0: The new project 2.0 and the bug-fixed version of 1.0. You can check out either project and build either one independently because CVS keeps track of all the versions.

# Getting CVS

CVS is available for many operating systems, including Linux, Solaris, and Windows. You can find a version for your operating system at www.cvshome.org. Additionally, you can find another version of CVS for Windows NT/2000/XP at www.cvsnt.org/.

If you're interested in _front ends_ for CVS (programs with interfaces that are supposed to make CVS easier to use), you can find plenty at www.wincvs.org/. (Don't let the name “wincvs” fool you; this isn't just for Windows. Mac and Unix versions are available, too.)