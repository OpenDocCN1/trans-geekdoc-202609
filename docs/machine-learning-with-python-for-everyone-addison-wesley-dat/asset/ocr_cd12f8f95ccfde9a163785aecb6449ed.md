# Chapter 8 More Classification Methods

trying to relate three measurements that we really don’t expect to be related at all: height, SAT scores, and love of abstract art. We get something like this:

```
In [44]:
data = pd.DataFrame({'x': [3, 6, 3, 4],
'y': [9, 6, 3, 0],
'z': [1, 4, 7, 0]})
data.index.name = 'examples'
display(data)
print("Covariance:")
display(data.cov())  # biased covariance, see EOC
```

|   | x | y | z |
| --- | --- | --- | --- |
| examples |   |   |   |
| 0 | 3 | 9 | 1 |
| 1 | 6 | 6 | 4 |
| 2 | 3 | 3 | 7 |
| 3 | 4 | 0 | 0 |

|   | x | y | z |
| --- | --- | --- | --- |
| x | 2.0000 | 0.0000 | 0.0000 |
| y | 0.0000 | 15.0000 | 0.0000 |
| z | 0.0000 | 0.0000 | 10.0000 |

The data numbers don’t look so special, but that’s a weird covariance matrix. What’s going on here? Let’s plot the data values:

```
In [45]:
fig, ax = plt.subplots(1,1,figsize=(4,3))
data.plot(ax=ax)
ax.vlines([0,1,2,3], 0, 10, colors=".5")
ax.legend(loc='lower center', ncol=3)
plt.box(False)
ax.set_xticks([0,1,2,3])
ax.set_ylabel("values");
```