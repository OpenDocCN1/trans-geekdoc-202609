```
---- Entering directory: http://192.168.86.52/wp-admin/ ----
+ http://192.168.86.52/wp-admin/admin.php (CODE:200|SIZE:10531)
==> DIRECTORY: http://192.168.86.52/wp-admin/css/
==> DIRECTORY: http://192.168.86.52/wp-admin/images/
==> DIRECTORY: http://192.168.86.52/wp-admin/includes/
+ http://192.168.86.52/wp-admin/index.php (CODE:200|SIZE:7265)
==> DIRECTORY: http://192.168.86.52/wp-admin/js/
==> DIRECTORY: http://192.168.86.52/wp-admin/maint/
==> DIRECTORY: http://192.168.86.52/wp-admin/network/
==> DIRECTORY: http://192.168.86.52/wp-admin/user/
```

What we've done so far is to check known or expected directories on a web server. Using a word list doesn't guarantee that you are going to identify all directories that are available on the server. If a directory isn't in the wordlist, it won't be identified. We can turn to another tool to help with fuzzing directory names, meaning generating names dynamically based on a set of rules. You may expect at this point that we would turn to Metasploit because it's so useful. You'd be correct. We can use the brute_dirs module. Using this module, you set a format for what a directory name could or should look like. Using the module will run through all possible names that match the format. Here you can see the options available for the module, followed by a format set. We're going to be testing against all words with lowercase characters whose lengths are between one and eight characters.

# **brute_dirs Metasploit Module**

```
msf > use auxiliary/scanner/http/brute_dirs
msf auxiliary(scanner/http/brute_dirs) > info
```

+   Name: HTTP Directory Brute Force Scanner
+   Module: auxiliary/scanner/http/brute_dirs
+   License: BSD License
+   Rank: Normal

Provided by:
et <et@metasploit.com>

Basic options:

| Name | Current Setting | Required | Description |
| --- | --- | --- | --- |
| FORMAT | a,aa,aaa | yes | The expected directory format (a alpha, d digit, A upperalpha) |
| PATH | / | yes | The path to identify directories |
| Proxies | | no | A proxy chain of format type:host:port[,type:host:port][...] |