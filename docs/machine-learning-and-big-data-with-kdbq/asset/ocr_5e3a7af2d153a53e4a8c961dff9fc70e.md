# Fourier Transform 305

The trigonometric form of the complex number is given as:

```
z = r(cos\phi + i\sin\phi). (15.11)
```

We implement the polar decomposition, which returns a dictionary of the radius and the angle:

```
.quantQ.polar:{[cx]
// cx -- complex number
// radial part
r: sqrt cx wsum cx;
// angular part
phi:$[@cx're;@cx'im]%cx're;
0=cx're;@cx'im;\atan[cx'im]%cx're]] + .quantQ.pi;
atan[cx'im]%cx're]] - .quantQ.pi;
0=cx're;$cx'im; .5 * .quantQ.pi;
0=cx'im; -.5 * .quantQ.pi;
0];
'radius angle!(r,phi);
```

Let us calculate a couple of examples:

```
.quantQ.complex.polar[cx1]
```

| radius | 1 |
| angle | 0 |

```
.quantQ.complex.polar[cx2]
```

| radius | 1 |
| angle | 1.570796 |

```
.quantQ.complex.polar[`re`im!@ 0f`]
```

| radius | 0 |
| angle | 0n |

For the sake of completeness, we provide a function which converts the polar coordinates to regular form using the trigonometric form:

```
.quantQ.complex.polar2Canonical:{[polar]
// polar -- complex number in polar coordinates
:re'im![`radius`*(cos;sin)@:polarangle;
```

and verify its functionality:

```
.quantQ.complex.polar2Canonical[`radius`angle!(2;0.25+3.14152)]
```