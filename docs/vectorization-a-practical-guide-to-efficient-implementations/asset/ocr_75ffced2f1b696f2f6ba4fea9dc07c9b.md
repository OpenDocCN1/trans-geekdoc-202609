```
from scipy.sparse import csc_matrix, load_npz, save_npz
from sklearn.model_selection import train_test_split
# Split train/test set
df = pd.read_csv(
    ".//ml-100k/u.data",
    names=["userId", "movieId", "rating", "timestamp"],
    usecols=["userId", "movieId", "rating"],
    header=None, sep="\t",
)
df_train, df_test = train_test_split(
    df, test_size=0.2, random_state=42
)
# df = None # remove the original dataframe
# Convert to sparse matrix
R_train = csc_matrix(
    (df_train["rating"], (df_train["userId"], df_train["movieId"])),
    shape=(944, 1683),
    dtype=np.float16
)
R_test = csc_matrix(
    (df_test["rating"], (df_test["userId"], df_test["movieId"])),
    shape=(944, 1683),
    dtype=np.float16
)
# Save the data
scipy.sparse.save_npz(
    ".//ml-100k/R_train_top.npz", R_train
)
scipy.sparse.save_npz(
    ".//ml-100k/R_test_top.npz", R_test
)
```

# Let's now train the model

```
# train the model
U, W, b, c, mu, J, J_eval = regularized_matrix_factorization(
    R_train, R_test, K=25, l2_reg=0.1, maxiter=30
)
# save results
np.savez(
    './/ml-100k/l2_regularized_matrix_factorization.npz',
    U=U, W=W, b=b, c=c, mu=mu, J=J, J_eval=J_eval,
)
```

We can plot out the training loss function over time (as illustrated in Figure 7.13).