Example: Modelling the Spread of COVID-19

# 15.3.1 SEIR Model

First, we use the SEIR model function to simulate the spread of the disease. The model compartments are: number of susceptible (S), the exposed (E), the infected (I), and R represents the number of recovered individuals. The parameters of the model are the transmission rate (β) and the recovery rate (γ), (k_exp) the latent period, and (N) is the total population.

```
library(deSolve)
library(tidyverse)
# Define parameters
N <- 16 # Total population
beta <- 0.5 # Transmission rate
gamma <- 0.1 # Recovery rate
t_exp <- 5 Latent period - or incubation period

# Initial conditions
init <- c(S = N - 1, E = 1, I = 0, R = 0)

# Define the SEIR model
seir_model <- function(t, y, parameters) {
  with(as.list(y),
    dS <- -beta * S * I / N
    dE <- beta * S * I / N - (1 / t_exp) * E
    dI <- (1 / t_exp) * E - gamma * I
    dR <- gamma * I
    return(list(c(dS, dE, dI, dR)))
  )
}
```

As previously, we use the ode() function from the {deSolve} package to solve the ordinary differential equations (ODEs) and simulate the spread of the virus over a period of 365 days:

```
times <- seq(0, 365, by = 1)
result <- ode(y = init, times = times, func = seir_model)
head(result, n = 6)
# time S E I R
# [1] 0 99999.0 1.000000 0.000000 0.000000
# [2] 1 99999.9 0.861442 0.175097 0.0091308
# [3] 2 99999.8 0.818671 0.316995 0.0339232
# [4] 3 99999.6 0.840094 0.444173 0.0720450
# [5] 4 99999.4 0.921481 0.562981 0.1269274
# [6] 5 99999.1 1.042877 0.701588 0.1861446
```

```
ggplot(as.frame(result), aes(time = Time, color = "Infected")) +
geom_line(aes(y = R, color = "Recovered")) +
geom_line(aes(y = S, color = "Susceptible")) +
scale_color_discrete(name = "Compartment") +\nlabs(x = "Time (days)", y = "Number of individuals")
```