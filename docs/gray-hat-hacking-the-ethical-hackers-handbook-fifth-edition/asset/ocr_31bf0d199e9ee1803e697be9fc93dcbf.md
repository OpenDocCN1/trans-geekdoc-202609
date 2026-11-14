little sloppy and point to somewhere in the middle of the NOP sled. To do that, the first
thing you need to know is the current ESP value, which points to the top of the stack. The
gcc compiler allows you to use assembly code inline and to compile programs as follows:

```
#include <stdio.h>
unsigned int get_sp(void){
        __asm__("movl %esp, %eax");
}
int main(){
        printf("Stack pointer (ESP): 0x%x\n", get_sp());
}
# gcc -o get_sp get_sp.c
# ./get_sp
Stack pointer (ESP): 0xbffff2f8     //remember that number for later
```

Remember the ESP value; we will use it soon as our return address, though yours will be
different.

At this point, it may be helpful to check whether your system has ASLR turned on. You
can check this easily by simply executing the last program several times in a row, as shown
here. If the output changes on each execution, then your system is running some sort of
stack randomization scheme.

```
# ./get_sp
Stack pointer (ESP): 0xbfe90d88
# ./get_sp
Stack pointer (ESP): 0xbfca1cc8
# ./get_sp
Stack pointer (ESP): 0xbfe88088
```

Until you learn later how to work around this situation, go ahead and disable ASLR, as
described in the Caution earlier in this chapter:

```
# echo "0" > /proc/sys/kernel/randomize_va_space
```

Now you can check the stack again (it should stay the same):

```
# ./get_sp
Stack pointer (ESP): 0xbffff2f8
# ./get_sp
Stack pointer (ESP): 0xbffff2f8     //remember that number for later
```

Now that we have reliably found the current ESP, we can estimate the top of the
vulnerable buffer. If you are still getting random stack addresses, try another one of the
echo lines shown previously.

These components are assembled in the order shown here: