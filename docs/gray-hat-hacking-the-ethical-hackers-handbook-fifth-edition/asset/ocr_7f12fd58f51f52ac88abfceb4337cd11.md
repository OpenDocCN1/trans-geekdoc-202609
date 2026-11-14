![](bbox=[0.135, 0.082, 0.255, 0.165])

NOTE At this time, we will switch to Kali Linux 2017, which you can download from kali.org.

```
```
root@kali:~/afl-2.41b# cat input/file.txt
aaaaaaa
root@kali:~/afl-2.41b# cat asdf3.c
#include <stdio.h>
#include <stdlib.h>
#code adapted with permission from Gynvael -
#https://github.com/gynvael/stream-en/tree/master/019-genetic-fuzzing
```
```

```
```
int main(int argc, char **argv) {
    FILE *f = fopen(argv[1], "rb");
    if (!f) {
        return 1;
    }

    char buf[16] = {0};
    fread(buf, 1, 16, f);
    fclose(f);

    if (buf[0] == 'a') {
        if (buf[1] == 'b') {
            if (buf[2] == 'c') {
                if (buf[3] == 'd') {
                    if (buf[4] == 'e') {
                        if (buf[5] == 'f') {
                            if (buf[6] == 'g') {
                                if (buf[7] == 'h') { ① abort();
                                }
                            }
                        }
                    }
                }
            }
        }
    }
    return 0;
}
```
```

The abort() statement at ① will cause the program to crash. The question is whether the fuzzer will find it. Using a mutation fuzzer, if we submit one input file at a time, we would have a 1 in 256^8 chance of hitting that innermost code block. If your computer was able to process 1,000 files per second (and you were unlucky), it might take upward of a number