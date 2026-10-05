![](bbox=[0.34375, 0.09375, 0.62125, 0.24375])

**Fig. 2.3** Examples of a plot for the sigmoid function $f(x)=rac{1}{1+e^{-x}}$ with the Matlab library.

# Listing **2.23** FirstProgram.ipynb (part 23)

```
x=np.array([])
for i in range(21):
    x=np.append(x,(i-10))

x = np.array([i-10 for i in range(21)])
x = np.linspace(-10,10,21),
```

Plotting this function is simply achieved with the following commands

# Listing **2.24** FirstProgram.ipynb (part 24)

```
plt.plot(x,lsig(x))
plt.rcParams.update({'font.size': 20})
plt.xlabel('x'); plt.ylabel('y')
plt.savefig('tmp.pdf', format='pdf')
```

The plot(x,y) is enough to plot the basic graph in the Jupyter environment, though IPython you might need a plt.show() to trigger the display. The resulting plot is shown in Fig. 2.3. The example code shows how to change the font size of the axis labels, is often useful when including graphs in documents. The final command shows how to save the file into a pdf file.

# 2.2.5 Timing the program

Some of the programs might need some time to run, and it might be necessary to estimate the time of running with some smaller examples and measuring the time. It can be done in the following way.

# Listing **2.25** FirstProgram.ipynb (part 25) with output

```
import time
tic = time.clock()
toc = time.clock()
print(toc - tic)
2.2214871933101676e-05
```