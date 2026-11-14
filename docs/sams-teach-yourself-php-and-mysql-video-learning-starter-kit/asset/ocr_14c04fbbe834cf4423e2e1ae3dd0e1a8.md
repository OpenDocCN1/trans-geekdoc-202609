container allows regular expression patterns to be specified as an argument. For example, the following allows a match of all second-level subdirectories of the www directory and made up of four numbers, such as a directory named after a year and month (0906 for September 2006):
<DirectoryMatch "^/www.*/[0-9]{4}">

+   ■ <Location>, <LocationMatch>—These containers allow directives to apply to certain requested URLs or URL patterns. They are similar to their Directory counterparts. LocationMatch takes a regular expression as an argument. For example, the following matches directories containing either "/my/data" or "/your/data":
+   <LocationMatch "^/(\my;your)/data">

+   ■ <Files>, <FilesMatch>—Similar to the Directory and Location containers, Files sections allow directives to apply to certain files or file patterns.

Containers surround directives, as shown in Listing 3.1.

```
LISTING 3.1 Sample Container Directives
1: <Directory "/some/directory">
2:   SomeDirective1
3:   SomeDirective2
4: </Directory>
5: <Location "/downloads/*.html">
6:   SomeDirective3
7: </Location>
8: <Files "\.(gif|jpg)">
9:   SomeDirective4
10: </Files>
```

Sample directives SomeDirective1 and SomeDirective2 apply to the directory /some/directory and its subdirectories. SomeDirective3 applies to URLs referring to pages with the .html extension under the /downloads/ URL. SomeDirective4 will apply to all files with .gif or .jpg extensions.

# Conditional Evaluation

Apache provides support for conditional containers. Directives enclosed in these containers will be processed only if certain conditions are met.