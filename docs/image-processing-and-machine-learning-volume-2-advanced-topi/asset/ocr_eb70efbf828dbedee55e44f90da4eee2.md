```
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

Figure 4.7 shows the result of the normalized cross-correlation between image 4.3a and the reference standard 4.3b. In Figure 4.7, the bright points show the pixels of the image where the maximum correlation has been obtained (value of 1), which means that there is a great similarity between those locations of the image and the reference pattern, while the other pixels (less than 1) have little or no correlation (similarity).

# 4.1.4 Correlation Coefficient

The lighting problem is a typical problem that affects the normalized cross-correlation. This problem represents the situation where pixels (less than 1)

![](bbox=[0.361, 0.696, 0.631, 0.879])

FIGURE 4.7
Result of the normalized cross-correlation calculation, considering the one shown in Figure 4.3a as the image and the one shown in Figure 4.3b as the reference image.