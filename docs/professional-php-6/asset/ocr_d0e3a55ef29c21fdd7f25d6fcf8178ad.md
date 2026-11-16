This alternative is well worth a look, but keep in mind that the licensing costs may be prohibitive for small projects. You need to pay only for copies of SourceSafe, however. Because it relies on shared disk space, there is no server as such, and you could even use a network drive presented by Samba running on Linux.

# CVS

Concurrent Versioning System (CVS), as the name suggests, is one of the better-known examples of a version-control platform that implements concurrent versioning for developer check-outs. CVS has the great advantage of being released under the GNU Public License, which means that it is essentially free to download and use.

It stores its repository in a folder largely mirroring the real directory structure of the project in question, and uses small tag lines in files, hidden files in directories, and minor filename concatenations to store auxiliary data in addition to the latest versions of the files themselves. This starkly contrasts with the manner in which SourceSafe stores its files.

CVS clients can connect to CVS in one of two ways: by simply looking at the repository directly (if it resides on the local machine), or by connecting using the pserver protocol. It would, in theory, be possible to share a network drive (a la SourceSafe) to allow the former connection method, but using the pserver protocol is by far the best way to implement CVS over a client/server environment.

CVS is generally run under UNIX, and typically on the same machine on which the local copies of the files reside. In the previous topology example, CVS was run by each user via a shell connection to the development server. For the more UNIX-savvy, this is probably the preferred route. For the not so UNIX savvy, a SourceSafe-like Windows client called WinCVS exists that replicates most of the UNIX client’s own functionality.

Resolving conflicts in CVS is usually relatively straightforward. CVS takes the merger as far as it possibly can, and then presents the user with a new version, annotated to demonstrate the conflict. The user then modifies this new version to resolve the conflict, saves it, and recommits it. CVS then stores this as the latest version. Difficulties do, of course, arise when the conflict is more serious.

CVS can be a good choice, but its concurrent versioning may not be to everyone’s taste (for the reasons outlined earlier in this appendix). Consider carefully whether this is appropriate for the project, and whether its presence could encourage poor working practices among your developers.

# Subversion

The successor to CVS is the increasingly popular application, preferred by the authors of this book, called Subversion (SVN). Subversion is an attempt to preserve all the things that are great about CVS and to replace all the things that aren’t so great. It provides both direct file-system access to the repository where that is useful, but also has an excellent Apache module that enables access to remote users through WebDAV over HTTP. This method does not require any additional ports to be opened in the firewall, or additional daemons to be running on the server, and provides a far more robust permissions system than pserver under CVS. Backup-and-restore is a simple operation, and an entire repository can be exported as a plain text file and migrated to a new server fairly painlessly.