
# IDEA

```c
ideaCipher(byte *inbuf, byte *outbuf, word16 *key)
  register uint16 x1, x2, x3, x4, s2, s3;
  word16 *in, *out;
#ifdef SMALL_CACHE
  register uint16 t16; // Temporaries needed by MUL macro *
  register word32 t32;
#endif
  int r = IDEAROUNDS;

  in = (word16*)inbuf;
  x1 = *in++; x2 = *in++;
  x3 = *in++; x4 = *in;
#ifdef HIGHFIRST
  x1 = (x1 >> 8) | (x1 << 8);
  x2 = (x2 >> 8) | (x2 << 8);
  x3 = (x3 >> 8) | (x3 << 8);
  x4 = (x4 >> 8) | (x4 << 8);
#endif
  do
    MUL(x1, *key++);
    x2 += *key++;
    x3 += *key++;
    MUL(x4, *key++);

    s3 = x3;
    x3 ^= x1;
    MUL(x3, *key++);
    s2 = x2;
    x2 ^= x4;
    x2 += s3;
    MUL(x2, *key++);
    x3 ^= x2;

    x1 ^= x2; x4 ^= x3;
  } while (--r);
  MUL(x1, *key++);
  x3 += *key++;
  x2 += *key++;
  MUL(x4, *key);

  out = (word16*)outbuf;
#ifdef HIGHFIRST
  *out++ = x1;
  *out++ = x3;
  *out++ = x2;
  *out++ = x4;
#else /* !HIGHFIRST */
  *out++ = (x1 >> 8) | (x1 << 8);
  *out++ = (x3 >> 8) | (x3 << 8);
  *out++ = (x2 >> 8) | (x2 << 8);
  *out++ = (x4 >> 8) | (x4 << 8);
#endif
}
/* * ideaCipher */
```

## 642 Source Code

```c
void idea_key(idea_ctx *c, unsigned char *key) {
    ideaExpandKey(key, c->ek);
    ideaInvertKey(c->ek, c->dk);
}

void idea_enc(idea_ctx *c, unsigned char *data, int blocks) {
    int i;
    unsigned char *d = data;
    for(i=0; i<blocks; i++) {
        ideaCipher(d, d, c->ek);
        d+=8;
    }
}

void idea_dec(idea_ctx *c, unsigned char *data, int blocks) {
    int i;
    unsigned char *d = data;
    for(i=0; i<blocks; i++) {
        ideaCipher(d, d, c->dk);
        d+=8;
    }
}

#include <stdio.h>
#ifndef BLOCKS
#ifndef BYTES
#define BYTES 1024
#endif
#define BLOCKS (64*BYTES)
#endif

int main(void)
{
    int i, j, k;
    idea_ctx c;
    byte userkey[16];
    word16 EK[IDEAKEYLEN], DK[IDEAKEYLEN];
    byte XX[8], YY[8], ZZ[8];
    word32 long_block[10]; /* 5 blocks */
    long i;
    char *lbp;

    /* Make a sample user key for testing... */
    for(i=0; i<16; i++)
        userkey[i] = i+1;

    idea_key(&c, userkey);

    /* Make a sample plaintext pattern for testing... */
    for (k=0; k<8; k++)
        XX[k] = k;

    idea_enc(&c, XX, 1); /* encrypt */

    lbp = (unsigned char *)long_block;
    for(i=0; i<10; i++) long_block[i] = i;
    idea_enc(&c, lbp, 5);
    for(i=0; i<10; i+=2) printf("Block %01d = %08x %08x\n",
        i/2, long_block[i], long_block[i]);

    idea_dec(&c, lbp, 3);
    idea_dec(&c, lbp+2, 4);

    for(i=0; i<10; i+=2) printf("Block %01d = %08x %08x\n",
        i/2, long_block[i], long_block[i+1]);

    return 0;
    /* normal exit */
}
```

## GOST

```c
typedef unsigned int u4;
typedef unsigned char byte;

typedef struct {
    u4 k[8];
    /* Constant boxes - set up in gost_init().*/
    u4 k8[256], k7[256], k6[256], k5[256], k4[256], k3[256], k2[256], k1[256];
} gost_ctx;

/* Note: encrypt and decrypt full blocks is the caller's responsibility. 
   All bulk encryption is done in ECB mode. */
void gost_enc(gost_ctx *c, u4 *, int);
void gost_dec(gost_ctx *c, u4 *, int);
void gost_key(gost_ctx *c, u4 *k);
void gost_init(gost_ctx *c);
void gost_destroy(gost_ctx *c);

#ifdef __alpha /* Any 64-bit machines? */
typedef unsigned int word32;
#else
typedef unsigned long word32;
#endif

byte k[16] = {14, 4, 13, 1, 2, 15, 11, 8, 3, 10, 6, 12, 5, 9, 0, 7};
byte k7[16] = {15, 1, 8, 14, 6, 11, 3, 4, 9, 7, 2};
byte k6[16] = {10, 0, 9, 14, 6, 3, 5, 1, 13, 12, 7, 11, 4, 8};
byte k5[16] = {7, 13, 3, 0, 6, 9, 10, 1, 2, 8, 5, 11, 12, 4, 15};
byte k4[16] = {2, 12, 7, 10, 11, 6, 8, 5, 3, 15, 13, 0, 14, 9};
byte k3[16] = {12, 1, 10, 15, 9, 2, 6, 0, 4, 14, 7, 5, 11};
byte k2[16] = {4, 11, 2, 14, 15, 0, 8, 13, 12, 7, 5, 10};
byte k1[16] = {13, 2, 8, 6, 15, 11, 10, 9, 3, 14, 5, 0, 12};

for (i = 0; i < 256; i++) {
    c->k8[i] = k[i%16] >> 4;
    c->k7[i] = (k[i%16] & 0x0F);
    c->k6[i] = k7[(i+1)2256] >> 4;
    c->k5[i] = (k7[(i+1)%256] & 0x0F);
    c->k4[i] = k6[(i+1)%256] >> 4;
    c->k3[i] = (k6[(i+1)%256] & 0x0F);
    c->k2[i] = k5[(i+1)%256] >> 4;
    c->k1[i] = (k5[(i+1)%256] & 0x0F);
}

static word32 gost(gost_ctx *ctx, word32 x) {
    x ^= ctx->k8[(x >> 24) & 0xFF];
    x ^= ctx->k7[(x >> 16) & 0xFF];
    x ^= ctx->k6[(x >> 8) & 0xFF];
    x ^= ctx->k5[x & 0xFF];
    x ^= ctx->k4[(x >> 24) & 0xFF];
    x ^= ctx->k3[(x >> 16) & 0xFF];
    x ^= ctx->k2[(x >> 8) & 0xFF];
    x ^= ctx->k1[x & 0xFF];
    return x << 11; /* Rotate left 11 bits */
}

void gostcrypt(gost_ctx *ctx, word32 *d) {
    register word32 n1 = d[0];
    word32 n2 = d[1];
    /* Instead of swapping halves, swap each round */
    for (i = 0; i < 32; i++) {
        n2 = gost(ctx, n1+ctx->k[0]);
        n1 = gost(ctx, n2+ctx->k[1]);
        n2 = gost(ctx, n1+ctx->k[2]);
        n1 = gost(ctx, n2+ctx->k[3]);
        n2 = gost(ctx, n1+ctx->k[4]);
        n1 = gost(ctx, n2+ctx->k[5]);
        n2 = gost(ctx, n1+ctx->k[6]);
        n1 = gost(ctx, n2+ctx->k[7]);

        n2 ^= f(ctx, n1+ctx->k[3]);
        n1 ^= f(ctx, n2+ctx->k[2]);
        n2 ^= f(ctx, n1+ctx->k[1]);
        n1 ^= f(ctx, n2+ctx->k[0]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);

        n2 ^= f(ctx, n1+ctx->k[7]);
        n1 ^= f(ctx, n2+ctx->k[6]);
        n2 ^= f(ctx, n1+ctx->k[5]);
        n1 ^= f(ctx, n2+ctx->k[4]);
    }
    d[0] = n1;
    d[1] = n2;
}
```

void main(void) {
    gost_ctx gc;
    u4 k[8], data[10];
    int i;

    /* Initialize context. */
    gost_init(&gc);

    /* Prepare -- simple key should be OK, with many rounds! */
    for(i=0; i<8; i++) k[i] = i;
    gost_key(&gc, k);

    /* Try some test vectors. */
    data[0] = 0; data[1] = 0;
    gost_crypt(&gc, data);
    printf("Enc of zero vector: %08x %08x\n", data[0], data[1]);
    gost_decrypt(&gc, data);
    printf("Enc of above: %08x %08x\n", data[0], data[1]);

    data[0] = 0xffffff;
    gost_crypt(&gc, data);
    printf("Enc of ones vector: %08x %08x\n", data[0], data[1]);
    gost_decrypt(&gc, data);
    printf("Enc of above: %08x %08x\n", data[0], data[1]);

    /* Does gost_dec() reverse gost_enc()? Do we deal OK with 
       single-block lengths passed in gost_dec() we do OK with different lengths passed in? */ */
    for(i=0; i<10; i++) data[i] = i;

    /* Encrypt data as 5 blocks. */
    gost_enc(&gc, data, 5);

    /* Display encrypted data. */
    for(i=0; i<10; i+=2) printf("Block %02d = %08x %08x\n", i/2, data[i], data[i+1]);

    /* Decrypt in different sized chunks. */
    gost_dec(&gc, data, 1);
    gost_dec(&gc, data+2, 4);
    printf("%s\n");

    /* Display decrypted data. */
    for(i=0; i<10; i+=2) printf("Block %02d = %08lx %08lx\n", i/2, data[i], data[i+1]);

    gost_destroy(&gc);
}
```

## BLOWFISH

```c
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#ifdef little_endian /* Eg: Intel */
#include <alloc.h>
#endif
#include <ctype.h>

#ifdef little_endian /* Eg: Intel */
#include <dir.h>
#include <blos.h>
#endif

#ifdef big_endian
#include <Types.h>
#endif

typedef struct {
    unsigned S[4][256], P[18];
} blf_ctx;

#define MAXKEYBYTES 56        /* 448 bits */
// define little_endian 1    /* Eg: Intel */
#define big_endian 1         /* Eg: Motorola */
```
