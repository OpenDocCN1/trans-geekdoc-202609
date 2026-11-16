# Version Control

Many programmers dread big projects, often for a whole host of reasons. However, one particular aspect of big projects can sometimes seem more unappealing than any other: code organization. Six or seven software developers, two software architects, a lead architect, and client-side developers all working on the same project often represent a recipe for disaster.

Mercifully, code organization on big projects has been made much easier in recent years with the advent of readily available, easy-to-use, cross-platform version-control software.

This appendix examines the basic principles of version control, and discusses how to organize a version-control strategy for your project. You'll also learn how these principles are applied in two of the most popular version-control software applications, and how to choose which (if either) best suits your project.

# Principles of Version Control

The purpose of version control is twofold. The first is to avoid the version conflicts in development that can arise when multiple programmers work on the same set of project files. The second is to automatically journal changes to key files on a project, which creates a historical record of changes to the code and enables the capability to revert to previous versions.

By requiring programmers to _check out a file_ from a central repository when they wish to work on it, a version-control platform can keep a record of who is working on which files, and at what times. Depending on the approach taken, this method can either wholly exclude other developers from working on that file at the same time, or allow other developers to also work on the file and then merge their changes when the file is checked back in again.

_Journaling of files_ in a project involves the retention of previous versions of each file. Whenever a file is checked in to a repository, the version-control platform marks it as current so that anyone retrieving that file from the repository does retrieve that latest version by default. However, a copy is taken of the file in its previous state. Not only does this enable the project administrator or lead