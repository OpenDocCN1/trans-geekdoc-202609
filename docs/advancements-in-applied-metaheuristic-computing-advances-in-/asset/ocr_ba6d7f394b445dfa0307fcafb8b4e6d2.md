```
x_{new} = x_{old} + \varepsilon A^t (24)
```

Where \(\varepsilon \in [-1, 1]\) is a random number, while At=<Ait > is the average loudness
of all the bats at this time step. Based on these approximations and idealization, the
basic steps of the Bat Algorithm can be summarized as the pseudo code shown here.
(Venkateswara Rao B et.al, 2014; Yang, X.-S, 2010)

# Bat Algorithm

```
Objective function f(x), x = (x1,x2, ..., xd)T
Initialize the bat population xii (ii = 1, 2, ..., n) and vii
Define pulse frequency fii at xii
Initialize pulse rates rii and the loudness Aii
while (t <Max number of iterations)
Generate a new solution by changing frequency,
And modifying velocities and solutions
if (rand > rii)
Select a best solution in the available solutions
Create a local solution around the selected best solution
end if
Create a new solution by flying randomly
if (rand < Aii & f(xii) < f(xo))
Accept the new solutions
Increase rii and reduce Aii
end if
Rank the bats and find the current best xo
End while
Post process results and visualization
Pseudo code of the BAT algorithm.
Loudness and Pulse Emission
```

The loudness Ai and the rate of pulse emission ri are updated accordingly as the
iterations proceed. The loudness decreases and rate of pulse emission increases as
the bat closes on its prey i.e., the equations for convergence can be taken as (25)

```
A_i^{t+1} = \alpha A_i^t (25)
```