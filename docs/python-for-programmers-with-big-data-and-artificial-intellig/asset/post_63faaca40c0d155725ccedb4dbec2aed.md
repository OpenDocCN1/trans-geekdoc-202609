
### 16.5.5 Implementing the Mapper

In this section, you’ll create a mapper script that takes lines of text as input from Hadoop and maps them to key-value pairs in which each key is a word, and its corresponding value is 1. The mapper sees each word individually so, as far as it is concerned, there’s only one of each word. In the next section, the reducer will summarize these key-value pairs by key, reducing the counts to a single count for each key. By default, Hadoop expects the mapper’s output and the reducer’s input and output to be in the form of key-value pairs separated by a tab.

In the mapper script (length_mapper.py), the notation #! in line 1 tells Hadoop to execute the Python code using python3, rather than the default Python 2 installation. This line must come before all other comments and code in the file. At the time of this writing, Python 2.7.12 and Python 3.5.2 were installed. Note that because the cluster does not have Python 3.6 or higher, you cannot use f-strings in your code.

click here to view code image

```python
#!/usr/bin/env python3
# length_mapper.py
"""Maps lines of text to key-value pairs of word lengths and 1."""
import sys

def tokenize_input():
    """Split each line of standard input into a list of strings."""
    for line in sys.stdin:
        yield line.split()

# read each line in the standard input and for every word
# produce a key-value pair containing the word, a tab and 1
for line in tokenize_input():
    for word in line:
        print(str(len(word)) + '\t1')
```

Generator function tokenize_input (lines 6–9) reads lines of text from the standard input stream and for each returns a list of strings. For this example, we are not removing punctuation or stop words as we did in the “Natural Language Processing” chapter.

When Hadoop executes the script, lines 13–15 iterate through the lists of strings from tokenize_input. For each list (line) and for every string (word) in that list, line 15 outputs a key-value pair with the word’s length as the key, a tab (\t) and the value 1, indicating that there is one word (so far) of that length. Of course, there probably are many words of that length. The MapReduce algorithm’s reduction step will summarize these key-value pairs, reducing all those with the same key to a single key-value pair with the total count.

### 16.5.6 Implementing the Reducer

In the reducer script (length_reducer.py), function tokenize_input (lines 8–11) is a generator function that reads and splits the key-value pairs produced by the mapper. Again, the MapReduce algorithm supplies the standard input. For each line, tokenize_input strips any leading or trailing whitespace (such as the terminating newline) and yields a list containing the key and a value.

click here to view code image

```python
#!/usr/bin/env python3
# length_reducer.py
"""Counts the number of words with each length."""
import sys
from itertools import groupby
from operator import itemgetter

def tokenize_input():
    """Split each line of standard input into a key and a value."""
    for line in sys.stdin:
        yield line.strip().split('\t')

# produce key-value pairs of word lengths and counts separated by tabs
for word_length, group in groupby(tokenize_input(), itemgetter(0)):
    try:
        total = sum(int(count) for word_length, count in group)
        print(word_length + '\t' + str(total))
    except ValueError:
        pass # ignore word if its count was not an integer
```

When the MapReduce algorithm executes this reducer, lines 14–19 use the `groupby` function from the `itertools module` to group all word lengths of the same value:

- The first argument calls `tokenize_input` to get the lists representing the key–value pairs.
- The second argument indicates that the key–value pairs should be grouped based on the element at index 0 in each list—that is the key.

Line 16 totals all the counts for a given key. Line 17 outputs a new key–value pair consisting of the word and its total. The MapReduce algorithm takes all the final word-count outputs and writes them to a file in HDFS—the Hadoop file system.

### 16.5.7 Preparing to Run the MapReduce Example

Next, you’ll upload files to the cluster so you can execute the example. In a Command Prompt, Terminal or shell, change to the folder containing your mapper and reducer scripts and the `RomeoAndJuliet.txt` file. We assume all three are in this chapter’s `ch16` examples folder, so be sure to copy your `RomeoAndJuliet.txt` file to this folder first.

### Copying the Script Files to the HDInsight Hadoop Cluster

Enter the following command to upload the files. Be sure to replace `YourClusterName` with the cluster name you specified when setting up the Hadoop cluster and press `Enter` only after you’ve typed the entire command. The colon in the following command is required and indicates that you’ll supply your cluster password when prompted. At that prompt, type the password you specified when setting up the cluster, then press `Enter`:

click here to view code image

```
scp length_mapper.py length_reducer.py RomeoAndJuliet.txt sshuser@YourClusterName-ssh.azurehdinsight.net:
```

The first time you do this, you’ll be asked for security reasons to confirm that you trust the target host (that is, Microsoft Azure).

### Copying RomeoAndJuliet into the Hadoop File System

For Hadoop to read the contents of RomeoAndJuliet.txt and supply the lines of text to your mapper, you must first copy the file into Hadoop's file system. First, you must use ssh to log into your cluster and access its command line. In a Command Prompt, Terminal or shell, execute the following command. Be sure to replace YourClusterName with your cluster name. Again, you'll be prompted for your cluster password:

> Windows users: If ssh does not work for you, install and enable it as described at https://blogs.msdn.microsoft.com/powershell/2017/12/15/using-the-openssh-beta-in-windows-10-fall-creators-update-and-windows-server-709/. After completing the installation, log out and log back in or restart your system to enable ssh.

click here to view code image

```
ssh sshuser@YourClusterName-ssh.azurehdinsight.net
```

For this example, we'll use the following Hadoop command to copy the text file into the already existing folder /examples/data that the cluster provides for use with Microsoft's Azure Hadoop tutorials. Again, press Enter only when you've typed the entire command:

click here to view code image

```
hadoop fs -copyFromLocal RomeoAndJuliet.txt /example/data/RomeoAndJuliet.txt
```

### 16.5.8 Running the MapReduce Job

Now you can run the MapReduce job for RomeoAndJuliet.txt on your cluster by executing the following command. For your convenience, we provided the text of this command in the file yarn.txt with this example, so you can copy and paste it. We reformatted the command here for readability:

click here to view code image

```
yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar
-D mapred.output.key.comparator.class=org.apache.hadoop.mapred.lib.KeyFieldBasedComparator
-D mapred.text.key.comparator.options=-n
-files length_mapper.py,length_reducer.py
-mapper length_mapper.py
-reducer length_reducer.py
-input /example/data/RomeoAndJuliet.txt
-output /example/wordlengthsoutput
```

The yarn command invokes the Hadoop's YARN ("yet another resource negotiator") tool to manage and coordinate access to the Hadoop resources the MapReduce task uses. The file hadoop-streaming.jar contains the Hadoop streaming utility that allows you to use Python to implement the mapper and reducer. The two -D options set Hadoop properties that enable it to sort the final key-value pairs by key (KeyFieldBasedComparator) in descending order numerically (-n; the minus indicates descending order) rather than alphabetically. The other command-line arguments are:

- -files—A comma-separated list of file names. Hadoop copies these files to every node in the cluster so they can be executed locally on each node.
- -mapper—The name of the mapper's script file.
- -reducer—The name of the reducer's script file
- -input—The file or directory of files to supply as input to the mapper.
- -output—The HDFS directory in which the output will be written. If this folder already exists, an error will occur.

The following output shows some of the feedback that Hadoop produces as the MapReduce job executes. We replaced chunks of the output with to save space and bolded several lines of interest including:

- The total number of “input paths to process”—the 1 source of input in this example is the RomeoAndJuliet.txt file.
- The “number of splits”—2 in this example, based on the number of worker nodes in our cluster.
- The percentage completion information.
- File System Counters, which include the numbers of bytes read and written.
- Job Counters, which show the number of mapping and reduction tasks used and various timing information.
- Map-Reduce Framework, which shows various information about the steps performed.

click here to view code image

```
packageJobJar: [] [/usr/hdp/2.6.5.3004-13/hadoop-mapreduce/hadoop-streaming-2...
...
18/12/05 16:46:25 INFO mapred.FileInputFormat: Total input paths to process :
18/12/05 16:46:26 INFO mapreduce.JobSubmitter: number of splits:2
...
18/12/05 16:46:26 INFO mapreduce.Job: The url to track the job: http://hn0-p...
...
18/12/05 16:46:35 INFO mapreduce.Job: map 0% reduce 0%
18/12/05 16:46:43 INFO mapreduce.Job: map 50% reduce 0%
18/12/05 16:46:44 INFO mapreduce.Job: map 100% reduce 0%
18/12/05 16:46:48 INFO mapreduce.Job: map 100% reduce 100%
18/12/05 16:46:50 INFO mapreduce.Job: Job job_1543953844228_0025 completed suc
18/12/05 16:46:50 INFO mapreduce.Job: Counters: 49
 File System Counters
 FILE: Number of bytes read=156411
 FILE: Number of bytes written=813764
...
 Job Counters
```
