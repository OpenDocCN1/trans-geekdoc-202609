# Debugging q

a
--
11
22
33

> 'mismatch – When two tables are being joined with an upsert (or a comma-join), and the columns between the two differ

```
t1:([[a:1 2;b:3 4)]
t2:([[c:10 20 30)]
```

'mismatch
[0] t1,t2

t1 upsert t2

'mismatch
[0] t1 upsert t2

+   'constants – We have declared too many constants, more than 96. This may frequently happen when we use long functions and define many variables and/or constants. This is q's way of telling us to refactor our code, i.e. to be modular: keep your functions small and with well-defined responsibilities.
'domain – This error occurs when we evaluate function outside of the natural domain; for example, we want to create an increasing sequence of integers starting at @ and running to a negative number.
'from – This error appears when we use one of the sql commands and forget (or misspell) the statement or omit the table name.
'ndate – This error can be encountered when we work on a server which has protection against writing or updating tables. This is frequently the case within a working environment, where the database is protected against write access, i.e. the historical data cannot be changed by intention or by mistake.
'nyi – "not yet implemented". One usually gets this when the command looks meaningful but q is not able to execute it. If we try to do what we intended to do in a slightly different way, we may usually find a coding solution.
'OS – Operating system error. One may encounter this if the underlying system command produces an error during its execution. For example, if we need to copy the files from a different server, we may use: "system"wget:http://sourceofourData/data.csv" – Such an evaluation may proceed properly; however, we still get it.
'params – This error is encountered when a function with more than eight parameters is constructed. The natural remedy to this error is to wrap parameters into a dictionary and pass the parameters through the dictionary. This approach is chosen throughout this book. It gives us flexibility in terms of the dimension of parameters.