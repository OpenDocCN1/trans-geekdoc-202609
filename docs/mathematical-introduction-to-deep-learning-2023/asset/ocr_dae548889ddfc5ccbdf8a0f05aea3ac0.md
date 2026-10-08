# 2.1. Compositions of fully-connected feedforward ANNs

Next note that (2.22), (2.2), and the assumption that $\mathcal{L}(\Phi_{2}) = 1$ imply that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1})\}$ it holds that

```
\begin{align} (\mathcal{W}_{k,\Phi_{1}\bullet\Phi_{2}}, \boldsymbol{B}_{k,\Phi_{1}\bullet\Phi_{2}}) = \begin{cases} (\mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{1,\Phi_{2}}, \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{1,\Phi_{2}} + \boldsymbol{B}_{1,\Phi_{1}}) & : k = 1 \\ (\mathcal{W}_{k,\Phi_{1}}, \boldsymbol{B}_{k,\Phi_{1}}) & : k > 1. \end{cases} \tag{2.24} \end{align}
```

This, (2.2), and (2.23) prove that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1}) + \mathcal{L}(\Phi_{3}) - 1\}$ it holds that

```
\begin{align} \begin{aligned} & \left(\mathcal{W}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}, \boldsymbol{B}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}\right) \\ &= \begin{cases} \left(\mathcal{W}_{k,\Phi_{3}}, \boldsymbol{B}_{k,\Phi_{3}}\right) & : k < \mathcal{L}(\Phi_{3}) \\ \left(\mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{3}}, \mathcal{W}_{1,\Phi_{1}\bullet\Phi_{2}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{1}\bullet\Phi_{2}}\right) & : k = \mathcal{L}(\Phi_{3}) \\ \left(\mathcal{W}_{k-\mathcal{L}(\Phi_{3})+1,\Phi_{1}\bullet\Phi_{2}}, \boldsymbol{B}_{k-\mathcal{L}(\Phi_{3})+1,\Phi_{1}\bullet\Phi_{2}}\right) & : k > \mathcal{L}(\Phi_{3}) \end{cases} \end{aligned} \tag{2.25} \end{align}
```

Furthermore, observe that (2.2), (2.22), and (2.23) show that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1}) + \mathcal{L}(\Phi_{3}) - 1\}$ it holds that

```
\begin{align} \begin{aligned} & \left(\mathcal{W}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}, \boldsymbol{B}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}\right) \\ &= \begin{cases} \left(\mathcal{W}_{k,\Phi_{2}\bullet\Phi_{3}}, \boldsymbol{B}_{k,\Phi_{2}\bullet\Phi_{3}}\right) & : k < \mathcal{L}(\Phi_{2}\bullet\Phi_{3}) \\ \left(\mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{\mathcal{L}(\Phi_{2}\bullet\Phi_{3}),\Phi_{2}\bullet\Phi_{3}}, \mathcal{W}_{1,\Phi}\boldsymbol{B}_{\mathcal{L}(\Phi_{2}\bullet\Phi_{3}),\Phi_{2}\bullet\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{1}}\right) & : k = \mathcal{L}(\Phi_{2}\bullet\Phi_{3}) \\ \left(\mathcal{W}_{k-\mathcal{L}(\Phi_{2}\bullet\Phi_{3})+1,\Phi_{1}}, \boldsymbol{B}_{k-\mathcal{L}(\Phi_{2}\bullet\Phi_{3})+1,\Phi_{1}}\right) & : k > \mathcal{L}(\Phi_{2}\bullet\Phi_{3}) \end{cases} \end{aligned} \tag{2.26} \end{align}
```

Combining this with (2.25) establishes that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1}) + \mathcal{L}(\Phi_{3}) - 1\} \setminus \{\mathcal{L}(\Phi_{3})\}$ it holds that

```
\begin{align} \left(\mathcal{W}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}, \boldsymbol{B}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}\right) = \left(\mathcal{W}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}, \boldsymbol{B}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}\right). \tag{2.27} \end{align}
```

Moreover, note that (2.24) and (2.2) ensure that

```
\begin{align} \mathcal{W}_{1,\Phi_{1}\bullet\Phi_{2}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} = \mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{1,\Phi_{2}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} = \mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{2}\bullet\Phi_{3}}. \tag{2.28} \end{align}
```

In addition, observe that (2.24) and (2.2) demonstrate that

```
\begin{align} \begin{aligned} \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{2}} + \boldsymbol{B}_{1,\Phi_{1}\bullet\Phi_{2}} &= \mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{1,\Phi_{2}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} + \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{1,\Phi_{2}} + \boldsymbol{B}_{1,\Phi_{1}} \\ &= \mathcal{W}_{1,\Phi_{1}}\left(\mathcal{W}_{1,\Phi_{2}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{2}}\right) + \boldsymbol{B}_{1,\Phi_{1}} \\ &= \mathcal{W}_{1,\Phi}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{2}\bullet\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{1}}. \end{aligned} \tag{2.29} \end{align}
```