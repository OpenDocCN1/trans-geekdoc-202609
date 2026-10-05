# 16.7. SETTING UP A SERVER

```
echo "Uploading code..."
# The \ at the end of the line tells bash to the next line,
sync -avr --exclude '.git*' --exclude 'tmp*' \
--exclude 'images/*' /. /\nroot@123.123.22.33:/root/go/scrc/lenslocked.com/
echo "Code uploaded successfully!"
```

Once our code is uploaded we are ready to start running commands on the server and building our code. The first step in our build process is to get any third party libraries our application is using. To do this we will use the ssh command and pass in whatever commands we need our server to execute as an additional argument.

```
echo "Go getting deps..."
sh root@123.123.22.33 "export GOPATH=/root/go; \
/usr/local/go/bin/go get golang.org/x/crypto/bcrypt"
sh root@123.123.22.33 "export GOPATH=/root/go; \
/usr/local/go/bin/go get github.com/gorilla/mux"
sh root@123.123.22.33 "export GOPATH=/root/go; \
/usr/local/go/bin/go get github.com/gorilla/schema"
sh root@123.123.22.33 "export GOPATH=/root/go; \
/usr/local/go/bin/go get github.com/lib/pq"
sh root@123.123.22.33 "export GOPATH=/root/go; \
/usr/local/go/bin/go get github.com/inzhuhu/orm"
sh root@123.123.22.33 "export GOPATH=/root/go; \
/usr/local/go/bin/go get github.com/gorilla/csrf"
```

> Note: Whenever you add new packages to your source code you will need to update this version of your release script, or alternatively you could look into using a package manager like dep¹³.

With all of our third party packages installed we can build our own application. We are going to use the -o flag to define the name of our resulting binary, and we will build from within our /root/app directory so that our binary is created.

¹³https://github.com/golang/dep