It's important to note that the user that you're using to run your Go application must have read permissions for both the cert.pem and key.pem files, otherwise ListenAndServeTLS() will return a permission denied error.

By default, the generate_cert.go tool grants read permission to all users for the cert.pem file but read permission only to the owner of the key.pem file. In my case the permissions look like this:

```
$ cd $HOME/code/snippetbox/tls
$ ls -l
total 8
-rw-rw-r-- 1 alex alex 1090 Mar 18 16:24 cert.pem
-rw------- 1 alex alex 1704 Mar 18 16:24 key.pem
```

Generally, it's a good idea to keep the permissions of your private keys as tight as possible and allow them to be read only by the owner or a specific group.

# Source control

If you're using a version control system (like Git or Mercurial) you may want to add an ignore rule so the contents of the tls directory are not accidentally committed. With Git, for instance:

```
$ cd $HOME/code/snippetbox
$ echo 'tls/' >> .gitignore
```