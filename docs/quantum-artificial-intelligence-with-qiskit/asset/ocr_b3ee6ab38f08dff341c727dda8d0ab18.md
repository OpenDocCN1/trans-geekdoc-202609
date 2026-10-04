```
qc.ccx(3,71)
#Dividing
qc.h(14)
qc.barrier()
#Marking
qc.cp(-pi/4,8,14)
qc.cp(-pi/4,9,14)
qc.cp(-pi/4,10,14)
qc.cp(-pi/4,11,14)
qc.barrier()
qc.x(14)
qc.cp(pi/4,8,14)
qc.cp(pi/4,9,14)
qc.cp(pi/4,10,14)
qc.cp(pi/4,11,14)
qc.h(14)
qc.draw(fold=110)
```

simulator = Aer.backend('statevector_simulator')
# Run and get counts
result=execute(qc,simulator).result()
counts = result.get_counts()
plot_histogram(counts)

With the query vector $x_q = (1, 0, 0, 1)$ units represented by the states following values

+   - The first unit has $count1=2$ and the two corresponding states are: for the control $qubit=1$, the value is $1 = \sin\frac{\pi}{2}$ with the measured probability $\sin\frac{\pi}{2}^2 = 0.5$ for the control $qubit=0$, the value is $0=\cos\frac{\pi}{2}$ with the measured probability 0.
- The second unit has $count2=1$ and the two corresponding states are: for the control $qubit=1$, the value is $\frac{1}{\sqrt{2}}=\sin\frac{\pi}{4}$ with the measured probability $\sin\frac{\pi}{4}^2=0.125$, for the control $qubit=0$, the value is $\frac{1}{\sqrt{2}}=\cos\frac{\pi}{4}$ with the measured probability $\cos\frac{\pi}{4}^2=0.125$.
- The third unit has $count3=1$ and the two corresponding states are: for the control $qubit=1$, the value is $0=\sin0$ with the measured probability $0$, and for the control $qubit=0$, the value is $1=\cos0$ with the measured probability $0.
- The fourth unit has $count4=2$ and the two corresponding states are: for the control $qubit=1$, the value is $1=\sin\frac{\pi}{2}$ with the measured probability $|\sin\frac{\pi}{2}|^2=0.25$, and for the control $qubit=0$, the value is $0=\cos\frac{\pi}{2}$ with the measured probability 0.

There are five states with probabilities not equal to zero, see Figure 15.11. The measured probability ($qubit=1$) indicating a firing of the units is 0.625.