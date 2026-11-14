# 6
String Processing

In our journey on vectorization so far, we have only been dealing with numerical data types (integers, float, complex, etc.). However, string data are also becoming more common especially when dealing with natural language processing (NLP) problems. In other applications of machine learning, we sometimes need to deal with categorical features, which often come as string values in the raw data form. Therefore, in this chapter, we will briefly examine vectorization operations on string values.

# ## 6.1 String Data Types

# ### 6.1.1 NumPy String, Bytes, and Object

NumPy has three data types that can be used to encode string values in its `np.ndarray`: `'S'` for byte string (corresponding to `np.bytes_` dtype), `'U'` for unicode characters (`np.str_`), and `'O'` or `object` for encoding objects in general (corresponding to `np.object_` dtype), including strings and bytes. We can construct an array of strings in NumPy as the following:

```
```python
import numpy as np
value = ["a", "b", "c"]
A_string = np.array(value, dtype=np.str_)
# array(['a', 'b', 'c'], dtype='<U1')

A_bytes = np.array(value, dtype=np.bytes_)
# array([b'a', b'b', b'c'], dtype='|S1')

A_object = np.array(value, dtype=object)
# array(['a', 'b', 'c'], dtype=object)
```
```