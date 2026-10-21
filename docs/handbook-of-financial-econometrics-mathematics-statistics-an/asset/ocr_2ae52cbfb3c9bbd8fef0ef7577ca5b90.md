Again from the property of $G(\cdot,\cdot)$ as given by (109.36), we have

$Q(2z;2v,2k)=g(1,k)G(v,z)+g(2,k)G(v+1,z)+g(3,k)G(v+2,z)+\cdots$
$=g(1,k)[G(v-1,z)+g(v,z)]$
$+g(2,k)[G(v-1,z)+g(v+1,z)]+g(3,k)[G(v-1,z)$
$+g(v,z)+g(v+1,z)+g(v+2,z)]+\cdots$
$=[G(v-1,z)+g(v,z)]\sum_{n=1}^{\infty}g(n,k)+g(v+1,z)$
$\times\sum_{n=2}^{\infty}g(n,k)+g(v+2,z)\sum_{n=3}^{\infty}g(n,k)+\cdots$
$=G(v-1,z)+g(v,z)+g(v+1,z)[1-g(1,k)]$
$+g(v+2,z)[1-g(1,k)-g(2,k)]+\cdots$
$=G(v-1,z)+\sum_{n=0}^{\infty}g(v+n,z)-g(v+1,z)[g(1,k)]$
$-g(v+2,z)[g(1,k)+g(2,k)]+\cdots$
$=1-g(v+1,z)[g(1,k)]-g(v+2,z)[g(1,k)+g(2,k)]-\cdots.$

We conclude that

$Q(2z;2v,2k)=1-\sum_{n=1}^{\infty}g(n+v,z)\sum_{i=1}^{n}g(i,k). \tag{109.39}$

From (109.35) and (109.39) we observe that

$\int_{y}^{\infty}P(2z;2v,2k)dk=1-Q(2z;2(v-1),2y). \tag{109.40}$

Thus, we can write $C_2$ as

$C_2=Ke^{-r\tau}\int_{y}^{\infty}P\left(2x;2+\frac{2}{2-\beta},2w\right)dw$

$=Ke^{-r\tau}Q\left(2y;2-\frac{2}{2-\beta},2x\right)$

$=Ke^{-r\tau}\left(1-Q\left(2x;\frac{2}{2-\beta},2y\right)\right). \tag{109.41}$

From (109.41) we immediately obtain

$Q\left(2y;2-\frac{2}{2-\beta},2x\right)+Q\left(2x;\frac{2}{2-\beta},2y\right)=1, \tag{109.42}$