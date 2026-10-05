# 654

# Source Code

```
d = data;
for(i=0;i<blocks;i++)
    Blowfish_decipher(c,d,d+1);
    d += 2;
}

void main(void) {
    blf_ctx c;
    char key[]="AAAA"
    unsigned long data[10];
    int i;

    for(i=0;i<10;i++) data[i] = i;

    blf_key(&c,key,5);
    blf_enc(&c,data,5);
    blf_dec(&c,data,1);
    blf_dec(&c,data,2,4);
    for(i=0;i<10;i++) printf("Block %0x decrypts to %08lx %08x.\n", i,data[i],data[i+1]);
}
```

# 3-Way

```
#define STR_F 0xb0b /* round constant of first encryption */
#define STR_D 0xb61 /* round constant of first decryption */
#define NMBR 11 /* number of rounds is 11
```

```
typedef unsigned long int word32;
/* the program only works correctly if long = 32bits */
typed unsigned u4;
typ unsigned char ul;
```

```
typedef struct {
    u4 k[3],ki[3],encron[NMBR+1],dcon[NMBR+1];
} twy_ctx;
```

> /* encrypt and decrypt full blocks--padding blocks
caller's responsibility. All encryption is done in
ECB mode by these calls. Other modes may be added
enough. */

> /* destroy: Context. */
/* Scrub context of all sensitive data. */
void twy_destroy(twy_ctx *);

> /* encrypt: ptr to data block, # of blocks. */
void twy_enc(twy_ctx *, u4 *, int);

> /* decrypt: ptr to data block, # of blocks. */
void twy_dec(twy_ctx *, u4 *, int);