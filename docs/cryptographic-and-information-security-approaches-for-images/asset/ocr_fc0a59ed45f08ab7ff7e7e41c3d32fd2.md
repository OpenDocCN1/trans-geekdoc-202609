if the cover signal has been a compressed signal, it is very different to hide bits by this strategy. Thereafter, researchers invented many other comprehensive reversible data hiding schemes. There are two commonly used strategies. One is histogram-shifting and another is difference expansion hiding. Following, we will review the principles.

# 14.4.1 Difference Expansion Hiding

The first well-known reversible data hiding is the difference expansion hiding at 2003. The hiding unit includes two pixels which are usually neighbor pixels. Otherwise, the expanded difference becomes relative larger and causes large modification for the two pixels. This is different from the non-reversible data hiding by modifying the difference. Suppose the pixel values are p_i, p_{i+1}, then the difference d is p_{i+1} - p_i, it is represented in binary form: d = (d_k ... d_2 d_1 d_0)_2, the information bit is m_i, then:

+   - **Hiding:**
+     $(p_i', p_{i+1}') = (\lfloor \frac{p_i + p_{i+1}}{2} \rfloor \pm \lfloor \frac{d'}{2} \rfloor, \lceil \frac{p_i + p_{i+1}}{2} \rceil \mp \lfloor \frac{d'}{2} \rfloor)$  (14.13)
+     where, $d' = (d_k \cdots d_2 d_1 d_0 m_i)_2$.
+   - **Extracting:**
+     $d' = p_{i+1}' - p_i' = (d_k \cdots d_2 d_1 d_0 m_i)_2$,  (14.14)
+     $m_i$ is the extracted bit.
+   - **Recovering:**
+     $d = (d_k \cdots d_2 d_1 d_0)_2$, $p_i = \lfloor \frac{p_i' + p_{i+1}'}{2} \rfloor \mp \lfloor \frac{d}{2} \rfloor$, $p_{i+1} = \lceil \frac{p_i' + p_{i+1}'}{2} \rceil \pm \lfloor \frac{d}{2} \rfloor$ (14.15)

Suppose $(p_i, p_{i+1})$ be $(108,115)$, then $d = 7 = (111)_2$, the information bit is 0. Then $d' = (1110)_2 = 14$, thus $p_i' = 111 - 7 = 104$, $p_{i+1}' = 111 + 7 = 118$. The extracting is straightforward. The recovering is also simple: $p_i = 111 - 3 = 108$, $p_{i+1} = 111 + 3 = 115$.

Later, this scheme is extended into other domain and hiding units and it is considered as a special case of generalized integer transform [36]. But the basic idea is not changed. It also can be used in compressed domain. The difference is that the hiding unit are other elements in compressed domain rather than the pixels values.

# 14.4.2 Histogram-Shifting Hiding

This scheme is based on the statistical histogram of an image. First a peak value $hist_p$ in the 256-dimensional histogram $hist$ is located, and then shifting the left