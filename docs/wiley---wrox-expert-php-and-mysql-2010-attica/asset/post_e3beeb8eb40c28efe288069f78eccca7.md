
| memc_set('foo', 'xyz', 5) |
|---|
| 0 |

1 row in set (0.01 sec)

| memc_get('foo') |
|---|
| xyz |

1 row in set (0.00 sec)

| sleep (6) |
|---|
| 0 |

1 row in set (6.01 sec)

| memc_get('foo') |
|---|
| NULL |

1 row in set (0.01 sec)

As you see, after six seconds, foo is expired to the bit-bucket in the sky.

The following code, of course, sets foo to the value of xyz without an expiration.

```
mysql> select memc_set('foo', 'xyz');
```

| memc_set('foo', 'xyz') |
|---|
| 1 |

## memc_set_by_key

The function memc_set_by_key() works the same way as memc_set() except the first argument is a master server key, which allows you to group stored values by server. The rest of the arguments are the same as memc_set, except they shifted by one. The second argument is the key for the object being stored. The third argument is the value being stored and the optional fourth value is a numeric expiration in seconds.

The syntax for memc_set_by_key() is:

```
memc_set_by_key('master key', 'key', value);
memc_set_by_key('master key', 'key', value, expiration);
```

The example that follows shows how you store a value using a server key:

```
mysql> select memc_set_by_key('A', 'key1', 'test');
```

| memc_set_by_key('A', 'key1', 'test') |
|---|
| 1 |

## memc_add

The function memc_add() takes two required arguments: a string key and a value. The value can be either numeric or a string that is cached in memcached and that is specified by key if this isn't already set. This function also has a third, optional, numeric argument for the number of seconds that the value is stored before it expires. memc_add() returns a zero upon success or a non-zero value upon failure.

The function memc_add_by_key() works the same as memc_add() except it has as its first argument a master server key that allows you to group stored values by server. The arguments following the master key argument are the same as for memc_add() — just shifted in order.

The syntax of memc_add() and memc_add_by_key() is:

```
memc_add('key', value);
memc_add('key', value, expiration);
memc_add_by_key('master key', 'key', value);
memc_add_by_key('master key', 'key', value, expiration);
```

The example that follows shows a value being added that, as yet, doesn't exist:

```
mysql> select memc_set('key1', 333);
```

| memc_set('key1', 333) |
|---|
| 1 |

## memc_replace

The function memc_replace takes two required arguments: a string key and a value, either numeric or string, that replaces the existing value of the key already stored. memc_replace returns a zero upon success or a non-zero value upon failure.

The function memc_replace_by_key() works the same as memc_replace() except it has as its first argument a master server key which allows you to group stored values by server. The arguments following the master key argument are the same as for memc_replace() — just shifted in order.

The syntax for memc_replace() and memc_replace_by_key() is:

```
memc_replace('key', value);
memc_replace('key', value, expiration);
memc_replace_by_key('master key', 'key', value);
memc_replace_by_key('master key', 'key', value, expiration);
```

The example that follows shows the retrieval of a previously stored value that is then replaced:

```
mysql> select memc_get('key2');
```

| memc_get('key2') |
|---|
| before value |

```
mysql> select memc_replace('key2', 'replaced value');
```

| memc_replace('key2', 'replaced value') |
|---|
| 0 |

```
mysql> select memc_get('key2');
```

| memc_get('key2') |
|---|
| replaced value |

The next example shows how to replace a value that doesn’t exist and returns an error code of 14:

```
mysql> select memc_replace('doesntexist', 'abcdefg');
```

| memc_replace('doesntexist', 'abcdefg') |
|---|
| 14 |

## memc_cas

If you recall from Chapter 4, CAS stands for check and set. The Memcached Functions for MySQL also have CAS UDFs. The function memc_cas() sets a value if the cas value is the same as the cas value on the server itself.

The syntax for memc_cas() and memc_cas_by_key() is:

```
memc_cas('key', value, cas);
memc_cas('key', value, cas, expiration);
memc_cas_by_key('master_key', 'key', value, cas, expiration);
```

This functionality is still experimental and you have to enable it by setting the behavior MEMCACHED_BEHAVIOR_SUPPORT_CAS.

```
mysql> select memc_servers_behavior_set('MEMCACHED_BEHAVIOR_SUPPORT_CAS', 1);
```

| memc_servers_behavior_set('MEMCACHED_BEHAVIOR_SUPPORT_CAS', 1) |
|---|
| 0 |

## memc_prepend

The function memc_prepend() prepends value to the beginning of an existing stored value, stored by key. The value being prepended can be either numeric or a string if the value already stored is a string. You cannot prepend anything to an existing stored numeric value or it results in that value being set to NULL. The expiration argument is optional and sets the expiration time in seconds.

The function memc_prepend_by_key() works the same as memc_prepend except the first argument is a master server key to which the value is prepended, all other values working the same.

The syntax for memc_prepend() and memc_prepend_by_key() is:

```
memc_prepend('key', value);
memc_prepend('key', value, expiration);
memc_prepend_by_key('master key', 'key', value);
memc_prepend_by_key('master key', 'key', value, expiration);
```

The example that follows shows a value initially set to ' this is some text' but that has 'this will be prepended.. ' prepended to it using memc_prepend():

```
mysql> select memc_set('abc', ' this is some text');
```

| memc_set('abc', ' this is some text') |
|---|
| 1 |

```
mysql> select memc_get('abc');
```

| memc_get('abc') |
|---|
| this is some text |

```
mysql> select memc_prepend('abc', 'hither... ');
```

| memc_prepend('abc', 'hither... ') |
|---|
| 1 |

```
mysql> select memc_get('abc');
```

| memc_get('abc') |
|---|
| hither... this is some text |

## memc_append

The function memc_append() appends the argument value to the existing value stored as key. The value being appended can be either numeric or a string if the value already stored is a string. You

*cannot* append anything to an existing stored numeric value or it will result in that value being set to NULL. The argument *expiration* is optional and specifies the expiration time in number of seconds.

The function `memc_append_by_key()` works the same as `memc_append()` except the first argument is a master key that the value was stored as.

The syntax for `memc_append()` and `memc_append_by_key()` is:

```
memc_append('key', value);
memc_append('key', value, expiration);
memc_append_by_key('master key', 'key', value);
memc_append_by_key('master key', 'key', value, expiration);
```

An example showing what `memc_append()` does is shown in the following code. First an existing value has text appended to it, and a subsequent `memc_get()` retrieves the value, verifying that it had the text appended by `memc_append()`

```
mysql> select memc_append('abc', ' ...tither');
```

| memc_append('abc', ' ...tither') |
|---|
| 1 |

```
mysql> select memc_get('abc');
```

| memc_get('abc') |
|---|
| hither... this is some text ...tither |

## memc_delete

The function `memc_delete()` deletes the value stored as *key* from memcached. The return value is zero if the value is deleted and non-zero value if not.

Just as with any of the other `*_by_key()` functions, `memc_delete_by_key()` works the same as `memc_delete()` except it has the master key representing the server where the object is stored as its first argument.

The syntax for `memc_delete()` and `memc_delete_by_key()` is:

```
memc_delete('key');

memc_delete_by_key('master key', 'key');
```

```
mysql> select memc_delete('foo');
```

| memc_delete('foo') |
|---|
| 1 |
