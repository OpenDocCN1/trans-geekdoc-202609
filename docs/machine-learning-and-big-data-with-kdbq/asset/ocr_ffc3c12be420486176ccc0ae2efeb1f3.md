# 462 MACHINE LEARNING

![](bbox=[0.104, 0.085, 0.895, 0.413])

and recover the four features using the trained model:

```
tabC3: update factorC1:factorModel[], factorC2:factorModel[1], factorC3:
factorModel1[2], factorC4:factorModel[3] from update factorModel:
quantQ. nn.funcNN['nonlinearReg']([1.0,]; quantQ.nn.sigmoid([1.0, 'flip']
([xC1,xC2,xC3,xC4])) mmu pIn2HidC3) mmu pHID2OutC3) from ([], xC1;
xC2; xC3; xC4; factor);
```

Finally, we confirm the trained neural network models the input well. We calculate the correlation between the component of the input and the corresponding modelled value:

cor[tabC3~xC1;tabC3~factorC1]
0.9985345

cor[tabC3~xC2;tabC3~factorC2]
0.9992018

cor[tabC3~xC3;tabC3~factorC3]
0.9987443

cor[tabC3~xC4;tabC3~factorC4]
0.9989041