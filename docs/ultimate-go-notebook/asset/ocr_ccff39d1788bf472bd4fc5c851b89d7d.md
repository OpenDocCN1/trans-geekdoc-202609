# 2.7 Padding and Alignment

How much memory is allocated for a value of type example?

Listing 2.9

```
type example struct {
  flag bool
  counter int16
  pi float32
}
```

A bool is 1 byte, int16 is 2 bytes, and float32 is 4 bytes. Add that all together and I get 7 bytes. However, the actual answer is 8 bytes. Why, because there is a padding value sitting between the flag and counter fields for the reason of alignment.

Figure 2.1

| Flag | Counter | Pi |
|---|---|---|
| 0 | 2 | 8 |

The idea of alignment is to allow the hardware to read memory more efficiently by placing memory on specific alignment boundaries. The compiler takes care of the alignment boundary mechanics so I don't have to.

Depending on the size of a particular field and its placement in the struct, Go determines the padding I need.

Listing 2.10

```
type example2 struct {
  flag bool
  counter int16
  flag2 bool
  pi float32
}
```

In this example, I’ve added a new field called flag2 between the counter and pi fields. This causes more padding inside the struct.