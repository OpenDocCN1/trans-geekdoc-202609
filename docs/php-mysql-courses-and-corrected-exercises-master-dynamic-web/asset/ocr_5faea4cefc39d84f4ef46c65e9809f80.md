| Permissions | Symbol | Value | Description |
|---|---|---|---|
| Read | r | 4 | Allows reading |
| Write | w | 2 | Allows writing |
| Execute | x | 1 | Allows execution |

# Examples:

7 (4 + 2 + 1): means the owner has read, write and execute permission.
6 (4 + 2): means that the owner has read and write permission, but not execute permission.
5 (4 + 1): means that the owner has read and execute permission, but not write permission.

So the number **641** grants the file owner read and write permission (6 = 4 + 2), the group only read permission (4) and others only execute permission (1).

Here's an example of how to use the **chmod()** function to change file permissions:

```
<?php
```