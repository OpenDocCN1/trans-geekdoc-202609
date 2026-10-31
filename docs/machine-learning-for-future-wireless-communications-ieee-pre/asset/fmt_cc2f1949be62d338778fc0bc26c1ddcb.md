
## Multi-cell Model Transmission Delay

In the considered multi-cell model, if user `j` requests a content that is not cached at any base station that can connect with the user, the content file will be first transmitted from the cloud data center to base station `i_hat`, which is the closest base station to user `j`, and then from base station `i_hat` to user `j`. Thus, the minimum transmission delay `D_hat_j` in the case of missing file in the cache can be expressed as

(21.5)
```
D_hat_j = T_{c,i_hat} + T_{i_hat,j}
```

where `T_{c,i_hat}` stands for the transmission delay from the cloud data center to base station `i_hat`, and `T_{i_hat,j}` is the transmission delay from base station `i_hat` to user `j`.

However, if the requested file is cached at base station `i`, which can connect to user `j`, the transmission delay `D_j` for the case of hitting the cache can be expressed as

(21.6)
```
D_j = T_{i,j}
```

Now, the transmission delay for both cases of missing and hitting the cache is known, and we define the transmission delay reduction `ΔD_j` as

(21.7)
```
ΔD_j = D_hat_j - D_j
```

So, the average transmission delay reduction in an operation cycle is

(21.8)
```
ΔD = 1/U sum_{j=1}^{U} ΔD_j
```
(21.9)
```
= 1/U sum_{j=1}^{U} (D_hat_j - D_j)
```
(21.10)
```
= 1/U sum_{j=1}^{U} (T_{c,i_hat} + T_{i_hat,j} - T_{i,j})
```

where `U` is the total number of users. Now, our goal is to maximize the average transmission delay reduction, and the caching problem is formulated as follows:
