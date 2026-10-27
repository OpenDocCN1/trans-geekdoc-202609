Note that there is now an “A” next to the example.txt file. This indicates that the file is staged for committing. Next, we can commit this file:

```
```text
$ svn commit -m "Initial commit."
Adding        example.txt
Transmitting file data .
Committed revision 1.
```
```

Note that I have committed the first revision to this repository. Also note the -m flag that I executed along with the commit: this designates to Subversion that we are adding a commit message. Developers should always commit with a commit message. For most repositories, if one is not provided they will be prompted in the editor of their choice to set one.

Now imagine that we make a bunch of changes to the example.txt file, and we run svn status again:

```
```text
$ svn status
M           example.txt
```
```

Now the file has an “M” next to it, indicating that it has been changed since our last commit. We no longer need to run the svn add command. This file, because it is tracked by Subversion, will automatically be committed during our next commit.

Imagine for the moment that the changes made to example.txt were inappropriate or wrong. We are not forced to commit those changes, but instead we can roll them back using svn revert:

```
```text
$ svn revert example.txt
Reverted ’example.txt’
```
```

Now a svn status command shows a clean working copy:

```
```text
$ svn status
    $
```
```

It is possible to revert a file to a particular revision. Consult the svn help revert command for more documentation on how this operation functions.