# European options

![](bbox=[0.142, 0.097, 0.857, 0.433])

Figure 4.3 Excel worksheet after calculation of the European options.

The cumulative standard normal distribution can also be used to provide analytic solutions for a range of *exotic* options as such as: Barrier options, Exchange options, Lookback options, Binary options, etc.

# 4.5 Barrier options

# 4.5.1 Introduction

Barrier options are derivatives that the payoff depends on whether the asset price reaches a given barrier level, *Knockout* options become worthless (cease to exist) if the asset price reaches the barrier, whereas *knockin* options come into existence when the asset price *bits* the barrier. We will consider the following single asset European options:

+   - **Down and out call**: A knockout vanilla call option, value $c_{d0}$, which ceases to exist when the asset price reaches or goes below the barrier level.
- **Up and out call**: A knockout vanilla call option, value $c_{uo}$, which ceases to exist when the asset price reaches, or goes above the barrier level.
- **Down and in call**: A knockin vanilla call option, value $c_{di}$, which comes into existence when the asset price reaches or goes above the barrier level.