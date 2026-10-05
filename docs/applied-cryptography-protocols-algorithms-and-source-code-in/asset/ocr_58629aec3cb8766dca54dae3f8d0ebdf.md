# 14 CHAPTER Foundations

The simple-XOR algorithm is really an embarrassment, it's nothing more than a Vigenère polyalphabetic cipher. It's here only because of its prevalence in commercial software packages, at least in the MS-DOS and Macintosh worlds [1502,1387]. Unfortunately, if a software security program claims that it has a "proprietary" encryption algorithm—significantly faster than DES—the odds that it is some variant of it.

```
* Usage: crypto key input_file output_file */
void main( int argc, char *argv[]) {
    FILE *fi, *fo;
    char *cp;
    int c;
    if ((cp = argv[1]) && *cp!='\0') {
        if ((fi = fopen(argv[2], "rb")) != NULL) {
            if ((fo = fopen(argv[3], "wb")) != NULL) {
                while ((c = getc(fi)) != EOF) {
                    c ^= *cp;
                    cp++;
                }
                putc(c,fo);
                fclose(fo);
            }
            fclose(fi);
        }
    }
}
```

This is a symmetric algorithm. The plaintext is XOREd with a keyword to generate the ciphertext. Since XORing the same value restores the original, encryption and decryption use exactly the same program:

P @ K = C
C @ K = P

There's no real security here. This kind of encryption is trivial to break, without computers [587,1475]. It will take a few seconds with a computer. Assume the plaintext is English. Furthermore, assume the key length is any small number of bytes. Here's how to break it:

+   1. Discover the length of the key by a procedure known as counting coincidences [577]. XOR the ciphertext against it-shifted various numbers of bytes, and count those bytes that are equal. If the displacement is a multiple of the key length, then something over 6 percent of the bytes will be equal. If it is not, then less than 0.4 percent will be equal (assuming a random key encrypting normal ASCII text; other plaintext will have different numbers). This is the index of coincidence. The smallest displacement that indicates a multiple of the key length is the length of the key.