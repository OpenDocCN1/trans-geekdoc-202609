

# 658
# 源代码

```c
void printvec(char *chrs, word32 *d) {
    printf("%20s %08x %08x %08x \n", chrs,d[2],d[1],d[0]);
}

main() {
    twy_ctx gc;
    word32 a[9],k[3];
    int i;

    /* 测试向量 1. */
    k[0]=k[1]=k[2]=0;
    a[0]=a[1]=a[2]=1;
    twy_key(&gc,k);

    printf("************\n\n    printvec("KEY = %s",k);
    printvec("PLAIN = %s",a);
    encrypt(&gc,a);
    printvec("CIPHER = %s",a);

    /* 测试向量 2. */
    k[0]=0xcdef012;k[1]=0x456789ab;k[2]=0xdef01234;
    a[0]=0x1234567;a[1]=0x9abcdef0;a[2]=0x23456789;
    twy_key(&gc,k);

    printf("************\n\n    printvec("KEY = %s",k);
    printvec("PLAIN = %s",a);
    encrypt(&gc,a);
    printvec("CIPHER = %s",a);

    /* 测试向量 3. */
    k[0]=0xcab920dc;k[1]=0xd6144138;k[2]=0xd2f05b5e;
    a[0]=0xad21ec7;a[1]=0x83ae9dc4;a[2]=0x40597c6e;
    twy_key(&gc,k);

    printf("************\n");
printvec("KEY = %s",k);
printvec("PLAIN = %s",a);ncrypt(&gc,a);
printvec("CIPHER = %s",a");
```

```c
/* 测试值

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

```c
/* 加/解密测试：*
for(i=0;i<9;i++) a[i]=a[i];
twy_enc(&gc,a,3);
for(i=0;i<9;i++) printf("Block %01d encrypts to 0x%8x 0x%8x 0x%8x\n", i/3,a[i],a[i+1],a[i+2]);

twy_dec(&gc,a,2);
twy_dec(&gc,a,6,1);

for(i=0;i<9;i+=3) printf("Block %01d decrypts to 0x%8x 0x%8x 0x%8x\n", i/3,a[i],a[i+1],a[i+2]);
```

# RC5

```c
#include <stdio.h>
```

```c
/* 一个 RC5 上文需要知道轮数以及它的子密钥。 */
typedef struct {
 u4 *xk;
 int nr;
} rc5_ctx;
```

```c
/* 在可能的情况下，在 C++ 中这些应该被替换为实际指令。
对于 Turbo，这是通过 _lrot 和 _rrot 实现的。 */
#define ROT32(X,C) (((X)<<(C))|((X)>>(32-(C))))
#define ROT32_RIGHT(X,C) (((X)>>(C))|((X)<<(32-(C))))
```

# 源代码

```c
/* 处理 RC5 基本操作的函数原型。 */
void rc5_init(rc5_ctx *, int);
void rc5_destroy(rc5_ctx *);
void rc5_key(rc5_ctx *, u4 *, int);
void rc5_encrypt(rc5_ctx *, u4 *, int);
void rc5_decrypt(rc5_ctx *, u4 *, int);
```

```c
/* RC5 的函数实现。 */
/* 擦除敏感值。 */
void rc5_destroy(rc5_ctx *c) {
  int i;
  for(i=0;i<c->nr;i++) c->xk[i]=0;
  free(c->xk);
}
```

```c
/* 为 rc5 的上文等内容分配内存。 */
void rc5_init(rc5_ctx *c, int rounds) {
  c->n = rounds;
  c->xk = (u4 *) malloc(rounds*2);
}
```

```c
void rc5_encrypt(rc5_ctx *c, u4 *data, int blocks) {
  u4 *d, *sk;
  int h, rc;

  data = data;
  sk = (c->xk)+2;
  for(h=0;h<blocks;h++)
    d[0] ^= c->xk[0];
    d[1] += c->xk[1];
    for(i=0;i<c->nr;i+=2)
      d[0] ^= d[1];
      rc = d[0] & 3;
      d[0] = ROT32(d[0],rc);
      d[0] += sk[i];

    d[1] ^= d[0];
    rc = d[1] & 3;
    d[1] = ROT32(d[1],rc);
    d[1] += sk[i];

    printf("Round %03d : %08x %08x %08x\n", i/2,d[0],d[1],sk[i+1]);
}
void rc5_decrypt(rc5_ctx *c, u4 *data, int blocks) {
  u4 *d, *sk;
  int h, i, rc;

  data = data;
  sk = (c->xk)+2;
  for(h=0;h<blocks;h++)
    for(i=(c->nr)*2-2;i>=0;i-=2)
    d[1] = --sk[i+1];
    rc = d[1] & 3;
    d[1] = ROTR32(d[1],rc);
    d[1] ^= d[0];

    d[0] = --sk[i];
    rc = d[0] & 3;
    d[0] = ROTR32(d[0],rc);
    d[0] ^= d[1];
    d[0] = --c->xk[i];
    d[1] = --c->xk[i];

    d+=2;
}
```

```c
void rc5_key(rc5_ctx *c, u4 *key, int keylen) {
  u4 *pk, A, B; // 填充密钥
  int xk_len, pk_len, i, num_steps, rc;
  ul *cp;

  xk_len = c->nr*2 + 2;
  pk_len = keylen/4;
  if(keylen%4!=0)pk_len += 1;

  pk = (u4 *) malloc(pk_len * 4);
  if(pk==NULL) {
    printf("发生错误!\n");
    exit(-1);
  }

  /* 初始化 pk -- 这在 Intel 机器上应该工作.... */
  for(i=0;i<pk_len;i++) pk[i]=0;
  cp = (ul *)pk;
  for(i=0;i<xk_len;i++) cp[i]=key[i];

  /* 初始化 xk. */
  c->xk[0] = 0x7be15163; P32 */
  for(i=1;i<xk_len;i++) c->xk[i] = 0x9e377b9; /* Q32 */

  /* 测试 */
  A = B = 0;
  for(i=0;i<xk_len;i++) {
    A = A + c->xk[i];
    B = B ^ c->xk[i];
  }

  /* 将密钥扩展到 xt. */
  if(pk_len>0)num_steps=3*pk_len;else num_steps=3*xk_len;

  A = B = 0;
  for(i=0;i<num_steps;i++) {
    A = c->xk[xk_len] = ROT32(c->xk[xk_len]) + A + B, 3;
    rc = (A+B) & 3;
    B = pk[i_len] = ROT32(pk[i_len]) + A + B,rc/* 在释放内存前销毁敏感数据。 */
  for(i=0;i<pk_len;i++) pk[i]=0;
  free(pk);
}

void main(void){
  rc5_ctx c;
  u4 data[8];
  char key[] = "ABC";
  int i;
  for(i=0;i<8;i++) data[i] = i;
  rc5_init(&c,10); /* 10 轮 */
  rc5_key(&c,key,5);
  rc5_encrypt(&c,data,4);
  printf("Encryptions:\n");
  for(i=0;i<8;i++) printf("Block %01d = %08x %08x\n", i/2,data[i],data[i+1]);
  rc5_decrypt(&c,data,2);
  rc5_decrypt(&c,data+4,2);
  printf("Decryptions:\n");
  for(i=0;i<8;i++) printf("Block %01d = %08x %08x\n", i/2,data[i],data[i+1]);
}
```

# A5

typedef struct {
  unsigned long r1, r2, r3;
} rc5_ctx;

static int threshold(unsigned int r1, unsigned int r2, unsigned int r3) {
  unsigned int r1, r2, r3, total;
  total = ((r1 >> 9) & 1) + ((r2 >> 11) & 1) + ((r3 >> 11) & 1);
  if (total > 1)
    return (0);
  else
    return (1);
}

unsigned long clock_r1(int ctl, unsigned long r1) {
  int ctl;
  unsigned long r1, feedback;

  ctl ^= ((r1 >> 9) & 1);
  if (ctl) {
    feedback = (r1 << 18) ^ (r1 >> 17) ^ (r1 << 16) ^ (r1 >> 13);
    r1 = (r1 << 1) & 0xffff;
    if (feedback & 0x1) {
      r1 ^= 0x1;
    }
  }
  return (r1);
}

unsigned long clock_r2(int ctl, unsigned long r2) {
  int ctl;
  unsigned long r2, feedback;

  ctl ^= ((r2 >> 11) & 1;
  if (ctl) {
    feedback = (r2 << 21) ^ (r2 >> 20) ^ (r2 >> 16) ^ (r2 >> 12);
    r2 = (r2 << 1) & 0x3ffff;
    if (feedback & 0x1) {
      r2 ^= 0x1;
    }
  }
  return (r2);
}

unsigned long clock_r3(int ctl, unsigned long r3) {
  int ctl;
  unsigned long r3, feedback;

  ctl ^= ((r3 >> 11) & 1);
  if (ctl) {
    feedback = (r3 >> 22) ^ (r3 >> 21) ^ (r3 >> 18) ^ (r3 >> 17);
    r3 = (r3 << 1) & 0x7ffff;
    if (feedback & 0x1) {
      r3 ^= 0x1;
    }
  }
  return (r3);
}
```

# 源代码

```c
int keystream(key, frame, alice, bob)
  unsigned char *key;               /* 64 位会话密钥 */
  unsigned long frame;            /* 22 位帧号 */
  unsigned char *alice;            /* 114 位 Alice 到 Bob 的密钥 */
  unsigned char *bob;              /* 114 位 Bob 到 Alice 的密钥 */
{
  unsigned long r1;               /* 19 位移寄存器 */
  unsigned long r2;               /* 22 位移寄存器 */
  unsigned long r3;               /* 23 位移寄存器 */
  int i;                           /* 循环计数 */
  int clock_ctl;                   /* 与移寄存器时钟允许异或 */
  unsigned char *ptr;              /* 密钥流当前位置 */
  unsigned char *byte;             /* 正在组装的字节 */
  unsigned int bits;               /* 字节中的密钥位数 */
  unsigned int bit;                /* 来自密钥生成器的位 */

  /* 从会话密钥初始化移寄存器 */
  r1 = (key[0] | (key[1] << 8) | (key[2] << 16) & 0xffffffff;
  r2 = ((key[2] >> 3) | (key[3] << 5) | (key[4] << 13) | (key[5] << 21)) & 0x3ffffff;
  r3 = ((key[5] >> 5) | (key[6] << 7) | (key[7] << 15)) & 0x7ffff;

  /* 将帧号异或到移寄存器状态中，将其异或到反馈路径 */
  for (i=0;i<22;i++) {
    clock_ctl = threshold(r1, r2, r2);
    r1 = clock_r1(clock_ctl, r1);
    r2 = clock_r2(clock_ctl, r2);
    r3 = clock_r3(clock_ctl, r3);
    if (frame & 1) {
      r1 &= 1;
      r2 &= 1;
      r3 &= 1;
    }
    frame = frame >> 1;
  }

  /* 让移寄存器运行 100 个时钟周期，允许帧号扩散到移寄存器的的所有位中 */
  for (i=0;i<100;i++) {
    clock_ctl = threshold(r1, r2, r2);
    r1 = clock_r1(clock_ctl, r1);
    r2 = clock_r2(clock_ctl, r2);
    r3 = clock_r3(clock_ctl, r3);
  }

  /* 生成 114 位 Alice->bob 密钥流 */
}
```

