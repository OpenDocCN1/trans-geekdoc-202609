# Parallelisation

```
// t -- reference to on-disk partition table name
// o -- operation: append (,) or assign (:)
// n -- new data table to append - data, not a reference, and already
// enumerated
{d;t;o;d;x;o t];d..q.Par(d;p;t;r;o];'!r+n];
[@;d;d;f&#-f;r];
[@;q.qasc[f] d;f;#pm];
};
```

Here we use k language and invoke it by using k.
We enumerate our data table and iterate over dates calling .quant.io .dpAppendNew in parallel using pooch

```
new: enlist 'code'time'price'volume'mktflag comments ! ( 'NEW; .z;t; 1f; ih
E; ""
enum; Q.en[::];
[ new, dt];quant.io.dpfsAppendNew[; dt; code;'trd;; new] []
enum; peach date
```

```
'trd'trd'
```

Reloading the hdb we can see that the new values have been applied:

```
\1
trd
```

| date | time | price | volume | mktflag | comments |
|---|---|---|---|---|---||
| 2016.04.07 | CLM16 | 10:20:00.329 | 38.3 | 4 | E | "NYMEX/CME Group trade" |
| 2016.04.07 | CLM16 | 13:00:00.128 | 38.4 | 3 | E | "NYMEX/CME Group trade" |
| 2016.04.07 | CLM16 | 12:00:00.555 | 120.5 | 6 | E | " |
| 2016.04.07 | CLM16 | 13:37:02.160 | 184.4 | 2 | E | " |
| 2016.04.07 | CLM16 | 14:35:01.241 | 124.1 | 2 | E | " |
| 2016.04.07 | NEW | 06:57:06.504 | 4 | 1 | E | " |
| 2016.04.08 | VXK16 | 13:12:00.918 | 188.85 | 5 | E | " |
| 2016.04.08 | CLM16 | 12:00:02.227 | 40.6 | 3 | E | "NYMEX/CME Group trade" |
| 2016.04.08 | CLM16 | 15:20:02.000 | 40.8 | 3 | E | "NYMEX/CME Group trade" |
| 2016.04.08 | NEW | 10:13:01.048 | 240 | 3 | E | " |
| 2016.04.08 | NEW | 06:57:06.591 | 4 | 1 | E | " |
| 2016.04.08 | VXK16 | 11:34:43.517 | 185.53 | 1 | E | "Transaction represents |
| 2016.04.08 | VXK16 | 12:16:11.444 | 184.4 | 2 | E | "Transaction represents |
| 2016.04.08 | VXK16 | 12:45:33.130 | 189.49 | 1 | E | "Transaction represents |
| 2016.04.11 | CLM16 | 11:00:00.185 | 41.3 | 2 | E | " |
| 2016.04.11 | CLM16 | 16:00:00.044 | 1257.9 | 1 | E | "NYMEX/CME Group trade" |
| 2016.04.11 | CLM16 | 16:28:34.311 | 1258.7 | 1 | E | " |
| 2016.04.11 | NEW | 06:57:06.585 | 4 | 1 | E | " |
| 2016.04.11 | VXK16 | 14:00:00.829 | 183.35 | 1 | E | " |
| 2016.04.11 | VXK16 | 15:14:58.775 | 190.05 | 2 | E | " |