# Core PHP Programming

The posix_getpwuid function returns an array describing an entry in the user database based on a given user ID. The elements of the array are dir, gecos, gid, name, password, shell, uid. These are the same elements returned by posix_getwnam.

# array posix_getrimit()

The posix_getrlimit function returns an array describing system resource usage. The array contains elements with hard and soft followed by a space and one of the following limit names: core, cpu, data, filesize, maxproc, memlock, openfiles, rss, stack, totalmem, virtualmem.

Figure 8-6. posix_getrlimit.

![](bbox=[0.198, 0.316, 0.403, 0.735])

```
<<?nforeach(posix_getrlimit() as $key=>$value {
    print("$key: $value<BR>\n");
}?>
```

# integer posix_getgid()