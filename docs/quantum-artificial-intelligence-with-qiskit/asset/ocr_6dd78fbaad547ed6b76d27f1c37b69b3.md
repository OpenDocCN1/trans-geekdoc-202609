# Quantum Physics and Quantum Computation ■35

It can be expressed as

```
$H_3(000) = H_1|0angle \otimes H_1|0angle \otimes H_1|0angle = \left(\frac{|0|+|1angle}{\sqrt{2}}ight) \cdot \left(\frac{|0|+|1angle}{\sqrt{2}}ight) \cdot \left(\frac{|0|+|1angle}{\sqrt{2}}ight)$
```

and

```
$H_3 \cdot H_3(000) = |000angle$.
```

This is because $H_m = H_m^*$ so that $I_m = H_m \cdot H_m$. The base states $|11angle$ is mapped into

```
$H_2|11angle = H_1|1angle \otimes H_1|1angle = \left(\frac{|0-|1angle}{\sqrt{2}}ight) \cdot \left(\frac{|0-|1angle}{\sqrt{2}}ight)$
```

```
$H_2|11angle = \frac{1}{2}(|00angle - |01angle + |11angle)$.
```

# 2.6.1 Matrix Representation of Serial and Parallel Operations

A serial computation corresponds to a multiplication of matrices that represents the gates. The multiplication of matrices is usually commutative, for example $H_1 \cdot X 
eq XH_1$

```
$\begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \ \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \end{pmatrix} \cdot \begin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix} \neq \begin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix} \cdot \begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \ \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \end{pmatrix}$
```

```
$\begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \ \frac{-1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{pmatrix} \neq \begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \ \frac{-1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{pmatrix}$,
```

it means

```
$H_1 \cdot X |0angle = H_1|1angle = \left(\frac{|0-|1angle}{\sqrt{2}}ight)$
```

and

```
$X \cdot H_1 \cdot |0angle = X \cdot \left(\frac{|0|+|1angle}{\sqrt{2}}ight) = \left(\frac{|1|+|0angle}{\sqrt{2}}ight) 
eq \left(\frac{|0-|1angle}{\sqrt{2}}ight)$
```

and it follows

```
$X \cdot H_1 \cdot |0angle = H_1|0angle$.
```

Only the multiplication with the identity matrix and the inverse matrix is commutative. Parallel operations correspond to the direct product, also called the tensor product or Kronecker product when dealing with matrices. For example with

```
$X \otimes I_1 \otimes H_1 \cdot |000angle = (X|0angle) \otimes (I_1|0angle) \otimes (H_1|0angle) =$
```

```
$|10angle \cdot \left(\frac{|0|+|1angle}{\sqrt{2}}ight) = \left(\frac{|100angle+|101angle}{\sqrt{2}}ight)$
```

in vector representation as

```
$$\left(egin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix}ight) \cdot \left(egin{pmatrix} 1 & 0 \ 0 & 1 \end{pmatrix}ight) \otimes \left(egin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix}ight) \otimes \left(egin{pmatrix} \frac{1}{\sqrt{2}} & \frac{-1}{\sqrt{2}} \ \frac{-1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{pmatrix}ight) \cdot \left(egin{pmatrix} 1 & 0 \ 0 & 1 \end{pmatrix}ight) =$
```