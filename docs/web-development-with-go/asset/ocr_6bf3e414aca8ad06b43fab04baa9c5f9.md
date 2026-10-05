# 16.7. SETTING UP A SERVER

ping to your IP address. Doing this will vary from provider to provider, but nearly all providers have tutorials explaining how to do this. You typically only need a name (which is the subdomain you are using, if any), an IP address, and a TTL (time to live) which dictates how long DNS servers should cache this record. I typically suggest a short TTL until things are setup correctly, then you can switch to a longer one.

Once you have either setup A record for your domain or decided you aren’t going to you want to verify you can SSH into your server.

```
$ ssh root@123.123.22.33
# or if you setup a domain:
$ ssh root@subdomain.yourdomain.com
```

Note: You may be asked about the authenticity of a host - if so type “yes” and hit enter.

If all went well, you should see a welcome message indicating that you have SSHed into your server. If you want to exit you can either press ctrl+d (even on Mac), or by typing “logout”.

# 16.7.2 Installing PostgreSQL in production

Once your server is set up we are going to setup Postgres. We will need to SSH into your server to do this, so that if you haven’t already.

```
$ ssh root@123.123.22.33
```

> Box 16.6. Do not memorize this setup