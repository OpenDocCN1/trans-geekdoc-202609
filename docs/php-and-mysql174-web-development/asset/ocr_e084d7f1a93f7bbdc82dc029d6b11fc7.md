# 396 Chapter 17 Interacting with the File System and the Server

```
$user = posix_getpwuid(fileowner($safe_file));
echo 'File Owner: '.$user['name'].'<br/>';

$group = posix_getgrgid(filegroup($safe_file));
echo 'File Group: '.$group['name'].'<br/>';

echo 'File Permissions: '.decoct(fileperms($safe_file)).'<br/>';
echo 'File Type: '.filetype($safe_file).'<br/>';
echo 'File Size: '.filesize($safe_file).' bytes<br/>';

necho '<h2>h2-File Tests:</h2>' . '_is_dir:isis_dir($safe_file) ? \'true\' : \'false\').'<br' . . 'is_executable: '.is_executable($safe_file) ? \'true\' : \'false\').'<br'' . 'is_file: '.is_file($safe_file) ? \'true\' : \'false\').'<br/>' . 'is_link: '.is_link($safe_file) ? \'true\' : \'false\').'<br/>' . 'is_readable: '.is_readable($safe_file) ? \'true\' : \'false\').'<br/>' . 'is_writable: '.is_writable($safe_file) ? \'true\' : \'false\').'<br/>';
</body></html>
```

The results of one sample run of Listing 17.6 are shown in Figure 17.4.

![](bbox=[0.115, 0.515, 0.765, 0.885])

Figure 17.4 The File Details view shows file system information about a file. Note that permissions are shown in octal format