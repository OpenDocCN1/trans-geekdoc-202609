```
```python
energy_old = energy_new
#end if
self.samples[iter, :] = np.array([x_old, y_old])
self.energies[iter] = energy_old

T = self.temperature_schedule(T, iter)
self.temperatures[iter] = T

iter = iter + 1

    if (iter > self.max_iter): converged = True
#end while

niter = iter - 1
acceptance_rate = num_accepted / niter
print("acceptance rate: ", acceptance_rate)

x_opt, y_opt = x_old, y_old

return x_opt, y_opt, self.samples[:niter,:], self.energies[:niter], self.temperatures[:niter]

if __name__ == "__main__":

    SA = simulated_annealing()

    nx, ny = (1000, 1000)
    x = np.linspace(-2, 2, nx)
    y = np.linspace(-2, 2, ny)
    xv, yv = np.meshgrid(x, y)

    z = SA.target(xv, yv)
    plt.figure()
    plt.contourf(x, y, z)
    plt.title("energy landscape")
    plt.show()

    #find global minimum by exhaustive search
    min_search = np.min(z)
    argmin_search = np.argwhere(z == min_search)
    xmin, ymin = argmin_search[0][0], argmin_search[0][1]
    print("global minimum (exhaustive search): ", min_search)
    print("located at (x, y): ", x[xmin], y[ymin])

    #find global minimum by simulated annealing
    x_init, y_init = 0, 0
    x_opt, y_opt, samples, energies, temperatures = SA.run(x_init, y_init)
    print("global minimum (simulated annealing): ", energies[-1])
    print("located at (x, y): ", x_opt, y_opt)

    plt.figure()
    plt.plot(energies)
    plt.title("SA sampled energies")
    plt.show()
```
```