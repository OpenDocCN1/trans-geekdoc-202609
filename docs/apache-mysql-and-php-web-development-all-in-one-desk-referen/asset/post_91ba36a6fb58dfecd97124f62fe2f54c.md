
## Seven quick reference guides — one great price!
## Apache, MySQL, and PHP Web Development
## ALL-IN-ONE DESK REFERENCE
## FOR DUMMIES
## 7 BOOKS IN 1

- Configuring Systems for Apache
- Building Apache Web Sites
- Perl Web Site Automation
- Tcl/Tk Front-End Development
- Dynamic PHP Web Pages
- MySQL Databases on the Web
- Processing Files with Regular Expressions

Jeff Cogswell

![](img/3f967ab8a8fddc723173059f56621648_0_0.png)

## Apache, MySQL, and PHP Web Development All-in-One Desk Reference For Dummies

### World's Greatest Perl Functions

| Function | Description |
| --- | --- |
| chomp | Removes trailing newline characters |
| close | Closes a file |
| closedir | Closes a directory |
| open | Opens a file |
| opendir | Opens a directory |
| split | Splits a string based on a regular expression |
| substr | Looks for a string within another string |
| time | Returns the current time in seconds since the epoch |

### Tcl Syntax

Remember the syntax of a Tcl command:
The command comes first, followed by the parameters, like so:
set x 100
This line stores 100 in the variable called x. If you want to use the results of a command in another command, use backticks to substitute, like so:
puts [expr $x * 5]
This evaluates the expr $x * 5 command first, which takes the value in the variable x, which is 100, and multiplies it by 5; the result is 500. The interpreter replaces everything in brackets with the result to get puts 500. The puts command prints out the result, which is 500.

### Complete MySQL Sample in PHP

Here's a complete MySQL program in PHP that retrieves records from a customer database. You can use this as a starting point for your own PHP/MySQL programs:

```
<?
$connect = mysql_connect("localhost", "phpuser",
"phpass");
$result = mysql_query("select * from phpbase.Customer");
if ($result) {
while ($line = mysql_fetch_assoc($result)) {
print $line['name'].'. '.$line['email'].'<br>';
}
mysql_free_result($result);
}
mysql_close($connect);
?>
```

## Most Useful PHP Functions

| PHP Function | Description |
| :--- | :--- |
| print | Prints text to the .html file. |
| strlen | Returns the length of a string. |
| $_GET | Actually, this isn't a function, but rather a global array. This contains the values passed in from a form via a GET method. For example, this line retrieves the form value called food: $food = $_GET["food"]; |
| $_POST | Again, this is an array, not a function. It contains the values passed in from a form via the POST method. |
| time | Returns the current time in seconds since the epoch. |
| preg_match | Tests for a regular expression match: |

## Matching Repeating Characters in Regular Expressions

Remember that you can allow a pattern to match multiple occurrences of items. Here are the quantifier characters:

| Character | Function |
| :--- | :--- |
| + | Matches one or more occurrences |
| * | Matches zero or more occurrences |
| { } | Matches a specified number of occurrences. For example a{3,5} matches aaa, aaaa, or aaaaa. Or a{6} matches exactly six occurrences of a, as in aaaaaa. |

## A Few Favorite Regular Expression Characters

| Character | Function |
| :--- | :--- |
| . | Matches a single character — any character. |
| \s | Matches whitespace |
| ^ | Signifies the start of line. |
| $ | Signifies the end of line |
| [ ] | Contains a character set, matching a single character. For example, [abc] matches the character a, or the character b, or the character c. |
| ( ) | Groups together for capturing, and for alternatives. |
| \\ | Matches one of these special characters. \\. will match a dot, for example. |

## Matching with Character Sets in Regular Expressions

Inside a character set, the rules for regular expressions change. The set [abc] matches the single character a, the single character b, or the single character c. Further, you can embed the following characters inside your set to change the meaning of the set:

- Including ^ at the beginning of the set will match the inverse of the set. Thus, [^abc] matches all characters except a, b, and c.
- If you want to match the ^ character within a set, put the ^ anywhere except the beginning. Thus, [abc^] matches the characters a, b, c, or ^.
- To match a range of characters, use the hyphen, as in [a-z], which matches any lowercase letter.
- If you want to match the - character in a set (rather than use it as a range), put the - character at the beginning of the set. Thus, [-az] matches the character -, the character a, or the character z.
- If you want your set to include both the - and ^ characters (and you don't want them to signify a range or an inverse, respectively) then put the hyphen first, then the caret. Thus, [^-abc] match the character -, the character ^, or a, b, or c.

## Apache, MySQL, and PHP Web Development

## ALL-IN-ONE DESK REFERENCE FOR DUMMIES®

## Apache, MySQL, and PHP Web Development
ALL-IN-ONE DESK REFERENCE
FOR
DUMMIES

by Jeffrey Cogswell

![](img/3f967ab8a8fddc723173059f56621648_6_0.png)

Wiley Publishing, Inc.

## Apache®, MySQL®, and PHP Web Development All-in-One Desk Reference For Dummies®

Published by
Wiley Publishing, Inc.
111 River Street
Hoboken, NJ 07030-5774

Copyright © 2004 by Wiley Publishing, Inc., Indianapolis, Indiana

Published by Wiley Publishing, Inc., Indianapolis, Indiana

Published simultaneously in Canada

No part of this publication may be reproduced, stored in a retrieval system or transmitted in any form or by any means, electronic, mechanical, photocopying, recording, scanning or otherwise, except as permitted under Sections 107 or 108 of the 1976 United States Copyright Act, without either the prior written permission of the Publisher, or authorization through payment of the appropriate per-copy fee to the Copyright Clearance Center, 222 Rosewood Drive, Danvers, MA 01923, (978) 750-8400, fax (978) 646-8700. Requests to the Publisher for permission should be addressed to the Legal Department, Wiley Publishing, Inc., 10475 Crosspoint Blvd., Indianapolis, IN 46256, (317) 572-3447, fax (317) 572-4447, e-mail: permcoordinator@wiley.com.

Trademarks: Wiley, the Wiley Publishing logo, For Dummies, the Dummies Man logo, A Reference for the Rest of Us!, The Dummies Way, Dummies Daily, The Fun and Easy Way, Dummies.com, and related trade dress are trademarks or registered trademarks of John Wiley & Sons, Inc. and/or its affiliates in the United States and other countries, and may not be used without written permission. All other trademarks are the property of their respective owners. Wiley Publishing, Inc., is not associated with any product or vendor mentioned in this book.

LIMIT OF LIABILITY/DISCLAIMER OF WARRANTY: WHILE THE PUBLISHER AND AUTHOR HAVE USED THEIR BEST EFFORTS IN PREPARING THIS BOOK, THEY MAKE NO REPRESENTATIONS OR WARRANTIES WITH RESPECT TO THE ACCURACY OR COMPLETENESS OF THE CONTENTS OF THIS BOOK AND SPECIFICALLY DISCLAIM ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. NO WARRANTY MAY BE CREATED OR EXTENDED BY SALES REPRESENTATIVES OR WRITTEN SALES MATERIALS. THE ADVICE AND STRATEGIES CONTAINED HEREIN MAY NOT BE SUITABLE FOR YOUR SITUATION. YOU SHOULD CONSULT WITH A PROFESSIONAL WHERE APPROPRIATE. NEITHER THE PUBLISHER NOR AUTHOR SHALL BE LIABLE FOR ANY LOSS OF PROFIT OR ANY OTHER COMMERCIAL DAMAGES, INCLUDING BUT NOT LIMITED TO SPECIAL, INCIDENTAL, CONSEQUENTIAL, OR OTHER DAMAGES.

For general information on our other products and services or to obtain technical support, please contact our Customer Care Department within the U.S. at 800-762-2974, outside the U.S. at 317-572-3993, or fax 317-572-4002.

Wiley also publishes its books in a variety of electronic formats. Some content that appears in print may not be available in electronic books.

Library of Congress Control Number available from publisher

ISBN: 0-7645-4969-3

Manufactured in the United States of America

10 9 8 7 6 5 4 3 2 1

10/RZ/RR/QT/IN

is a trademark of Wiley Publishing, Inc.
