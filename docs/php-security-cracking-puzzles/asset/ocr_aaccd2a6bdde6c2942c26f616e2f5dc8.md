# Chapter II.13: UNIX 359

The results of applying the script in Listing II.13.2 are shown in Fig. II.13.2.
There is no special function for obtaining the file name from its inode. In this case, the UNIX find command can be used as follows:

```
find / -inum 68958 -print
```

Here, the slash (/) means that the search is conducted over the entire file system, although, it can be narrowed to a specific directory. The -inum parameter specifies the inode to look for; the -print parameter tells the utility to output the results to the standard output device. A script to obtain and display the file name from its inode is shown in Listing II.13.3.

# Listing II.13.3. Obtaining the file name from its inode

```
<form method="post"><table>
<tr><td>File name</td><td><input type="text" name="inode" value="<?php echo $_POST['inode']; ?>"></td></td></tr>
<tr><td></td><td><td><input type="submit" value="Check"></td></td></tr>
</table></form>
<?php
if (!empty($_POST)) 
{
  echo "<pre>";
  system("find / -inum $_POST[inode] -print");
  echo "</pre>";
}
```

The results of the script in Listing II.13.3 are shown in Fig. II.13.3.

![](bbox=[0.137, 0.674, 0.863, 0.893])

Fig. II.13.3. Obtaining the file name from its inode