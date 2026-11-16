```
Launched map tasks=2
Launched reduce tasks=1

...

Map-Reduce Framework
Map input records=5260
Map output records=29596
Map output bytes=104493
Map output materialized bytes=156417
Input split bytes=346
Combine input records=0
Combine output records=0
Reduce input groups=19
Reduce shuffle bytes=156417
Reduce input records=25956
Reduce output records=19
Spilled Records=51912
Shuffled Maps =2
Failed Shuffles=0
Merged Map outputs=2
GC time elapsed (ms)=193
CPU time spent (ms)=4440
Physical memory (bytes) snapshot=1942798336
Virtual memory (bytes) snapshot=8463282176
Total committed heap usage (bytes)=3177185280

...
18/12/05 16:46:50 INFO streaming.StreamJob: Output directory: /example/wordler
```

# iewing the Word Counts

Hadoop MapReduce saves its output into HDFS, so to see the actual word counts you must look at the file in HDFS within the cluster by executing the following command:

lick here to view code image

```
hdfs dfs -text /example/wordlengthsoutput/part-00000
```

Here are the results of the preceding command:

lick here to view code image

```
8/12/05 16:47:19 INFO lzo.GPLNativeCodeLoader: Loaded native gpl library
18/12/05 16:47:19 INFO lzo.LzoCodec: Successfully loaded & initialized native-
1 1140
2 3869
3 4699
4 5651
5 3668
6 2719
7 1624
8 1062
9 855
10 317
11 189
12 95
13 35
14 13
15 9
16 6
17 3
18 1
23 1
```