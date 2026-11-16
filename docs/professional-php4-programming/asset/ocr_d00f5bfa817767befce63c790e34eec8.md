| Commands | Description |
|---|---|
| W $variable | This command sets a watch-point on the variable $variable. |
| Step or SI | Causes the debugger to single-step through each statement in the script. The current statement is displayed in bold. This command steps over functions, except include(), and SI n causes the debugger to step through n number of statements. |
| G line or Go line | Causes the program to execute until it reaches the line number line. Go with no line number causes the program to continue until it encounters a breakpoint or exit. |
| B expression or BREAK expression | This causes the execution to pause when expression evaluates to true. |
| DB n | Causes breakpoint number n to be deleted. |
| SO | Causes execution to continue until the end of the current function is reached. In other words this causes execution to step out of the current function. |
| Exec statement | This causes the execution of statement, thereby allowing us to modify variables on the fly. For example, Exec $I = 36; |
| Reset | Deletes all watch-points and breakpoints. |

We see that using BODY, we can pinpoint the erroneous pop function, which can be fixed as shown below:

```
function pop()
{
 if ($this->isEmpty())
 {
 echo("Stack empty<br>");
 return -1;
 } else {
 $ret = $this->vector[$this->stackPointer];
 --$this->stackPointer;
 return $ret;
 }
}
```

# Zend IDE

The Zend IDE is a commercial offering available at http://www.zend.com/. It has an integrated debugger comparable with debugging solutions seen with other established languages. A debug server is required for the IDE-based debugger to function. This is a commercial offering requiring licensing (more information at http://www.zend.com/).

We need to have the Java runtime environment installed for the client to work. The Zend IDE and the debug server are distributed as binaries for both Windows and UNIX. Trial downloads are available from the Zend web site. Please follow the setup instructions that come with the binaries, which involves obtaining and setting up licenses.