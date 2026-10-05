# LOKI91

```
extern void deloki(char *);
extern void setlokey(char key[LOKIBLK]);
@else /* else declare library functions *
extern void enoki(), deloki(), setlokey());
#endif _STDC_
```

```
char P[32] = {
    31, 23, 15, 7, 30, 22, 14, 6,
    29, 21, 13, 5, 28, 20, 12, 4,
    27, 19, 11, 3, 26, 18, 10, 2,
    25, 17, 9, 1, 24, 16, 8, 0};
```

```
typedef struct {
    short gen; /* irreducible polynomial used in this field *
    short exp; /* exponent used to generate this s function *
    sfn_desc;
};
```

```
sfn_def sfn[] = {
    /* 101110111 * 375, 311, /* 101110111 * 379, 311,
    /* 110000011 * 391, 311, /* 110000011 * 395, 311,
    /* 110001111 * 397, 311, /* 110011111 * 415, 311,
    /* 101000111 * 419, 311, /* 101010101 * 425, 311,
    /* 110110100 * 433, 311, /* 110111111 * 445, 311,
    /* 110011111 * 451, 311, /* 110111101 * 463, 311,
    /* 110111011 * 471, 311, /* 111110101 * 477, 311,
    /* 111100111 * 487, 311, /* 111100111 * 499, 311,
    00, 00};
```

```
typedef struct {
    Long loki_subkeys[ROUNDS];
    loki_ctx;
};
```

```
static long f(); /* declare LOKI function *
static short s(); /* declare LOKI S-box fn *
```

```
#define ROL12(b) = ((b << 12) | (b >> 20));
#define ROL13(b) = ((b << 13) | (b >> 19));
```

```
#ifndef LITTLE_ENDIAN
#define bswap(cb) {
    register char c;
    c = cb[0] = cb[3]; cb[3] = c; \
    c = cb[1] = cb[2]; cb[2] = c; \
    c = cb[4] = cb[7]; cb[7] = c; \
    c = cb[5] = cb[6]; cb[6] = c; \
}
#endif
```

```
void
setlokey(loki_ctx, char *key)
{
    register i;
    register Long KL, KR;
};
```