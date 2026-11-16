```
```python
In [1]: months = {'January': 1, 'February': 2, 'March': 3}

In [2]: for month_name in months.keys():
   ....:     print(month_name, end=' ')
   ....: 
January February March

In [3]: for month_number in months.values():
   ....:     print(month_number, end=' ')
   ....: 
1 2 3
```
```

# Dictionary Views

Dictionary methods items, keys and values each return a view of a dictionary’s data.
When you iterate over a view, it “sees” the dictionary’s current contents—it does not
have its own copy of the data.

To show that views do not maintain their own copies of a dictionary’s data, let’s first
save the view returned by keys into the variable months_view, then iterate through
it:

![](bbox=[0.13, 0.48, 0.4, 0.51])

```
```python
In [4]: months_view = months.keys()

In [5]: for key in months_view:
   ....:     print(key, end=' ')
   ....: 
January February March
```
```

Next, let’s add a new key–value pair to months and display the updated dictionary:

![](bbox=[0.13, 0.72, 0.4, 0.745])

```
```python
In [6]: months['December'] = 12

In [7]: months
Out[7]: {'January': 1, 'February': 2, 'March': 3, 'December': 12}
```
```

Now, let’s iterate through months_view again. The key we added above is indeed
displayed:

![](bbox=[0.13, 0.94, 0.4, 0.97])