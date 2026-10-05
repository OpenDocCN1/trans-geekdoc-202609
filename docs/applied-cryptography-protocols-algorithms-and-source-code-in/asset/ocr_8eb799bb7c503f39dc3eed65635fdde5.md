# GOST

for (k=0; k<8; k++)
XX[k] = k;

```
idea_enc(&c,XX,1); /* encrypt */

lbp = (unsigned char *)long_block;
for(i=0;i<10;i++) long_block[i] = i;
idea_enc(&c,lbp,5);
for(i=0;i<10;i+=2) printf("Block %01d = %08x %08x\n",
i/2,long_block[i],long_block[i]);
```

```
idea_dec(&c,lbp,3);
idea_dec(&c,lbp+2,4);
```

```
for(i=0;i<10;i+=2) printf("Block %01d = %08x %08x\n",
i/2,long_block[i],long_block[i+1]);
```

```
return 0;
/ * normal exit */
```

# GOST

```
typedef unsigned u4;
typed unsigned char byte;
```

```
typedef struct {
u4 k[8];
/* Constant boxes - set up in gost_init().*/
char k8[256],k25[256],k43[256],k21[256];
gost_ctx;
```

> * Note: encrypt and decrypt expect full blocks--padding blocks is
caller's responsibility. All bulk encryption is done in
ECB mode by these cases. Other methods may be easily eased
enough.*

```
void gost_enc(gost_ctx *, u4 *, int);
void gost_dec(gost_ctx *, u4 *, int);
void gost_key(gost_ctx *, u4 *);nvoid gost_init(gost_ctx *);
void gost_destroy(gost_ctx *);
```

```
#ifdef __alpha /* Any other 64-bit machines? */
typed unsigned int word32;
#else
typed unsigned long word32;
#endif
```

```
kboxinit(gost_ctx *)
int;
```

```
byte k8[16] = {14, 4, 13, 1, 2, 15, 11, 8, 3, 10, 6,
12, 5, 9, 0, 7};
byte k7[16] = {15, 1, 8, 14, 6, 11, 3, 4, 9, 7, 2,
```