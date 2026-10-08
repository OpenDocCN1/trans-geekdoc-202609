# Enhancing Multicriteria Decision-Making

Converting the cipher text $c^* = 30$ into a trapezoidal fuzzy number $< 10, 20, 30, 40>$. For $x$, choose between $(10,40)$, Let $x = 38$.

```
$\mu_m(38) = \frac{\frac{d-x}{d-c}}{\frac{40-38}{40-30}} = 0.2$
```

Now the cipher text is $(10,20,0.2,40)$; Key = 38; Range = 10

+   (a) First-level decryption

```
$\mu_m(38) = \frac{Encrypted fuzzy number \times Range}{d-c^*}$
$
mu_m(38) = \frac{0.2 \times 10}{d-c} \text{ where } d-c^* = range$

$40 - c^* = 10$
```

+   (b) Second-level decryption

```
$m_{17} = \frac{30^1(mod \ 17) + 15}{3} = 9.3$
$m_{19} = \frac{30^1(mod \ 19) + 15}{3} = 8.6, m_{23} = \frac{30^1(mod \ 23) + 15}{3} = 7.3$
$m_{29} = \frac{30^1(mod \ 29) + 15}{3} = 5.3, m_{31} = \frac{30^1(mod \ 31) + 15}{3} = 15$
$m_{27} = \frac{30^1(mod \ 37) + 15}{3} = 15$
$
$:. m = m_{31} = m_{37} = \dots = 15$
```

Hence the original message is found as 15

# 17.4 APPLICATIONS

In the realm of MCDM, the RSA cryptosystem finds application primarily in sensitive data and communication channels within decision-making processes that involve multiple stakeholders, criteria, and sensitive information. MCDM often involves the exchange of critical and confidential information among multiple parties. RSA encryption can be employed to secure these communications, ensuring that the criteria, evaluations, and decisions remain confidential and protected from unauthorized access or interception.