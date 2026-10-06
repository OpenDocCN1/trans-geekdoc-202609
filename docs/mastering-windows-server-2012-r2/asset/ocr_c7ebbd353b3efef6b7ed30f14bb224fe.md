Using net use You can use the net use command at the command line. The basic syntax is as follows:

```
net use driveletter \servername\sharename
```

For example, to attach to the share Apps on the server BFI and then to be able to refer drive Z, you can use this command:

```
net use Z: \BF1\apps
```

If you later want to remove the mapping, you can use this command:

```
net use Z: /delete
```

# **A Set of Credentials Conflicts**

Sometimes when you're trying to attach to a share, you'll get an error message that says something like "A set of credentials conflicts with an existing set of credentials on that share." Here's what's happening. You've already tried to access this share and failed for some reason—perhaps you mistyped a password. The server that you have constructed security about tells that you're a deadbeat, and it doesn't want to hear anything. You need the server to forget about you so that you can start all over. You can do that with the / option

Suppose you've already tried accessing the \BF1\Apps share and apparently failed. It might be that you are actually connected to the share but with no permissions. (We know it doesn't make sense, but it happens.) You can find out what shares are connected to by typing net use by itself. Chances, you'll see that \BF1\Apps is on the list. You need to disconnect from BFI server so that you can start over. To do that, type this:

```
net use \BF1\apps /d
```

Then do other net to make sure that all of those connections cleaned up; you may find that you have multiple attachments to a particular server. Or...in a few cases, you may have to disconnect all of your file shares with this command:

```
net use * /d
```

With all the connections closed, you can try net use again, and it will work.

# **Using net use on a WAN**

Now you are into one of the most difficult situations: connecting to your resources across long distances and great unknowns. If you've ever had to rely on long-distance remote computing, know not to rely on it. But you have a little function in your net arsenal that acts like the "unknown" out of the picture.

Instead of relying on getting to the appropriate name resolution server, getting through to that server, and getting accurate resolution over an inaccurate or unreliable network link, you can now make a drive straight to your server via its IP address. Granted, you now need to know that IP address, but it is a good fail-safe. In our case, we work from several different locations with frame-relay WAN links. The network isn't always good