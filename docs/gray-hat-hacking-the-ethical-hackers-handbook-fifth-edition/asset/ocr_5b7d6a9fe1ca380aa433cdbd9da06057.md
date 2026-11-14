```
//fmtstr.c
#include <string.h>
#include <stdio.h>
int main(int argc, char *argv[]){
    static int canary=0;    // stores the canary value in .data section
    char temp[2048];        // string to hold large temp string
    strcpy(temp, argv[1]);  // take argv1 input and jam into temp
    printf(temp);           // print value of temp
    printf("\n");           // print carriage return
    printf("Canary at 0x%08x = 0x%08x\n", &canary, canary); //print canary
}
```

```
#gcc -o fmtstr fmtstr.c
# ./fmtstr Testing
Testing
Canary at 0x80002028 = 0x00000000
#chmod u+s fmtstr
$
```

![](bbox=[0.13, 0.43, 0.26, 0.51])

NOTE The canary value is just a placeholder for now. It is important to realize that your value will be different. For that matter, your system might produce different values for all the examples in this chapter; however, the results should be the same.

# Lab 12-1: Reading from Arbitrary Memory

We will now begin to take advantage of the vulnerable program. We will start slowly and then pick up speed. Buckle up, here we go!

![](bbox=[0.13, 0.69, 0.26, 0.77])

NOTE This lab, like all the labs, has a unique README file with instructions for setup. See the Introduction for more information.

# Using the %x Token to Map Out the Stack

As shown in Table 12-1, the %x format token is used to provide a hex value. So, by supplying a few %08x tokens to our vulnerable program, as shown here, we should be able