# RC5 659

```
printvec("KEY = *,k);\nprintvec("PLAIN = *,a);\nncrypt(&gc,a);
printvec("CIPHER = *,a");
```

```
/* TEST VALUES

key : 00000000 00000000 00000000
plaintext : 00000001 00000001 00000001
ciphertext : ad21ec7 83ae9dc4 4059c76e

key : 00000004 00000005 00000006
plaintext : 00000001 00000002 00000003
ciphertext : cab920cd d6144138 d2f05b5e

key : bcdfe012 456789ab def01234
plaintext : 01234567 9abcdef02 23456789
ciphertext : 7cd7b6b2 9cddd0b6 0aa55ddb

key : cab920cd d6144138 d2f05b5e
plaintext : ad21ec7 83ae9dc4
ciphertext : 15b15ff5 6b13f17c 478ea871
*/
```

```
/* Enc/dec test: *\nfor(i=0;i<9;i++) a[i]=a[i];\ntwy_enc(&gc,a,3);
for(i=0;i<9;i++) printf("Block %01d encrypts to 0x81x 0x81x 0x81x\n", i/3,a[i],a[i+1],a[i+2]);
```

```
twy_dec(&gc,a,2);
twy_dec(&gc,a,6,1);
```

```
for(i=0;i<9;i+=3) printf("Block %01d decrypts to 0x81x 0x81x 0x81x\n", i/3,a[i],a[i+1],a[i+2]);
```

# RC5

```
#include <stdio.h>
```

```
/* An RC5 context needs to know how many rounds it has, and its subkeys. */\ntype struct {
 u4 *xk;
 int nr;
} rc5_ctx;
```

```
/* Where possible, C++, these should be replaced with actual instructions. */\nFor Turbo, this is done with _lrot and _rrot. */
```

```
#define ROT32(X,C) (((X)<<(C))|((X)>>(32-(C))))\n#define ROT32(X,C) (((X)>>(C))|((X)<<(32-(C))))
```