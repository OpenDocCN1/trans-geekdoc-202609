You can also import several classes, constants, or functions at once in a single use statement:

```
use const myNS\{versionMajor, versionMinor as minor\}
```

Finally, it has been made possible to include an additional comma at the very end when importing a group via use, similar to functions (see Chapter 6). The potential meaning of this arises when the code is formatted:

```
use const myNS\{
    versionMajor,
    versionMinor,
    minor,
\}
```

Imagine that an additional constant is imported at a later point in time:

```
use const myNS\{
    versionMajor,
    versionMinor,
    minor,
    major,
\}
```

Only the line highlighted in bold is new (because the comma you need was already there before). In a vision management system, only this line would be displayed as changed. There is no difference in purely functional terms, but this is a small but important detail.