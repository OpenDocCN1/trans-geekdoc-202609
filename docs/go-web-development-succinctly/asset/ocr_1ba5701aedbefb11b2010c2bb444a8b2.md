![](bbox=[0.118, 0.076, 0.881, 0.413])

You might next need to close and re-open any command-line sessions in order for the changes to take effect.

# Mac OS X

Download the .pkg file and follow the prompts. The package installs the Go distribution to /usr/local/go and adds /usr/local/go/bin to your PATH.

# Linux, Unix, and FreeBSD

You'll notice that 'nix-based systems expect a bit more from you. But as a 'nix user, you are more than the challenge to choose.

Download the .tar.gz file and extract it to /usr/local as the root user, or get it via sudo:

```
sudo tar -C /usr/local -xzf $GOVERSION.$OS-$GOARCH.tar.gz
```

You may need to add /usr/local/go/bin permanently to your PATH. Put the following line in your /etc/profile (for all users) or ~/.profile (for only you) to make this a permanent thing:

```
export PATH=$PATH:/usr/local/go/bin
```

# Custom installation locations

Those methods decide where Go will be installed. If you don't like to be bossed around that way, you must tell Go where to find itself by setting the GOROOT environment variable. If you're happy with the default location, then doesn't specify GOROOT. You'll only confuse things.