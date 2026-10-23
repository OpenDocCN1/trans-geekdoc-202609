It’s possible to encode a map which has integer values as the map keys. The integers will be automatically converted to strings in the resulting JSON (because the keys in a JSON object must always be strings). For example, the following map:

```
m := map[int]string{
  123: "foo",
  456_000: "bar",
}
```

Will encode to the JSON:

```
{"123":"foo","456000":"bar"}
```

In addition, map keys that implement the encoding.TextMarshaler interface are also supported. This means that you can also use time.Time and net.IP values as map keys out-of-the-box. For example, the following map:

```
t1 := time.Now()
t2 := t1.Add(24 * time.Hour)

m := map[time.Time]string{
  t1: "foo",
  t2: "bar",
}
```