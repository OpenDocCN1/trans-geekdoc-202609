# Source Code

```
d = x & 0x0FF;
x >>= 8;
c = x & 0x0FF;
x >>= 8;
b = x & 0x0FF;
x >>= 8;
a = x & 0x0FF;
//y = (S[0][a] + S[1][b]) * S[2][c] + S[3][d];
y = bc-S[0][a] + bc-S[1][b];
y = y + bc-S[2][c];
y = y + bc-S[3][d];

return y;
```

```
void Blowfish_encipher(blf_ctx *c, unsigned long *x1, unsigned long *xr)
{
unsigned long X1;
unsigned long XR;
unsigned long temp;
short
    i;

X1 = *x1;
XR = *xr;

for (i = 0; i < N; ++i++) {
    X1 = X1 ^ c->P[i];
    XR = F(c,X1) ^ XR;

    temp = X1;
    X1 = XR;
    XR = temp;
}

temp = X1;
X1 = XR;
XR = temp;

XR = XR ^ c->P[N];
X1 = X1 ^ c->P[N + 1];

*x1 = X1;
*xr = XR;
}
```

```
void Blowfish_decipher(blf_ctx *c, unsigned long *x1, unsigned long *xr)
{
unsigned long X1;
unsigned long XR;
unsigned long temp;
short
    i;

X1 = *x1;
XR = *xr;
```