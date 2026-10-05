# 358 Part II: Solutions

The results of executing the script in Listing II.13.1 may look as seen in Fig. II.13.1.
As can be seen in Fig. II.13.1, the results of sending four Internet control message protocol (ICMP) echo packets, all of which made it through, are displayed in the browser window.

# II.13.2. The File Inode

The file's inode is obtained with the help of the fileinode() function. A script for using this function to solve the posed posed problem is shown in Listing II.13.2.

# Listing II.13.2. Obtaining the file's inode

```
<form method="post"><table>
<tr><td>File name</td><td><input type="text" name="filename"
value=<?php echo $_POST['filename']; ?>"></td></tr>
<tr><td></td><td><input type="submit" value="Check"></td></tr>
</table></form>
<?php
if(!empty($_POST['filename']))
{
    echo fileinode($_POST['filename']);
}
n?>
```

![](bbox=[0.16362000000000002, 0.66367, 0.95238, 0.9136799999999999])