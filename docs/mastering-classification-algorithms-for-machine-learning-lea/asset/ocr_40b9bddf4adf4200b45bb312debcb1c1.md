# Singular Value Decomposition

$u2 = \left[egin{matrix} 1 & 0 \ 1 & -1 \end{matrix}\right] \left[egin{matrix} -1/\sqrt{2} \ 0 \ -1/\sqrt{2} \end{matrix}\right] /\sqrt{2} = \left[egin{matrix} -1 \ 0 \end{matrix}ightright]$

So, we get

$U = \left[egin{matrix} 0 & -1 \ 1 & 0 \end{matrix}\right]$

Let us verify if $A = U\Sigma V^T$

$U\Sigma V^T = \left[egin{matrix} 0 & -1 \ 1 & 0 \end{matrix}\right] \left[egin{matrix} 1/\sqrt{3} & 0 & 0 \ -1/\sqrt{2} & -1/\sqrt{3} & 0 \ 1/\sqrt{6} & 2/\sqrt{6} & 1/\sqrt{6} \end{matrix}\right] =$

$\left[egin{matrix} 0 & -\sqrt{2} & 0 \ \sqrt{3} & 0 & 0 \end{matrix}\right] \left[egin{matrix} 1/\sqrt{3} & 1/\sqrt{3} & 1/\sqrt{3} \ -1/\sqrt{2} & 0 & 1/\sqrt{2} \ 1/\sqrt{6} & 2/\sqrt{6} & 1/\sqrt{6} \end{matrix}\right] \left[egin{matrix} 1 & 0 & -1 \ -1 & -1 & 1 \end{matrix}\right] = A$

Now, let us reduce the dimensions of matrix A. If $A = UDVT$, we would have reduced the dimension by 1. Let us check this out:

# Singular Value Decomposition

![](bbox=[0.303, 0.653, 0.696, 0.763])

Figure Annexure 3.1: Singular Value Decomposition (SVD)

Now, we know that D is a $2 * 2$ matrix, we keep two columns in U and 2 rows in V. We get:

$U_2DV_2^T = \left[egin{matrix} 0 & -1 \ 1 & 0 \end{matrix}\right] \left[egin{matrix} 1/\sqrt{3} & -1/\sqrt{3} & 1/\sqrt{3} \ -1/\sqrt{2} & 0 & 1/\sqrt{2} \end{matrix}\right] =$