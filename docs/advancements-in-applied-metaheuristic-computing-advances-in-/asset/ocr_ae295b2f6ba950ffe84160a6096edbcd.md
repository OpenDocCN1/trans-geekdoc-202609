crevices in the dark. We will first formulate The BAT algorithm by idealizing the echolocation behavior of bats. These bats emit a very loud sound pulse and listen for the echo that bounces back from surrounding objects. Bat algorithm is developed by idealizing some of the characteristics of micro bats. The approximated or idealized rules are (Yang, 2008):

+   1. All bats use echolocation to sense distance and they also know the difference between food/prey and barriers in some magical way.

+   2. Bats fly randomly with velocity vi at position xi with a fixed frequency fmin, varying wavelength λ and loudness A0 to search for prey. They can automatically adjust the wavelength (or frequency) of their emitted pulses and the rate of pulse emission r ∈ [0,1] depending on the proximity of the target.

+   3. Loudness varies from a large positive A0 to a minimum constant value Amin.

# Population

The initial population i.e., number of virtual bats for BAT algorithm is generated randomly. The number of bats can be anywhere between 10 and 40. After finding the initial fitness of the population for given objective function, the values are updated based on movement, loudness and pulse rate.

# Movement of Virtual Bats

The rules for updating the positions xi and velocities vi of the virtual bats are given as (22)

```
f_i^t = f_{min} + (f_{max} - f_{min})\beta
(21)
```

```
v_i^t = v_i^{t-1} + (x_i^t - x_*) f_i^t
(22)
```

```
x_i^t = x_i^{t-1} + v_i^t
(23)
```

Where, β ∈ [0, 1] is a random vector drawn from a uniform distribution. Here x* is the current global best location (solution) which is located after comparing all the solutions among all the n bats. A new solution for each bat is generated locally using random walk given by equation (24)