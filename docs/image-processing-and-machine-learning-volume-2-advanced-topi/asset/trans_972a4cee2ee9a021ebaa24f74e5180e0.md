

与公式 4.5 相比，公式 4.7 的表述展示了参考图像 R(i,j) 与其对应的图像区块 I(x,y) 之间绝对距离的局部距离度量的表征。但是，需要指出的是，图像整体照度的增加会导致 C_N(r,s) 的值产生非常大的变化。

## 4.1.3.1 归一化互相关的实现

本节展示了如何在图像与参考图像之间实现公式 4.7 中定义的归一化互相关。程序 4.5 展示了如何计算通用归一化互相关。

```
PROGRAM 4.5 DETERMINATION OF THE NORMALIZED
CROSS-CORRELATION DEFINED IN EQUATION 4.7
BETWEEN AN IMAGE AND A REFERENCE PATTERN
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Program that allows calculating the normalized
% cross-correlation between I(x,y) and R(i,j)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Get the dimension of the image
[m n]=size(Im);
% Convert to double to avoid numerical problems
Imd=double(Im) ;
Td=double(T) ;
% Get the size of the reference image
[mt nt]=size(T) ;
%Variable sum is initialized to zero
suma=0;
suma1=0;
%The matrixes C(r,s) y A(r,s) of Eq. 4.4 are obtained
for re=1:m-mt
for co=1:n-nt
indice=0;
for rel=0:mt-1
for col=0:nt-1
suma=Imd(re+rel,co+col)*Td(rel,col)+suma;
suma1=Imd(re+rel,co+col)*Imd(re+rel,co+col)+suma1;
end
end
C(re,co)=2*suma;
A(re,co)=suma1;
suma=0;
suma1=0;
end
end
sum=0;
% The matrix B of Eq. 4.4 is obtained
for rel=0:mt-1
    for col=0:nt-1
sum=Td(rel+1,col+1)*Td(rel+1,col+1)+sum;
    end
end
% The normalized cross-correlation is obtained
%according to the Eq. 4.7
for re=1:m-mt
    for co=1:n-nt

Cn(re,co)=C(re,co)/((sqrt(A(re,co)))*sqrt(sum));
    end
end
imshow(Cn)
```

图 4.7 展示了图像 4.3a 与参考图样 4.3b 之间的归一化互相关结果。在图 4.7 中，亮点显示了图像中获得最大相关性（值为 1）的像素，这意味着图像的这些位置与参考图样之间存在很大的相似性，而其他像素（小于 1）则几乎没有或没有相关性（相似性）。

![](img/fa2d7e8bd88af7122f764c748b0a3723_163_0.png)

FIGURE 4.7
归一化互相关计算结果，将图 4.3a 中显示的作为图像，将图 4.3b 中显示的作为参考图像。

## 4.1.4 相关系数

由于照明条件，具有很少或没有相关性或相似性。避免此问题的一种可能性是考虑这些像素值与其平均值的局部差异，而不仅仅是像素的强度值 [5]。因此，公式 4.7 改写如下：

$$ C_L(r, s) = \frac{ \sum_{(i,j) \in R} \left( I(r+i, s+j) - \bar{I}(r, s) \right) \cdot \left( R(i, j) - \bar{R} \right) }{ \left[ \sum_{(i,j) \in R} \left( I(r+i, s+j) - \bar{I}(r, s) \right)^2 \right]^{1/2} \cdot \left[ \sum_{(i,j) \in R} \left( R(i, j) - \bar{R} \right)^2 \right]^{1/2} } $$

其中 \(\bar{I}(r, s)\) 和 \(\bar{R}\) 定义如下：

$$ \bar{I}(r, s) = \frac{1}{N} \sum_{(i,j) \in R} I(r+i, s+j) \qquad \bar{R} = \frac{1}{N} \sum_{(i,j) \in R} R(i, j) $$

其中 N 对应于参考图像 R(i, j) 中的元素数量。在统计学领域，公式 4.8 称为相关系数。相关系数不能被视为评估一般数据集的全局相关指数，而应视为仅考虑由参考图像大小明确确定的区域的局部因子。相关系数波动的值范围是 [-1,1]，其中值 1 表示最高相似度指数，而 -1 表示 I(x, y) 和 R(i, j) 完全不同。

公式 4.8 的分母包含以下表达式：

$$ \sigma_R^2 = \sum_{(i,j) \in R} (R(i, j) - \bar{R})^2 = \sum_{(i,j) \in R} (R(i, j))^2 - N \cdot \bar{R}^2 $$

公式 4.10 对应于图样 R(i, j) 的方差。该值在 C_L(r, s) 值的处理中是恒定的，因此只需计算一次。通过在公式 4.8 中替换此因子，该表达式将改写如下：

$$ C_L(r, s) = \frac{ \sum_{(i,j) \in R} \left( I(r+i, s+j) \cdot R(i, j) \right) - N \cdot \bar{I}(r, s) \cdot \bar{R} }{ \left[ \sum_{(i,j) \in R} \left( I(r+i, s+j) \right)^2 - N \cdot \left( \bar{I}(r, s) \right)^2 \right]^{1/2} \cdot \sigma_R } $$

前一个表达式是计算局部相关系数最有效的方法。其效率源于 \(\bar{R}\) 和 \(\sigma_R\) 只需计算一次，而 \(\bar{I}(r,s)\) 的值不再参与图像区块每个像素的处理，而是现在仅考虑一次。

基于公式 4.11 计算的相关系数对应于图像的局部测量指标，与公式 4.5 中显示的线性相关相反。由于它是一个局部指标，因此无法在频域中建立计算相同指标的方法，因为频谱技术制定的是全局特征的计算。

## 4.1.4.1 相关系数的实现

本节展示了如何在图像与参考图样之间实现公式 4.11 中定义的相关系数。程序 4.6 展示了如何计算相关系数。

```
PROGRAM 4.6 CALCULATION OF THE CORRELATION COEFFICIENT DEFINED IN EQUATION 4.8 BETWEEN AN IMAGE AND A REFERENCE PATTERN
%%%%%%%%%%%%%%
% Program that allows calculating the coefficient of
%correlation between I(x,y) and R(i,j)
%%%%%%%%%%%%%%
% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%
% Get the dimension of the image
[m n]=size(Im);
% Convert to double to avoid numerical problems
Imd=double(Im);
Td=double(T);
%Get the size of the reference image
[mt nt]=size(T);
%Variables sum are initialized to zero
suma1=0;
suma2=0;
suma3=0;
% The mean of the reference image is calculated
MT=mean(mean(Td));
for re=1:m-mt
for co=1:n-nt
for rel=0:mt-1
for col=0:nt-1
    Itemp(rel+1,col+1)=Imd(re+rel,co+col);
    end
end
% The average of the corresponding image is
% calculated
MI=mean(mean(Itemp));
for rel=0:mt-1
    for col=0:nt-1
suma1=(Itemp(rel+1,col+1)-MI)*(Td(rel+1,col+1)-MT)+suma1;
suma2=((Itemp(rel+1,col+1)-MI)^2)+suma2;
suma3=((Td(rel+1,col+1)-MT)^2)+suma3;
    end
end
% The correlation coefficient is calculated
% according to 4.8
CL(re,co)=suma1/((sqrt(suma2)*sqrt(suma3))+eps);
% Accumulation variables are reset
suma1=0;
suma2=0;
suma3=0;
end
end
%The elements of CL are transformed within the interval
[0,1]
CLN=mat2gray(CL);
imshow(CLN)
```

图 4.8 展示了图像 4.3a 与参考图样 4.3b 之间的归一化互相关结果。在图 4.8 中，亮点显示了图像中获得最大相关性（值为 1）的像素，这意味着图像的这些区域与参考图样之间存在很大的相似性，而暗像素（值接近 -1）则几乎没有或没有相关性或相似性。

图 4.9 展示了先前讨论的每个模型的曲面，这些模型用于衡量图像与其包含的参考图样之间的相似性。在曲面上，峰值表示图像与图样非常相似的点或区域。

从图 4.9 所示的曲面中可以得出一些重要结论。在图 4.9a 中，它展示了作为全局相关产物得到的曲面，显示了尽管图像与图样具有最大相似性的点清晰可辨，但它有一个

