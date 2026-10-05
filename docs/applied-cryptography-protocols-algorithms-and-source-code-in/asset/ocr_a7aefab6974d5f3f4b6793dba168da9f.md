# BLOWFISH

# 653

```
c->S[3][i] = ks3[i];

j = 0;
for (i = 0; i < N + 2; ++i) {
    data = 0x00000000;
    for (k = 0; k < 4; ++k) {
        data = (data << 8) | key[j];
        j = j + 1;
        if (j >= keybytes) {
            j = 0;
        }
    }
}
c->P[i] = c->P[i] ^ data;

datal = 0x00000000;
ddatar = 0x00000000;

for (i = 0; i < N + 2; ++i) {
    Blowfish_encipher(c, &datal, &datar);
    c->P[i] = datal;
    c->P[i + 1] = datar;
}

for (i = 0; i < 4; ++i) {
    for (j = 0; j < 256; j += 2) {
        Blowfish_encipher(c, &datal, &datar);
        c->S[i][j] = datal;
        c->S[i][j + 1] = datar;
    }
}
```

```
void blf_key(blf_ctx *c, char *key, int len) {
    InitializeBlowfish(c, k, len);
}
```

```
void blf_encipher(blf_ctx *c, unsigned long *data, int blocks) {
    unsigned long *d;
    int i;

dd = data;
    for (i = 0; i < blocks; i++) {
        Blowfish_encipher(c, d, d + 1);
        d += 2;
    }
}
```

```
void blf_decipher(blf_ctx *c, unsigned long *data, int blocks) {
    unsigned long *d;
    int i;
```