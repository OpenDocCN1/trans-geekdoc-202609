
消息传递可以从叶节点 `(*A*, *T*)` 和 `(*X*, *E*)` 开始，朝向 `(*S*, *L*, *B*)`；一旦该消息流完成，消息传递将在反方向进行。下面给出了一些消息计算的示例。

节点 `(*T*, *L*, *E*)` 接收到的消息等于

```
\mu_{S_{1}\rightarrow V_{2}}(T) = \sum\limits_{A}\psi_{1}(A,T).
```

此外，

```
\mu_{V_{2}\rightarrow S_{2}}(L,E) = \sum\limits_{T}\psi_{2}(T,L,E)\mu_{S_{1}\rightarrow V_{2}}(T) = \mu_{S_{2}\rightarrow V_{4}}(L,E),
```

以及

```
\mu_{V_{4}\rightarrow S_{3}}(L,B) = \sum\limits_{E}\psi_{4}(B,L,E)\mu_{S_{2}\rightarrow V_{4}}(L,E)\mu_{S_{4}\rightarrow V_{4}}(B,E).
```

其余消息的计算方式类似。

对于团节点 `V[2]` 中变量的边缘概率 `P(T, L, E)`，我们得到
