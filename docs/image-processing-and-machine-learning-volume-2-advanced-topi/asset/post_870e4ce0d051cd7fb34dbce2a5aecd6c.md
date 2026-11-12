

% Get the dimension of the image
[m n] = size(Im);
% Convert to double to avoid numerical problems
Imd = double(Im);
Td = double(T);
% Get the size of the reference image
[mt nt] = size(T);
% A matrix is defined that collects the results of the
% differences
Itemp = zeros(size(T));
% The distances between I(x,y) and R(i,j)
% are obtained according to 4.2
for re = 1:m-mt
    for co = 1:n-nt
        indice = 0;
        for rel = 0:mt-1
            for col = 0:nt-1
                Itemp(rel+1, col+1) = abs(Imd(re+rel, co+col) - Td(rel+1, col+1));
            end
        end
        dm(re, co) = max(max(Itemp));
    end
end

Figure 4.5a shows the result of the determination of the distance of the maximum of the differences between an image and a reference pattern (Figure 4.3a and b, respectively). As can be seen, this image does not suggest that this type of measurement can be used as a similarity index.

![](img/fa2d7e8bd88af7122f764c748b0a3723_157_0.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_157_1.png)

**FIGURE 4.5**
Results of distance calculations between an image and a reference pattern. (a) Distance of the maximum of the differences and (b) distance of the sum of the squared distances.

### 4.1.1.3 Sum of Squared Distances

Program 4.3 shows how to calculate the sum of the squared distances between an image and a reference pattern.

In Figure 4.5b, the dark points show the pixels where a small distance between an image and a reference has been obtained (Figure 4.3a and b, respectively), which means that there is a high resemblance between those regions of the image and the reference pattern.

## 4.1.2 Distance and Correlation

The Euclidean distance defined in Equation 4.3 is especially important because of its statistical properties. To find the maximum coincidence between the reference image R(i,j) and the image I(x,y), it is enough to minimize the square of \(d^2_E\), which is defined as positive. \(d^2_E\) can be described as follows:

```
PROGRAM 4.3 CALCULATION OF THE DISTANCE
OF THE SUM OF THE QUADRATIC DISTANCES
BETWEEN AN IMAGE AND A REFERENCE PATTERN
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Program to calculate the distance of the sum
% of squared distances between I(x,y) and R(i,j)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Get the dimension of the image
[m n] = size(Im);
% Convert to double to avoid numerical problems
Imd = double(Im);
Td = double(T);
% Get the size of the reference image
[mt nt] = size(T);
% Variable sum is initialized to zero
suma = 0;
% The distances between I(x,y) and R(i,j)
% are obtained according to 4.3
for re = 1:m-mt
    for co = 1:n-nt
        indice = 0;
        for re1 = 0:mt-1
            for col = 0:nt-1
                suma = (Imd(re+re1, co+col) - Td(re1+1, col+1))^2 + suma;
            end
        end
        de(re, co) = sqrt(suma);
        suma = 0;
    end
end
```

\( d_E^2(r,s) = \sum_{(i,j)\in R} \left( I(r+i, s+j) - R(i,j) \right)^2 \)

\( = \underbrace{\sum_{(i,j)\in R} (I(r+i, s+j))^2}_{A(r,s)} + \underbrace{\sum_{(i,j)\in R} (R(i,j))^2}_{B} - \underbrace{2 \sum_{(i,j)\in R} I(r+i, s+j) \cdot R(i,j)}_{C(r,s)} \) (4.4)

The part B in Equation 4.4 represents the sum squared of all values of the reference image \( R(i, j) \). Since these values do not depend on the offset \( (r, s) \), this factor is constant throughout the processing of Equation 4.4. Therefore, \( B \) could be ignored for the evaluation. The expression \( A(r, s) \) represents the sum of the values of the image pixels corresponding to the squared \( R(i, j) \). The value \( A(r, s) \) clearly depends on the offset \( (r, s) \). \( C(r, s) \) corresponds to the so-called cross-correlation (\( I \otimes R \)) between \( I(x, y) \) and \( R(i, j) \). This cross-correlation is defined as follows:

\( (I \otimes R)(r, s) = \sum_{i=-\infty}^{\infty} \sum_{j=-\infty}^{\infty} I(r+i, s+j) \cdot R(i, j) \) (4.5)

Since the elements outside the dimensions of images \( I(x, y) \) and \( R(i, j) \) are considered zero, Equation 4.5 can be rewritten as follows:

\( \sum_{i=0}^{a_R-1} \sum_{j=0}^{d_K-1} I(r+i, s+j) \cdot R(i, j) = \sum_{(i,j)\in R} I(r+i, s+j) \cdot R(i, j) \) (4.6)

Correlation is fundamentally the same operation as convolution, except that in convolution, the kernel of the operation is inverted on itself.

If the factor \( A(r, s) \) in Equation 4.4 remains approximately constant throughout the image \( I(x, y) \), it would mean that the energy in the image is uniformly distributed. Thus, the maximum value of the correlation \( C(r, s) \) corresponds to the point of the image \( I(x, y) \) where the reference image \( R(i, j) \) has the maximum coincidence. In this case, the minimum value of \( d_E^2(r, s) \) can only be calculated by means of the maximum value of the \( I \otimes R \) correlation. This fact is very important since, using the Fourier transform, it is highly efficient to calculate the correlation in the frequency domain.

### 4.1.2.1 Implementation of General Correlation

This section shows how to implement the general correlation defined in Equation 4.6 between an image and a reference pattern. The code is shown in Program 4.4.

```
PROGRAM 4.4 CALCULATION OF THE GENERAL CORRELATION DEFINED IN EQUATION 4.6 BETWEEN AN IMAGE AND A REFERENCE PATTERN
********************************************************************************
% Program that allows calculating the general correlation
% between I(x,y) and R(i,j)
********************************************************************************
% Erik Cuevas, Alma Rodriguez
********************************************************************************
% Get the dimension of the image
[m n] = size(Im);
% Convert to double to avoid numerical problems
Imd = double(Im);
Td = double(T);
% Get the size of the reference image
[mt nt] = size(T);
% Variable sum is initialized to zero
suma = 0;
% The distances between I(x,y) and R(i,j)
% are obtained according to 4.6
for re = 1:m-mt
    for co = 1:n-nt
        indice = 0;
        for rel = 0:mt-1
            for col = 0:nt-1
                suma = Imd(re+rel, co+col) * Td(rel+1, col+1) + suma;
            end
        end
        de(re, co) = suma;
        suma = 0;
    end
end
% The elements of de are transformed within the interval [0,1]
C = mat2gray(de);
imshow(C)
```

![](img/fa2d7e8bd88af7122f764c748b0a3723_161_0.png)

**FIGURE 4.6**
Result of the calculation of the global correlation, considering the image shown in Figure 4.3a as the image and the one shown in Figure 4.3b as the reference image.

Figure 4.6 shows the result of the correlation between image 4.3a and reference pattern 4.3b. In Figure 4.6, the dark points show the pixels of the image where small values were obtained, which means, according to Equation 4.6, that there is a great similarity between those locations of the image and the reference pattern.

## 4.1.3 The Normalized Cross-Correlation

In practice, the assumption that _A_ (_r_, _s_) remains approximately constant in the image is not fulfilled. Therefore, the result of the correlation is highly dependent on the intensity changes of the image _I_ (_x_, _y_) [4]. The normalized cross-correlation _C<sub>N</sub>_ (_r_, _s_) compensates for this dependence through the consideration of the total energy of the image. The normalized cross-correlation is defined as follows:

```
\( C_N(r,s) = \frac{C(r,s)}{\sqrt{A(r,s) \cdot B}} = \frac{\sum_{(i,j)\in R} I(r+i,s+j) \cdot R(i,j)}{\left[\sum_{(i,j)\in R} \left(I(r+i,s+j)\right)^2\right]^{1/2} \cdot \left[\sum_{(i,j)\in R} \left(R(i,j)\right)^2\right]^{1/2}} \) (4.7)
```

Since the values of both the image _I_ (_x_, _y_) and the reference _R_ (_i_, _j_) are positive, the resulting values of _C<sub>N</sub>_ (_r_, _s_) are within the interval [0,1]. A value of _C<sub>N</sub>_ (_r_, _s_) = 1 represents a maximum index of similarity between _R_ (_i_, _j_) and the section of the image _I_ (_x_, _y_) with which it corresponds. The value produced by the normalized cross-correlation has the advantage that it can be used as a standard similarity index.

