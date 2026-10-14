
```python
R2 = X**2 + Y**2
inside = R2 < radius**2
outside = ~inside

samples = (2*radius)*(2*radius)*inside

I_hat = np.mean(samples)
pi_hat = I_hat/radius ** 2
pi_hat_se = np.std(samples)/np.sqrt(num_iter)
print("pi est: {} +/- {:f}".format(pi_hat, pi_hat_se))

plt.figure()
plt.scatter(X[inside],Y[inside], c='b', alpha=0.5)
plt.scatter(X[outside],Y[outside], c='r', alpha=0.5)
plt.show()

if __name__ == "__main__":
    pi_est()
```

If we execute the code, we get π = 3.1348 ± 0.0164, which is a relatively good result (within the error bounds). Try experimenting with different numbers of samples N to see how fast we converge to π as a function of N. Figure 2.5 shows the accepted Monte Carlo samples in blue, corresponding to samples inside the circle, and the rejected samples in red, corresponding to samples outside the circle.

![](img/325742126d3ff007c6c385f4ffb5c3be_41_0.png)

Figure 2.5 Monte Carlo samples used to estimate pi

In the preceding example, we assumed that samples came from a uniform distribution X, Y ~ Unif(−R, R). In the following section, we will look at simulating a stock price over different time horizons using the binomial tree model.

## 2.3 Binomial tree model

Now, let’s examine how Monte Carlo sampling can be used in finance. In a binomial tree model of a stock price, we assume that at each time step, the stock could be in either up or down states with unequal payoffs characteristic for a risky asset. Assuming the initial stock price at time t = 0 is $1, at the next time step t = 1, the price is u in the up state and d in the down state, with up-state transition probability p. A binomial tree model for the first two timesteps is shown in figure 2.6. Note that the price in the next up (down) state is u (d) times the price of the previous state.

We can use Monte Carlo to generate uncertainty estimates of the terminal stock price after some time horizon T. When using a binomial model to describe the price process of the stock, we can use the following calibration (the derivation of which is outside the scope of this book).

u = exp( σ sqrt(T/n) ) = 1/d

p = 1/2 + 1/2 (μ/σ) sqrt(T/n)   (2.12)

Here, T is the length of the prediction horizon in years and n is the number of time steps. We assume 1 year equals 252 trading days, 1 month equals 21 days, 1 week equals 5 days, and 1 day equals 8 hours. Let's simulate the stock price using the binomial model with a daily time step for two different time horizons: 1 month from today and 1 year from today. We can summarize the algorithm in the pseudo-code shown in figure 2.7.

```
1: function binomial_tree(μ, σ, S0, N, T, step):
2: u = exp( σ sqrt(T/n) ) ← Up price
3: d = 1/u ← Down price
4: p = 1/2 + 1/2 (μ/σ) sqrt(T/n) ← Up-state transition probability
5: up_times = Binomial( T/step, p, N )
6: down_times = T/step - up_times
7: S_T = S0 × u^{up_times} × d^{down_times}
8: return S_T
```

![](img/325742126d3ff007c6c385f4ffb5c3be_42_0.png)

Figure 2.6 Binomial tree model

Figure 2.7 Binomial tree pseudo-code

We begin by initializing up price u and down price d, along with up-state transition probability p. Next, we simulate all the up-state transitions by sampling from a Binomial random variable with the number of trials equal to T/step, the success probability p, and the number of Monte Carlo simulations equal to N. The down-state transitions are computed by complementing up-state transitions. Finally, we compute the asset price by multiplying the initial price S0 with the price of all the up-state transitions and all the down-state transitions.

### Listing 2.2 Binomial tree stock price simulation

```python
import numpy as np

import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(42)

def binomial_tree(mu, sigma, S0, N, T, step):

    #compute state price and probability
    u = np.exp(sigma * np.sqrt(step))
    d = 1.0/u
    p = 0.5+0.5*(mu/sigma)*np.sqrt(step)

    #binomial tree simulation
    up_times = np.zeros((N, len(T)))
    down_times = np.zeros((N, len(T)))
    for idx in range(len(T)):
        up_times[:,idx] = np.random.binomial(T[idx]/step, p, N)
        down_times[:,idx] = T[idx]/step - up_times[:,idx]

    #compute terminal price
    ST = S0 * u**up_times * d**down_times

    #generate plots
    plt.figure()
    plt.plot(ST[:,0], color='b', alpha=0.5, label='1 month horizon')
    plt.plot(ST[:,1], color='r', alpha=0.5, label='1 year horizon')
    plt.xlabel('time step, day')
    plt.ylabel('price')
    plt.title('Binomial-Tree Stock Simulation')
    plt.legend()
    plt.show()

    plt.figure()
    plt.hist(ST[:,0], color='b', alpha=0.5, label='1 month horizon')
    plt.hist(ST[:,1], color='r', alpha=0.5, label='1 year horizon')
    plt.xlabel('price')
    plt.ylabel('count')
    plt.title('Binomial-Tree Stock Simulation')
    plt.legend()
    plt.show()

if __name__ == "__main__":

    #model parameters
    mu = 0.1
    sigma = 0.15
    S0 = 1
    N = 10000
    T = [21.0/252, 1.0]
    step = 1.0/252

    binomial_tree(mu, sigma, S0, N, T, step)
```

```
1: function rand_walk(num_step, num_iter, moves):
2: X, Y, lattice = 0, 0, 0
3: weight = 1
4: xx = num_step + 1 + X ← Middle of the x-axis
5: yy = num_step + 1 + Y ← Middle of the y-axis
6: lattice[xx, yy] = 1 ← Init grid position
7: for i = 1 to num_step:
8:   up = lattice[xx, yy+1]
9:   down = lattice[xx, yy-1]
10:  left = lattice[xx-1, yy]
11:  right = lattice[xx+1, yy]
12:  neighbors = [1, 1, 1, 1]− [up, down, left, right] ← Available directions
13:  if sum(neighbors) == 0
14:    break ← Self-loop
15:  end if
16:  weight = weight × sum(neighbors) ← Computes importance weights
17:  direction ~ Cat( neighbors / sum(neighbors) ) ← Samples a move direction
18:  X = X+ moves[direction]
19:  Y = Y+ moves[direction]
20:  // update grid coordinates
21:  xx = num_step + 1 + X
22:  yy = num_step + 1 + Y
23:  lattice[xx, yy] = 1
24: end for
25: return lattice
```

Figure 2.9 Random walk pseudo-code

Next, we sample a move direction from the available directions, represented by a sample from the categorical random variable. Since the neighbors array can only take the values of 0 and 1, we are sampling uniformly from the available directions.

Next, we update the grid coordinates xx and yy and mark the occupancy by setting lattice[xx, yy]=1. While only a single iteration is shown in the pseudo-code, the following code listing wraps the pseudo-code in an additional for loop over the number of iterations num_iter. Each iteration is an attempt or a trial to produce a nonintersecting (i.e., self-avoiding random walk). The square distance of the random walk and the importance weights are recorded in each trial. We are now ready to look at the self-avoiding random walk code.

### Listing 2.3 Self-avoiding random walk

```python
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(42)

def rand_walk(num_step, num_iter, moves):
```

```python
#random walk stats
square_dist = np.zeros(num_iter)
weights = np.zeros(num_iter)

for it in range(num_iter):

    trial = 0
    i = 1

    while i != num_step-1:

        #init
        X, Y = 0, 0
        weight = 1
        lattice = np.zeros((2*num_step+1, 2*num_step+1))
        lattice[num_step+1,num_step+1] = 1
        path = np.array([0, 0])
        XX = num_step + 1 + X
        YY = num_step + 1 + Y

        print("iter: %d, trial %d" %(it, trial))

        for i in range(num_step):

            up     = lattice[XX,YY+1]
            down   = lattice[XX,YY-1]
            left   = lattice[XX-1,YY]
            right  = lattice[XX+1,YY]

            neighbors = np.array([1, 1, 1, 1]) -
                np.array([up, down, left, right])

            if (np.sum(neighbors) == 0):
                i = 1
                break
            #end if

            weight = weight * np.sum(neighbors)

            direction = np.where(np.random.rand() <
                np.cumsum(neighbors/float(sum(neighbors))))

            X = X + moves[direction[0][0],0]
            Y = Y + moves[direction[0][0],1]

            path_new = np.array([X,Y])
            path = np.vstack((path,path_new))

            #update grid coordinates
            XX = num_step + 1 + X
            YY = num_step + 1 + Y
            lattice[XX,YY] = 1
        #end for

        trial = trial + 1
```

Iterates until we have a noncrossing random walk

Computes available directions

Avoids self-loops

Computes importance weights

Samples a move direction

Stores a sampled path
