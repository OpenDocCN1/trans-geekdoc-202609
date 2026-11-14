```
```python
from tqdm import tqdm
import multiprocessing
from joblib import Parallel, delayed
import pandas as pd

def apply_parallel(df_grouped, func):
    """
    Apply a function to grouped pandas dataframe using
        multiprocessing.
    Usage:
    def apply_func(pandas_df) :
        ...
    df = apply_parallel (
        df.groupby(
            by=grouped_by_columns,
            as_index=False,
        ),
        apply_func
    """
    ret = Parallel(n_jobs=multiprocessing.cpu_count()) (
        delayed(func)(group) for name, group in tqdm(df_grouped)
    ) # enumerate(tqdm(dfGrouped))
    return pd.concat(ret)
```
```

We then use this helper function to perform our batchwise transformations

```
```python
df_out_parallel = apply_parallel(
    df.groupby(by="id", as_index=False), apply_func
)
```
```

This takes 677 ms, which is much slower than using the native pandas. DataFrame.apply function. This is because setting up multiprocessing has an overhead, so most of the process is used to set up the multiprocessing environment instead of performing the actual computation. However, when the size of the data and the number of batches are large, we can expect that the additional overhead can be worthwhile for the overall speed gain from multiprocessing. Let's now instead randomly generate 100,000 rows of data for our transformation.

```
```python
import string
import random
df = pd.DataFrame({
    "id": [
        "".join(
            random.choices(string.ascii_letters, k=3)
        ) for _ in range(100_000)
    ],
    "scores": [
        random.randint(1, 100) for _ in range(100_000)
    ],
})
```
```