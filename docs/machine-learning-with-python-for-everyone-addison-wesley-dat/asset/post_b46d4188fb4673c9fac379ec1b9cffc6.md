
## 3.7.2.4 Time

In a Jupyter notebook, we have some nice tools to measure execution times. These are great for measuring the time use of small snippets of code. If we have two different ways of coding a solution to a problem and want to compare their speed, or just want to measure how long a snippet of code takes, we can use Python’s timeit module. The Jupyter cell magic %timeit gives us a convenient interface to time a line of code:

```
In [12]:

%timeit -r1 datasets.load_iris()
```

1000 loops, best of 1: 1.4 ms per loop

The -r1 tells timeit to measure the timing of the snippet once. If we give a higher r, for repeats, the code will be run multiple times and we will get statistics. Recent versions of Jupyter default to calculating the mean and standard deviation of the results. Fortunately, for a single result we just get that single value. If you are concerned about the 1000 loops, check out my note on it at the end of the chapter. %%timeit—the two-percents make it a cell magic—applies the same strategy to the entire block of code in a cell:

```
In [13]:

%%timeit -r1 -n1
(iris_train_ftrs, iris_test_ftrs,
 iris_train_tgt,  iris_test_tgt) = skms.train_test_split(iris.data,
                                        iris.target,
                                        test_size=.25)
```

1 loop, best of 1: 638 µs per loop

And now let’s point our chronometer (timeit) at our learning workflow:

```
In [14]:

%%timeit -r1

nb  = naive_bayes.GaussianNB()
fit  = nb.fit(iris_train_ftrs, iris_train_tgt)
preds = fit.predict(iris_test_ftrs)

metrics.accuracy_score(iris_test_tgt, preds)
```

1000 loops, best of 1: 1.07 ms per loop

```
In [15]:
%timeit -r1
knn = neighbors.KNeighborsClassifier(n_neighbors=3)
fit = knn.fit(iris_train_ftrs, iris_train_tgt)
preds = fit.predict(iris_test_ftrs)
metrics.accuracy_score(iris_test_tgt, preds)
```

1000 loops, best of 1: 1.3 ms per loop

If we just want to time one line in a cell—for example, we only want to see how long it takes to fit the models—we can use a single-percent version, called a line magic, of timeit:

```
In [16]:
# fitting
nb = naive_bayes.GaussianNB()
%timeit -r1 fit = nb.fit(iris_train_ftrs, iris_train_tgt)
knn = neighbors.KNeighborsClassifier(n_neighbors=3)
%timeit -r1 fit = knn.fit(iris_train_ftrs, iris_train_tgt)
```

1000 loops, best of 1: 708 μs per loop
1000 loops, best of 1: 425 μs per loop

```
In [17]:
# predicting
nb = naive_bayes.GaussianNB()
fit = nb.fit(iris_train_ftrs, iris_train_tgt)
%timeit -r1 preds = fit.predict(iris_test_ftrs)
knn = neighbors.KNeighborsClassifier(n_neighbors=3)
fit = knn.fit(iris_train_ftrs, iris_train_tgt)
%timeit -r1 preds = fit.predict(iris_test_ftrs)
```

1000 loops, best of 1: 244 μs per loop
1000 loops, best of 1: 644 μs per loop

There seems to be a bit of a tradeoff. k-NN is faster to fit, but slower to predict. Conversely, NB takes a bit of time to fit, but is faster predicting. If you're wondering why I didn’t reuse the knn and nb from the prior cell, it’s because when you %timeit, variable assignment are trapped inside the timeit magic and don’t leak back out to our main code. For example, trying to use preds as “normal” code in the prior cell will results in a NameError.

## 3.7.2.5 Memory

We can also do a very similar sequence of steps for quick-and-dirty measurements of memory use. However, two issues raise their ugly heads: (1) our tool isn’t built into Jupyter, so we need to install it and (2) there are technical details—err, opportunities?—that we’ll get to in a moment. As far as installation goes, install the `memory_profiler` module with `pip` or `conda` at your terminal command line:

```
pip install memory_profiler
conda install memory_profiler
```

Then, in your notebook you will be able to use `%load_ext`. This is Jupyter’s command to load a Jupyter extension module—sort of like Python’s `import`. For `memory_profiler`, we use it like this:

```
%load_ext memory_profiler
```

Here it goes:

In [18]:

```
%load_ext memory_profiler
```

Use it is just like `%%timeit`. Here’s the cell magic version for Naive Bayes:

In [19]:

```
%%memit
nb = naive_bayes.GaussianNB()
fit = nb.fit(iris_train_ftrs, iris_train_tgt)
preds = fit.predict(iris_test_ftrs)
```

peak memory: 144.79 MiB, increment: 0.05 MiB

And for Nearest Neighbors:

In [20]:

```
%%memit
knn = neighbors.KNeighborsClassifier(n_neighbors=3)
fit = knn.fit(iris_train_ftrs, iris_train_tgt)
preds = fit.predict(iris_test_ftrs)
```

peak memory: 144.79 MiB, increment: 0.00 MiB

## 3.7.2.6 Complicating Factors

You may never have considered what happens with memory on your computer. In the late 2010s, you might have 4 or 8GB of system memory, RAM, on your laptop. I have 32GB
on my workhorse powerstation—or workstation powerhorse, if you prefer. Regardless, that system memory is shared by each and every running program on your computer. It is the job of the operating system—Windows, OSX, Linux are common culprits—to manage that memory and respond to applications’ requests to use it. The OS has to be a bit of a playground supervisor to enforce sharing between the different programs.

Our small Python programs, too, are playing on that playground. We have to share with others. As we request resources like memory—or time on the playground swing—the OS will respond and give us a block of memory to use. We might actually get more memory than we request (more on that in a second). Likewise, when we are done with a block of memory—and being the polite playground children that we are—we will return it to the playground monitor. In both our request for memory and our return of the memory, the process incurs management overhead. Two ways that OSes simplify the process and reduce the overhead are (1) by granting memory in blocks that might be more than we need and (2) by possibly letting us keep using memory, after we’ve said we’re done with it, until someone else actively needs it. The net result of this is that determining the actual amount of memory that we are using—versus the amount the operating system has walled off for us—can be very tricky. Measuring additional requests within a running program is even more difficult.

Another issue further complicates matters. Python is a memory-managed language: it has its own memory management facilities on top of the OS. If you were to rerun the above cells in a Jupyter notebook, you might see a memory increment of 0.00 MiB and wonder what circuits just got fried. In that case, the old memory we used was released by us—and the operating system never shuffled it off to someone else. So, when we needed more memory, we were able to reuse the old memory and didn’t need any new memory from the OS. It is almost as if the memory was released and reclaimed by us so quickly that it was never actually gone! Now, whether or not we see an increment is also dependent on (1) what the notebook cell is doing, (2) what other memory our program has claimed and is using, (3) every other program that is running on the computer, and (4) the exact details of the operating system’s memory manager. To learn more, check out a course or textbook on operating systems.

## 3.7.3 Stand-Alone Resource Evaluation

To minimize these concerns and to reduce confounding variables, it is extremely useful to write small, stand-alone programs when testing memory use. We can make the script general enough to be useful for stand-alone timing, as well.

In [21]:

```
!cat scripts/knn_memtest.py

import memory_profiler, sys
from mlwpy import *

@memory_profiler.profile(precision=4)
def knn_memtest(train, train_tgt, test):
    knn  = neighbors.KNeighborsClassifier(n_neighbors=3)
    fit  = knn.fit(train, train_tgt)
    preds = fit.predict(test)

if __name__ == "__main__":
    iris = datasets.load_iris()
    tts = skms.train_test_split(iris.data,
                                iris.target,
                                test_size=.25)

    (iris_train_ftrs, iris_test_ftrs,
     iris_train_tgt,  iris_test_tgt) = tts
    tup = (iris_train_ftrs, iris_train_tgt, iris_test_ftrs)
    knn_memtest(*tup)
```

There are a few ways to use `memory_profiler`. We’ve seen the line and cell magics in the previous section. In `knn_memtest.py`, we use the `@memory_profiler.profile` decorator. That extra line of Python tells the memory profiler to track the memory usage of `knn_memtest` on a line-by-line basis. When we run the script, we see memory-related output for each line of `knn_memtest`:

In [22]:

```
!python scripts/knn_memtest.py
```

```
Filename: scripts/knn_memtest.py
# output modified for formatting purposes

Line #   Mem usage   Increment   Line Contents
================================================
   4 120.5430 MiB 120.5430 MiB   @memory_profiler.profile(precision=4)
   5                              def knn_memtest(train, train_tgt, test):
   6 120.5430 MiB   0.0000 MiB      knn  = neighbors.
                                   KNeighborsClassifier(n_neighbors=3)
   7 120.7188 MiB   0.1758 MiB      fit  = knn.fit(train, train_tgt)
   8 120.8125 MiB   0.0938 MiB      preds = fit.predict(test)
```

Here’s another stand-alone script to measure the memory usage of Naive Bayes:

In [23]:

```
```python
import functools as ft
import memory_profiler
from mlwpy import *

def nb_go(train_ftrs, test_ftrs, train_tgt):
    nb  = naive_bayes.GaussianNB()
```
