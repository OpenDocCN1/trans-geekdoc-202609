# 658

# Source Code

]

```
void printvec(char *chrs, word32 *d) {
    printf("%20s %08x %08x %08x \n", chrs,d[2],d[1],d[0]);
}

main() {
    twy_ctx gc;
    word32 a[9],k[3];
    int i;

    /* Test vector 1. */
    k[0]=k[1]=k[2]=0;
    a[0]=a[1]=a[2]=1;
    twy_key(&gc,k);

    printf("************\n\n    printvec("KEY = %s",k);
    printvec("PLAIN = %s",a);
    encrypt(&gc,a);
    printvec("CIPHER = %s",a);

    /* Test vector 2. */
    k[0]=0xcdef012;k[1]=0x456789ab;k[2]=0xdef01234;
    a[0]=0x1234567;a[1]=0x9abcdef0;a[2]=0x23456789;
    twy_key(&gc,k);

    printf("************\n\n    printvec("KEY = %s",k);
    printvec("PLAIN = %s",a);
    encrypt(&gc,a);
    printvec("CIPHER = %s",a);

    /* Test vector 3. */
    k[0]=0xcab920dc;k[1]=0xd6144138;k[2]=0xd2f05b5e;
    a[0]=0xad21ec7;a[1]=0x83ae9dc4;a[2]=0x40597c6e;
    twy_key(&gc,k);

    printf("************\n");
```