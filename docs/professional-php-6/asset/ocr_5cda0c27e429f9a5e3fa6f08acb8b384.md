```
$objPDO = NULL;

} catch (PDOException $e) {
echo "An error occurred connecting: " . $e->getMessage() . "<br />\n";
list($strCode, $strCode2, $strInfo) = $objPDO->errorInfo();
print "PDO: - Code was '$strCode',<br /> - Driver code was '$strCode2',<br /> - Info string was '$strInfo',";
if ($objStatement instanceof PDOStatement) {
list($strCode, $strCode2, $strInfo) = $objStatement->errorInfo();
print "<br /><br />PDO Statement: - Code was '$strCode',<br /> - Driver code was '$strCode2',<br /> - Info string was '$strInfo'";
};
exit(0);
}

php?>
```

Run this code (which contains a deliberate error), and you should see something like this:

An error occurred connecting: SQLSTATE[42P01]: Undefined table: 7 ERROR:
relation "udser" does not exist

PDO: - Code was '00000',
- Driver code was '7',
- Info string was 'ERROR: relation "udser" does not exist'

PDO Statement: - Code was '42P01',
- Driver code was '7',
- Info string was 'ERROR: relation "udser" does not exist'

It is hoped that this kind of verbosity makes it very easy to see the error you've trapped — you've made an honest typo. Fix it, refresh, and you should see some very familiar output.

This example has fallen over and died when trapping the error. Naturally, in your enterprise-grade, real-world application, you'll want to be a bit smarter than this. Rather than simply dump the information available to you to the screen, you'd be wise to use a switch() statement or similar to make some decision regarding what error message to display — if, indeed, you display one at all.

One final word of warning: Don't tell the user too much. Not only is this tiresome and useless from a usability point of view (why would the user care what table is missing?), but it also exposes your database schema to the outside world. From a security perspective, that's best avoided.

# Advanced PDO Techniques

So far, you've learned about the basics of PDO. It is hoped that you're now confident how to use it in your projects in place of traditional procedural connectivity or third-party unofficial wrapper classes.

There are a few topics that are still worth covering, though. Don't expect too much detail here — they're big topics in their own right, and some of them you'll meet in more detail later in this book. However, by scratching the surface of each here, you can learn why you should not be tempted to revert back to bad habits as the complexity of your projects increases.