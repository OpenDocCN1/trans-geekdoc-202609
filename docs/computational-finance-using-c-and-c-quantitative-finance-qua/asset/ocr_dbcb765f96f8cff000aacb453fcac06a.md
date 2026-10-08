# 156 Computational Finance Using C and C#

nearest asset grid line. Furthermore, as the number of asset points, $n_s$, increases the magnitude of $d_s$ will oscillate within the range 0 to $\Delta S/2$.

When $d_s \sim 0$ the grid will be accurate, but when $|d_k| \sim \Delta S/2$ there will be a large pricing error. This gives rise to the oscillating pricing errors shown in Figs. 5.7 and 5.8.

The nonuniform grids are constructed using the techniques mentioned earlier in this section, and also Code excerpt 5.19. We now, irrespective of $n_s$, arrange for one asset grid line to coincide with the current asset value, $S_0$, and another asset grid line $B_L$ to coincide with $B$ and not using $B_U$. In Fig 5.6 this corresponds to setting $B_U$.

It can be seen in Figs. 5.7 and 5.8 in this case the pricing error is very much less, and also does not exhibit the pronounced oscillations that are produced by a uniform grid. In Code excerpt 5.19 we give the computer program which was used to obtain the nonuniform grid values for the down and call options presented in Figs. 5.7 and 5.8. Although this program only deals with European options it can be easily altered, using the same techniques as in Code excerpt 5.18, to deal with American-style options; this is left as an exercise for the reader.

![](bbox=[0.158, 0.47, 0.842, 0.833])

**Figure 5.6** A nonuniform grid in which the grid spacing is reduced near current time $t$, and also in the neighborhood of the asset price 25; this can lead to greater accuracy in the computed option values and the associated *Greeks*. Grid lines are also placed at asset prices of $B_L$ and $B_U$; this enables the accurate evaluation of options which have barriers at these asset prices.