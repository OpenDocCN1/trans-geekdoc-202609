to have about as many possible values as elements in Z_p* and therefore as many possible values for the shared secret. To ensure the highest security, safe DH parameters should work with a prime p such that (p − 1)/2 is also prime. Such a safe prime guarantees that the group doesn’t have small subgroups that would make DH easier to break. With a safe prime, DH can work with any element in Z_p*, excepting 1 and p − 1; notably, g = 2 makes computations slightly faster. But generating a safe prime p takes more time than generating a totally random one.

For example, the dhparam command of the OpenSSL toolkit generates only safe DH parameters, but the extra checks built into the algorithm result increase the execution time considerably, as Listing 11-1 shows.

```
$ time openssl dhparam 2048
Generating DH parameters, 2048 bit long safe prime, generator 2
This is going to take a long time
--snip--
-----BEGIN DH PARAMETERS-----
MIJBCAKCAQEAoSIbyA9e8e44q7V89rceO8v8d/12svwhIIjG9EPwWrr7FkfYhYkU9
fRNtmi1GCTfxc9EDf+4zw+AbRBc6O0LGsxUoPn0d1/G/YDygp1FSM3Xeswqe a
SD+B7628pWtaCZGKZham7vmiN8azGeYaUcckTk jWceHVIVXe5fvuU7k7+C2wKk
iiyMfM8thZm9W/shiKNV2+SshTD6r3C2/hfu7XdOIa1T6ise83YicU/cRaDmK6
zgbKn3S1CjW1M4M3+m1+VhOUFz/nWTJ1IWAVC+a0LK8upqRgApOgHkVqzP/CgWbW
XAOE8NcQqroJomUSB5e1qfpAyvBWPkwrQWIBAg==
-----END DH PARAMETERS-----
openssl dhparam 2048 7.46s user 0.10s system 99% cpu 7.593 total
```

Listing 11-1: Measuring the execution time of generating 2,048-bit Diffie–Hellman parameters with the OpenSSL toolkit

It took around eight seconds to generate the DH parameters using the OpenSSL toolkit (it's common to observe generation times in the order of 30 seconds or even more than 1 minute).

For the sake of comparison, Listing 11-2 shows how long it takes on the same system to generate RSA parameters of the same size (that is, two prime numbers, p and q, each half the size of the p used for DH).

```
$ time openssl genrsa 2048
Generating RSA private key, 2048 bit long modulus
.......................................+...
.......................................+...
e is 65537 (0x10001)
-----BEGIN RSA PRIVATE KEY-----
--snip--
-----END RSA PRIVATE KEY-----
openssl genrsa 2048 0.16s user 0.01s system 95% cpu 0.171 total
```

Listing 11-2: Generating 2,048-bit RSA parameters while measuring the execution time

Generating DH parameters took about 50 times longer than generating RSA parameters of the same security level, mainly due to the extra constraint imposed on the prime generated to create DH parameters.