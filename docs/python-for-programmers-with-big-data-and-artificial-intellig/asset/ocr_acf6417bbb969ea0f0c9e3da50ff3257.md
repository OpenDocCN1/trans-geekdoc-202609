```
Test2 87
Test3 90
Name: Eva, dtype: int64
```

If a `DataFrame`'s column-name strings are valid Python identifiers, you can use them as attributes. Let's get Sam's grades with the `Sam` attribute:

```
In [8]: grades.Sam
Out[8]:
Test1 94
Test2 77
Test3 90
Name: Sam, dtype: int64
```

# Selecting Rows via the `loc` and `iloc` Attributes

Though `DataFrames` support indexing capabilities with `[]`, the pandas documentation recommends using the attributes `loc`, `iloc`, `at` and `iat`, which are optimized to access `DataFrames` and also provide additional capabilities beyond what you can do only with `[]`. Also, the documentation states that indexing with `[]` _often_ produces a copy of the data, which is a logic error if you attempt to assign new values to the `DataFrame` by assigning to the result of the `[]` operation.

You can access a row by its label via the `DataFrame`'s `loc` attribute. The following lists all the grades in the row `'Test1'`:

lick here to view code image

```
In [9]: grades.loc['Test1']
Out[9]:
Wally 87
Eva 100
Sam 94
Katie 100
Bob 83
Name: Test1, dtype: int64
```

You also can access rows by integer zero-based indices using the `iloc` attribute (the `i` in `iloc` means that it's used with integer indices). The following lists all the grades in the second row:

lick here to view code image