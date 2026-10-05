# Splayed and Partitioned Tables

- 2016.04.11
- trd
- .d
- :
- volume

In the direction that we have specified to .Q.dpft, we have one subdirectory per each partition (2016.04.07, 2016.04.08, and 2016.04.11). Inside those directories, we have a subdirectory whose name is that of the table that we provided to .Q.dpft as an argument: trd. Inside trd, we have the same files as we encountered when splaying tables, with the exception of sym, which now resides two levels above. Before, the file enumerates the columns of type symbol. Notice that we didn't have to call .Q.en explicitly this time.

We can add another table to the mydb directory. Suppose that we have the following (again, highly coveted) table of quotes:

+   LISTING 6.1 An example table of quotes
quotes ([ code:symbol(); date:date(); time:time(); bidprice:float($); bidesize:short($); askprice:float($); asksize:short($); mktflag:symbol());
quotes upset (
`CM616, 2016.04.07; 10:15:00.010; 38.34 ; 86h ; 3h ; 'E` );
`CM616, 2016.04.07; 11:02:16.663; 1241.4 ; 1241.5 ; 1h ; 'E` );
`CM616, 2016.04.07; 12:05:20.303; 38.12 ; 7h ; 38.13 ; 13h ; 'E` );
`CM616, 2016.04.07; 13:22:20.005; 38.11 ; 38.12 ; 8h ; 'E` );
`CM616, 2016.04.07; 13:50:00.205; 1238.6 ; 8h ; 7h ; 'E` );
`CM616, 2016.04.07; 15:20:02.224; 1240.9 ; 38.53 ; 18h ; 'E` );
`CM616, 2016.04.08; 15:00:05.051; 38.52 ; 6h ; 1241f ; 1h ; 'E` );
`CM616, 2016.04.08; 10:53:00.002; 40.83 ; 40.84 ; 66h ; 'E` );
`CM616, 2016.04.08; 13:56:30.070; 40.54 ; 38.56 ; 58h ; 'E` );
`CM616, 2016.04.08; 15:20:02.000; 40.77 ; 26h ; 44h ; 'E` );
`CM616, 2016.04.08; 15:21:43.786; 40.76 ; 3h ; 28h ; 'E` );
 )

We run the following

```
{
qt select from quotes where date=x;
Q.dpft[mydb;quotes];
delete qt from _;
deach distinct quotes["date]
```

and obtain the following directory structure:

```
-C:/data/mydb
- 2016.04.07
- trd
```