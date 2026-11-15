requiring extra steps for negative values, such as taking their two's complement. All of this can be accomplished instead by using the IEEE 754 Floating Point Standard. This is the approach taken by modern CPUs.⁵

As an example, let's add together 0d7.875 and 0d0.1875. In fixed point binary the initial expression is:

```
111.1110.0011+
```

To convert fixed point binary into the IEEE 754 Standard, first convert the values into a 32-bit normalized form.⁶ Note that 111.111 can be written as:

```
1.11111 × 2²
```

Note that 2² is the largest magnitude of 2 that will go 7.875. Note that 0.0011 can be written as:

```
1.1 × 2⁻³
```

2⁻³ is the smallest magnitude of 2 that will go 0.1875.

In binary32, this looks like:

| sign | exponent | fraction (ignoring the implicit leading bit) |
| :--- | :--- | :--- |
| 0 | 10000001 | 111 1100 0000 0000 0000 0000 0000 |
| 0 | 01111100 | 100 0000 0000 0000 0000 0000 0000 |