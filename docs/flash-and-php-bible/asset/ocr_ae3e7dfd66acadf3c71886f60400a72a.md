```
$dir = preg_replace('//$/', '', $dir);
$archiveName = preg_replace('/^(.*)\..*?/', '', $dir);
```

After you define the archive name, the next step is to build the command that will create the archive file.

```
$tgzName = "{$archiveName}-{$date}.tgz";
$tgzFile = "{$backupDir}/{$tgzName}";
$backupCmd = "tar czf {$tgzFile} {$archiveName}";
```

The $backupCmd variable is passed into the system command, which informs PHP to run the passed-in command at the system level of your Web server. This would be the same as executing the command in the command prompt or terminal.

```
$result = system($backupCmd . " 2>&1");
```

For debugging purposes you may want to output the command in case an error occurs, as well as the original command to ensure the structure is properly defined.

```
print "Command: " . $backupCmd . "<br />";
print "Result: " . $result;
```

That is the end of the file backup script. As you can see, the structure of this script is straightforward and the only important aspect is the system function, which could be disabled in some environments.

Here is the completed script, which you reference in the crontab file to automate the process.

```
<?php
// File Backup
$dirs = array("/var/www/vhosts/example.org/myfiles");
$backupDir = "/var/www/vhosts/example.org/backups";
$date = date('m-d-y');
foreach($dirs as $dir)
{
    $dir = preg_replace('//$/', '', $dir);
    $archiveName = preg_replace('/^(.*)\..*?/', '', $dir);
    $tgzName = "{$archiveName}-{$date}.tgz";
    $tgzFile = "{$backupDir}/{$tgzName}";
    $backupCmd = "tar czf {$tgzFile} {$archiveName}";
    $result = system($backupCmd . " 2>&1");
    print "Command: " . $backupCmd . "<br />";
}
```