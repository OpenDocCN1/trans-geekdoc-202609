
# Afterword

- 6. Mismatched trust. Almost all currently available cryptographic software assumes that the user is in direct control over the systems which it runs and has a secure path to it. For example, the interfaces to programs like PGP assume that passphrase input always comes from the user over a secure path like the local console. This is not always the case, of course, consider the problem of reading your encrypted mail when logged in over a network connection. What the system designer assumes trusted may not match the needs or intentions of the real users, especially when software can be controlled over insecure networks.

- 7. Poorly understood protocol and service interactions. As systems get bigger and more complex, benign features frequently come back to haunt us, and it’s hard to know where to look when innocent-looking fail. The Internet worm was propagated via an obscure and innocent-looking feature in the sendmail program; how many features in how many programs have unexpected consequences just waiting to be discovered?

- 8. Unrealistic threat and risk assessment. Security experts tend to focus on the threats they know how to model and predict. Unfortunately, attackers focus on what they know how to exploit, and the two are rarely exactly the same. Many “secure” systems are designed without considering what the attacker is likely to do.

- 9. Interfaces that make security expensive and special. If security features are to be used, they must be convenient and transparent enough that people actually turn them on. Only come at the expense of performance or ease of use, and even easier to design mechanisms that invite innocent mistakes. Security should be harder to turn off than on; unfortunately, few systems actually work this way.

- 10. Little broad-based demand for security. This is a well-known problem among everyone who has tied or her fortune to selling security products and services. Until there is widespread demand for transparent security, the tools and infrastructure needed to support it will be expensive and inaccessible to many applications. This is partly a problem of understanding and exposing the threats and risks in real applications and partly a of not designing systems that include security as a basic feature rather than a later add-on.

A complete list and discussion of these kinds of threats could easily fill a book of this size and barely scratch the surface. What makes them especially difficult and dangerous is that there are no magic techniques, beyond good engineering and ongoing scrutiny, for avoiding them. The lesson for the aspiring cryptographer is to respect the limits of the art.

Matt Blaze
New York, NY

# PART V

# SOURCE CODE

1. DES
2. LOKI91
3. IDEA
4. GOST
5. BLOWFISH
6. 3-Way
7. RC5
8. A5
9. SEAL

# DES

```c
@define ENO 0    /* MODE == encrypt */
@define DEI 1    /* MODE == decrypt */

typedef struct {
    unsigned long ek[32];
    unsigned long dk[32];
} desctx;

extern void deskey(unsigned char *, short);
/*
* hexey[8] MODE
* Sets the internal key register according to the hexadecimal
* key contained in the 8 bytes of key, according to the DES,
* for encryption or decryption according to MODE.
*/

extern void usekey(unsigned long *);
/*
cookedkey[32]
```

# Source Code

* Loads the internal key register with the data in cookedkey.
*/

```c
extern void cpkey(unsigned long *);
/*
* cookedkey[32]
* Copies the contents of the internal key register into the storage
* located at &cookedkey[0];
*/
```

```c
extern void des(unsigned char *, unsigned char *);
/*
* Encrypts/Decrypts to decrypt the key currently loaded in the
* internal key register one block of eight bytes at address 'from'
* into the block at address 'to'. They can be the same.
*/
```

```c
static void scrunch(unsigned char *, unsigned long *);
static void unscrunch(unsigned long *, unsigned char *);
static void desfunc(unsigned long *, unsigned long *);
static void cookscrunch(unsigned long *);
```

```c
static unsigned long KnR[32] = 0L;
static unsigned long KnL[32] = 0L;
static unsigned long Kn3[32] = 0L;
static unsigned char DfKey[24] = {
01,02,03,04,05,06,07,89,0ab,0cd,0ef,
0fe,0dc,0ba,98,37,76,54,32,10,
89,0ab,0cd,0ef,01,02,03,067};
```

```c
static unsigned short bitetable[2] = {0200, 0140, 0240, 010, 004, 01};
```

```c
static unsigned long bigbyte[24] = {
0800000L, 0400000L, 0200000L, 0100000L,
0800000L, 0200000L, 0100000L,
0800L, 0400L, 0200L, 0100L,
080L, 040L, 020L, 010L,
08L, 04L, 02L, 01L,
100L, 10L};
```

```c
/* Use the key schedule specified in Standard (ANSI-1981). */
static unsigned char pc1[56] = {
56, 48, 40, 32, 24, 8, 0, 57, 49, 41, 33, 25, 17,
9, 1, 58, 50, 42, 34, 26, 18, 10, 2, 59, 51, 43, 35,
62, 54, 46, 38, 30, 22, 14, 6, 61, 53, 45, 37, 29, 21,
13, 5, 60, 52, 44, 36, 28, 20, 12, 4, 27, 19, 11};
```

```c
static unsigned char pc2[48] = {
1, 2, 4, 6, 8, 10, 12, 14, 15, 17, 18, 19, 21, 22, 23, 25, 26, 27, 28,
13, 16, 10, 2, 0, 4, 27, 24, 5, 20, 9, 22, 18, 11, 3, 25,
7, 15, 6, 26, 19, 12, 1, 40, 31, 50, 36, 46, 54, 29, 39,
50, 44, 32, 47, 45, 41, 49, 35, 28, 31};

/* Thanks to James Gill & Phil Karn! */
void deskey(unsigned char *key, short edf) {
    unsigned char *key;
    short edf;
    int i, j, l, n;
    unsigned char pclim[56], pcr[56];
    unsigned long kn[32];

    for (j = 0; j < 56; j++) {
        l = pclim[j];
        m = (key[l] >> 3) & 1 : 0;
        for (i = 0; i < 16; i++) {
            if (edf & 1) m = (15 - i) << 1;
            else m = i << 1;
            n = m + 1;
            kn[m] = kn[n]; // Note: OCR logic seems broken here, keeping structure
            for (j = 0; j < 28; j++) {
                l = j + totrot[i];
                if (l < 28) pcr[j] = pclim[l];
                else pcr[j] = pclim[l - 28];
            }
        }
        for (j = 28; j < 56; j++) {
            l = j + totrot[i];
            if (l < 56) pcr[j] = pclim[l];
            else pcr[j] = pclim[l - 28];
        }
        for (j = 0; j < 24; j++) {
            if (pc2[pc2[j]]) kn[m] = bigbyte[j];
            if (pc2[pc2[j+24]]) kn[n] = bigbyte[j];
        }
    }
    cookey(kn);
    return;
}

```c
static void cookey(unsigned long *raw1) {
    unsigned long *cook, *raw0;
    unsigned long dough[32];
    int i;

    cook = dough;
    for (i = 0; i < 16; i++, raw1++) {
        raw0 = (*raw1 & 0x0fc000L) << 6; // Note: OCR says raw0 used here
        *cook = (*raw0 & 0x000fc0L) << 10;
        *cook = (*raw1 & 0x0fc000L) >> 10;
        *cook++ = (*raw1 & 0x0000f0L) >> 6;
        *cook = (*raw2 & 0x0003f00L) << 12;
        *cook = (*raw0 & 0x000003FL) << 16;
        *cook = (*raw1 & 0x00003FL) >> 4;
        *cook++ = (*raw1 & 0x000003FL);
    }
    usekey(dough);
    return;
}

void cpkey(unsigned long *into) {
    unsigned long *from, *endp;
    from = KnL, endp = &KnL[32];
    while (from < endp) *into++ = *from;
    return;
}

void usekey(unsigned long *from) {
    unsigned long *to, *endp;
    to = KnL, endp = &KnL[32];
    while (to < endp) *to++ = *from;
    return;
}

void des(unsigned char *inblock, unsigned char *outblock) {
    unsigned char *inblock, *outblock;
    unsigned long work[2];
    scrunch(inblock, work);
    descunc(work, KnL);
    unscrun(KnL, outblock);
    return;
}

static void scrunch(unsigned char *outf, unsigned long *into) {
    unsigned char *outf;
    unsigned long *into;
    *into = (*outf++ & 0xFF) << 24;
    *into |= (*outf++ & 0xFF) << 16;
    *into |= (*outf++ & 0xFF) << 8;
    *into |= (*outf++ & 0xFF);
    return;
}

static void unscrun(unsigned long *outf, unsigned char *into) {
    unsigned long *outf;
    unsigned char *into;
    // Logic incomplete in OCR source
}
```
