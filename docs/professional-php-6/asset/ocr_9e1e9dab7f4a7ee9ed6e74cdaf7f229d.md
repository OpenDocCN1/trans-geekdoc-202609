+   - The -r flag causes the copy to take place recursively.
+   - The -z flag causes data being transferred to be compressed before transfer. On a same-server copy, this should be omitted.
+   - The -e ssh directive tells rsync to use SSH to transfer files, rather than RSH.
+   - The source directory is specified as /local/directory/* (the * simply signifying that all files within that directory should be copied).
+   - The remote directory is specified as username@remotehost:/remote/directory, but if you're copying to another folder on the same server, the username@remotehost directive should be omitted.

Upon executing an rsync command, you may be prompted for a password. This is the login password associated with the username on the remote server specified, as if you were SSH’ing into that server in the normal fashion.

Let’s look at some examples of this syntax at work.

# rsync Syntax Examples

Let’s first look at how you might deploy the contents of your studio staging environment to your live staging environment at your client’s data center. You would use the following syntax:

```
rsync -avrz -e ssh /home/widgets/staging/
 * widgets@staging.widgets.com:/home/widgets/staging
```

If the client then approves the changes on the staging server, you can put them live. In this example, suppose that you put live simply to another folder on the same server. You would use the following syntax:

```
rsync -avr /home/widgets/staging/* /home/widgets/live
```

Note that now you omit the protocol directive, because this is a local-only synchronization. In addition, you do not enable compression because you assume that the speed increase will be minimal.

If your client’s live production server were a physically different server, you might use the following syntax:

```
rsync -avrz -e ssh /home/widgets/staging/* widgets@live:/home/widgets/live
```

Alternatively, if your client used load balancing across three servers, you would have to execute the deployment three times, once for each target server:

```
rsync -avrz -e ssh /home/widgets/staging/* widgets@web01:/home/widgets/live
rsync -avrz -e ssh /home/widgets/staging/* widgets@web02:/home/widgets/live
rsync -avrz -e ssh /home/widgets/staging/* widgets@web03:/home/widgets/live
```