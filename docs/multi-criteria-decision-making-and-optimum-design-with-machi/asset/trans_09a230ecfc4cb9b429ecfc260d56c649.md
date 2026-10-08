

# 机器学习树枝图 (Twig Graphs)

## 证明

对于 $m = s+1$，该定理成立。即：

```
$$(s+1)7(s+1)^3+216(s+1)^2+2192(s+1)-6528 \n 1024$$
```

证明 $HW_{TG}(K_m\bigcirc T_m) =$

现在，令 $m = s+1$。那么。

```
$$HW_{TG}(K_{s+1}\bigcirc T_{s+1}) = HW_{TG}(K_s\bigcirc T_s) + \sum_{s=1}^{m} d(U_{m+s},V_i) + \sum_{s=1}^{m} d(U_{m+s},V_i)^2$$
```

```
$$s(7s^3+216s^2+2192s-6528) + \sum_{s=1}^{m} d(U_{m+s},V_i) + \sum_{s=1}^{m} d(U_{m+s},V_i)^2 s=1,2,3 \n 1024$$
```

```
$$(s+1)7(s+1)^3+216(s+1)^2+2192(s+1)-6528 \n 1024$$
```

因此，对于 $m = s+1$，该定理对于每一个 $m$ 的值都成立。因此，$K_m \bigcirc T_i$ 的超维纳纳指数（hyper-Wiener index）为：

```
$$HW_{TG}(K_m\bigcirc T_m) = m(7m^3+216m^2+2192m-6528) \n 1024$$
```

## 16.4 性能分析

### 16.4.1 $HW_{TG}(K_m \bigcirc P_m \bigcirc K_i)$ 的 C++ 编码

```cpp
// 图 ($K_m\bigcirc(\bigcirc K_m))
#include<iostream.h>
#include<math.h>
#include<conio.h>
void main()
{
  long int i,n,j,z,s=0,t,b,h=0,a=0;
  clrscr();
  cout<<"Enter No. of vertices in a Graph:";
  cin>>n;
  for(i=1;i<3*n;i++,s=0,t=1,b=2)
  {
    cout<<"\"\n"
    <<"\n";
    for(z=2;z<=i;z++)
      cout<<"\"\n--";
    for(j=i+1;j<=3*n;j++)
    {
      if(j<=n)
      {
        s=1;
        cout<<" "<<s<<"\n  a=a+s;
        h=h+s*s;
      }
      if(j>n && j<=2*n+1)
      {
        s=s+1;
        cout<<" "<<s<<"\n  a=a+s;
        h=h+s*s;
      }
      if(j>2*n+1)
      {
        if(i>2*n)
        {
          b=b+1;
          cout<<" "<<b<<"\n    a=a+b;
          h=h+b*b;
        }
        else
        {
          if(s==1)
          {
            t=t+1;
            cout<<" "<<t<<"\n      a=a+t;
            h=h+t*t;
          }
          else
          {
            s=s-1;
            cout<<" "<<s<<"\n      a=a+s;
            h=h+s*s;
          }
        }
      }
    }
    return 0;
  }
  cout<<"\n\nWiemer Index of G \t:"<<a;
  cout<<"\n\nHyper Wiener Index of G is:\t:"<<a+h;
  getch();
}
```

### 16.4.2 HW_TG ($K_\omega\bigcirc T_m$) 的 C++ 编码

```cpp
// Graph (K_\omega\bigcirc T_m)
#include <iostream>
#include <conio.h>
void main(void)
{
    int n,i,j,s=0,a=0,t,b,h=0;
    clrscr();
    cout<<"Enter No. of vertices in a Graph:";
    cin>>n;
    for(i=1;i<4*n;i++,s=0,t=1,b=2)
    {
        for(j=i+1;j<=4*n;j++)
        {
            if(j<=n)
            {
                cout<<" "<<s<<"\n                a=a+s;
                h=h+s*s;
            }
            if(j>n && j<=2*n)
            {
                s=s+1;
                cout<<" "<<s<<"\n                a=a+s;
                h=h+s*s;
            }
            if(j>2*n)
            {
                if(j%2==1) b=b+1;
                cout<<" "<<b<<"\n                a=a+b;
                h=h+b*b;
            }
            else
            {
                if(s==1)
                {
                    if(j%2==1) t=t+1;
                    cout<<" "<<t<<"\n                a=a+t;
                    h=h+t*t;
                }
                else
                {
                    if(j%2==1) s=s-1;
                    cout<<" "<<s<<"\n                a=a+s;
                    h=h+s*s;
                }
            }
        }
    }
    cout<<"\nWiener Index of G \t:"<<a;
    cout<<"\nHyper Wiener Index of G:\t:"<<h;
    getch();
}
```

## 16.5 结论

一旦模型经过训练并得到了满意的评估，就可以用于预测新的、未见图的超维纳纳指数。这种能力在各种应用中都有用，包括化学理论、网络分析、计算生物学、遥控、天文学通信网络。

对维纳纳指数（Wiener index）的估计将涉及对不同数据集的评估。

## 参考文献

- Annamalai, M., and K. Adhim, Graceful Graphs, AIP Proceedings. 256. https://doi.org/10.1023/0076-003
- Dobrynin, A., I. Gutman, and S. Klavzar, The Wiener index of Hexagonal Systems, Acta math. 72 (2002), 247–296. https://doi.org/10.139471531
- Entringer, R. C., Jackson, and D. Snyder, Distance in Graphs, Czechoslovak Math. 26 (1976), 283–296. https://doi.org/10.1109/65.19
- Gutman, I. and B. Furta, Hyper-Wiener index, Monatshefte für Chemie/134 (2003), 975–981. http://dx.org/10.1001/01193a
- Khalifee, M., Houssefi-Azari, and Ali Reza Ashrafi, The hyper-Wiener index of Graph Operations, Computers & Mathematics with 56(5) (2008), 1402–1470. http://doi.org/10.1016/camwa.03
- Meenakshi, A., J. Senbagalar, and A. Kannan, Application of Intuistic Fuzzy Network Using Efficient Domination, Fuzzy Logic Applications in Computer Science and Mathematics (2023a), 213–232. https://doi.org/10.1002/9781394715
- Meenakshi, A., et al., A Comparative Study of Fuzzy Domination and Fuzzy Coloring in an Optimal Approach, Mathematics. 11.18 (2023b), 4019. https://doi.org/10.3390/math118
- Meenakshi, A., et al., Efficient Graph Network Using Total Magic Labeling and Its Applications, Mathematics. 11.19 (2023c), 4132. https://doi.org/10.3390/math11
- Su, Z., Tang, and H. Deng, Extremal Wiener Index of Graphs with Given Number of Vertices of Odd Degree, MATCH Communications in Mathematical and Computer Chemistry. 89.2 (2023), 503–516. https://doi.org/10.46793/match.89
- Wiener, H., Structural Determination of Paraffin Boiling Points, J. Amer. Chem. Soc. 69 (1947), 17–20. http://dx.org/10.1021/ja0
- Xia, X. Y., Zhang, W. Li, and G. Y. Wang, A Novel Rough Algorithm for Fast Adaptive Attribute Reduction in Classification, IEEE Trans. Knowl. Data Eng. 34 (2020), 1231–1242. https://doi.org/10.1109/TKDE.299

## 17 通过加密安全系统增强多准则决策

Meenakshi Annamalai, S. Dhanushiya, O. Mythreyi, and Shivangi Mishra

## 17.1 引言

