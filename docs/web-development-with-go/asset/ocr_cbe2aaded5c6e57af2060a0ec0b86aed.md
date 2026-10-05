# CHAPTER 16. DEPLOYING TO PRODUCTION

```
# Change to the directory with our code that we plan to work from
cd "$GOPATH/src/lenslocked.com"
```

After that we can start the release by deleting any binaries that exist they aren't uploaded. I tend to call mine lenslocked.com when I build them, so that is what I will be deleting. We are NOT deleting the lenslocked.com directory, but a binary inside it of named lenslocked.com.

```
echo "==== Releasing lenslocked.com ===="
echo "Deleting the local binary if it exists (so it isn't uploaded)..."
rm lenslocked.com
echo "Done!"
```

We are going to upload our source code to the server to build, but first we should delete any source code on the server to make sure we don't have any files accidentally leftover from a previous build.

```
echo "Deleting existing code.."
sh root@123.123.22.33 "rm -rf /go/root/src/lenslocked.com"
echo "Code deleted successfully!"
```

After that we can upload our source code. We will be using rsync¹ an incredibly useful tool for transferring and synchronizing files across different servers. If you haven't ever used it I highly recommend digging further into it.

For now what I'll say is that the flags we are using rsync to print out a little more information, to work recursively (getting files in nested folders), and the exclude flags tell it not to sync files from a few directories that aren't intended to be copied to our server.

> ¹²https://en.wikipedia.org/wiki/Rsync