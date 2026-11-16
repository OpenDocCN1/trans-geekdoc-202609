
For readability, we opened the file objects (snippets [1] and [2]), then specified their variable names in the first line of snippet [3]. This `with` statement manages two resource objects, specified in a comma-separated list after `with`. The `for` statement unpacks each record into `account`, `name` and `balance`. If the `account` is not '300', we write `record` (which contains a newline) to `temp_file`. Otherwise, we assemble the new record containing 'Williams' in place of 'White' and write it to the file. After snippet [3], `temp_file.txt` contains:

```
100 Jones 24.98
200 Doe 345.67
300 Williams 0.00
400 Stone -42.16
500 Rich 224.62
```

## os Module File-Processing Functions

At this point, we have the old `accounts.txt` file and the new `temp_file.txt`. To complete the update, let’s delete the old `accounts.txt` file, then rename `temp_file.txt` as `accounts.txt`. The `os` module 4 provides functions for interacting with the operating system, including several that manipulate your system’s files and directories. Now that we’ve created the temporary file, let’s use the `remove` function 5 to delete the original file:

4 https://docs.python.org/3/library/os.html.

5 Use `remove` with caution; it does not warn you that you're *permanently* deleting the file.

![](img/34b7fc2f1ee27beb73bca14927d42340_354_0.png)

```
In [4]: import os

In [5]: os.remove('accounts.txt')
```

Next, let’s use the `rename` function to rename the temporary file as 'accounts.txt':

![](img/34b7fc2f1ee27beb73bca14927d42340_354_1.png)

```
In [6]: os.rename('temp_file.txt', 'accounts.txt')
```

## 9.5 SERIALIZATION WITH JSON

Many libraries we’ll use to interact with cloud-based services, such as Twitter, IBM Watson and others, communicate with your applications via JSON objects. JSON (JavaScript Object Notation) is a text-based, human-and-computer-readable, data-interchange format used to represent objects as collections of name–value pairs. JSON can even represent objects of custom classes like those you’ll build in the next chapter.

JSON has become the preferred data format for transmitting objects across platforms. This is especially true for invoking cloud-based web services, which are functions and methods that you call over the Internet. You’ll become proficient at working with JSON data. In the “Data Mining Twitter” chapter, you’ll access JSON objects containing tweets and their metadata. In the “IBM Watson and Cognitive Computing” chapter, you’ll access data in the JSON responses returned by Watson services. In the “Big Data: Hadoop, Spark, NoSQL and IoT” chapter, we’ll store JSON tweet objects that we obtain from Twitter in MongoDB, a popular NoSQL database. In that chapter, we’ll also work with other web services that send and receive data as JSON objects.

### JSON Data Format

JSON objects are similar to Python dictionaries. Each JSON object contains a comma-separated list of property names and values, in curly braces. For example, the following key–value pairs might represent a client record:

```
{"account": 100, "name": "Jones", "balance": 24.98}
```

JSON also supports arrays which, like Python lists, are comma-separated values in square brackets. For example, the following is an acceptable JSON array of numbers:

```
[100, 200, 300]
```

Values in JSON objects and arrays can be:

- strings in double quotes (like "Jones"),
- numbers (like 100 or 24.98),
- JSON Boolean values (represented as `true` or `false` in JSON),
- `null` (to represent no value, like `None` in Python),
- arrays (like `[100, 200, 300]`), and
- other JSON objects.

### Python Standard Library Module json

The **json** module enables you to convert objects to JSON (JavaScript Object Notation) text format. This is known as **serializing** the data. Consider the following dictionary, which contains one key–value pair consisting of the key 'accounts' with its associated value being a list of dictionaries representing two accounts. Each account dictionary contains three key–value pairs for the account number, name and balance:

click here to view code image

```
In [1]: accounts_dict = {'accounts': [
    ...:     {'account': 100, 'name': 'Jones', 'balance': 24.98},
    ...:     {'account': 200, 'name': 'Doe', 'balance': 345.67}]}
```

### Serializing an Object to JSON

Let’s write that object in JSON format to a file:

click here to view code image

```
In [2]: import json

In [3]: with open('accounts.json', 'w') as accounts:
    ...:     json.dump(accounts_dict, accounts)
```

Snippet [3] opens the file `accounts.json` and uses the **json** module’s **dump** function to serialize the dictionary `accounts_dict` into the file. The resulting file contains the following text, which we reformatted slightly for readability:

click here to view code image

```
{"accounts": [
{"account": 100, "name": "Jones", "balance": 24.98},
{"account": 200, "name": "Doe", "balance": 345.67}]}
```

Note that JSON delimits strings with double-quote characters.

### Deserializing the JSON Text

The json module’s load function reads the entire JSON contents of its file object argument and converts the JSON into a Python object. This is known as deserializing the data. Let’s reconstruct the original Python object from this JSON text:

click here to view code image

```
In [4]: with open('accounts.json', 'r') as accounts:
    ...:     accounts_json = json.load(accounts)
    ...:
    ...:
```

We can now interact with the loaded object. For example, we can display the dictionary:

click here to view code image

```
In [5]: accounts_json
Out[5]:
{'accounts': [{'account': 100, 'name': 'Jones', 'balance': 24.98],
{'account': 200, 'name': 'Doe', 'balance': 345.67}]}
```

As you’d expect, you can access the dictionary’s contents. Let’s get the list of dictionaries associated with the 'accounts' key:

click here to view code image

```
In [6]: accounts_json['accounts']
Out[6]:
[{'account': 100, 'name': 'Jones', 'balance': 24.98],
{'account': 200, 'name': 'Doe', 'balance': 345.67}]}
```

Now, let’s get the individual account dictionaries:

click here to view code image

```
In [7]: accounts_json['accounts'][0]
Out[7]: {'account': 100, 'name': 'Jones', 'balance': 24.98}
In [8]: accounts_json['accounts'][1]
Out[8]: {'account': 200, 'name': 'Doe', 'balance': 345.67}
```

Though we did not do so here, you can modify the dictionary as well. For example, you could add accounts to or remove accounts from the list, then write the dictionary back into the JSON file.

### Displaying the JSON Text

The json module’s dumps function (dumps is short for “dump string”) returns a Python string representation of an object in JSON format. Using dumps with load, you can read the JSON from the file and display it in a nicely indented format—sometimes called “pretty printing” the JSON. When the dumps function call includes the indent keyword argument, the string contains newline characters and indentation for pretty printing—you also can use indent with the dump function when writing to a file:

click here to view code image

```
In [9]: with open('accounts.json', 'r') as accounts:
    ...:     print(json.dumps(json.load(accounts), indent=4))
    ...:
{
    "accounts": [
        {
            "account": 100,
            "name": "Jones",
            "balance": 24.98
        },
        {
            "account": 200,
            "name": "Doe",
            "balance": 345.67
        }
    ]
}
```

## 9.6 FOCUS ON SECURITY: PICKLE SERIALIZATION AND DESERIALIZATION

The Python Standard Library’s pickle module can serialize objects into a Python-specific data format. Caution: The Python documentation provides the following warnings about pickle:

- “Pickle files can be hacked. If you receive a raw pickle file over the network, don’t trust it! It could have malicious code in it, that would run arbitrary Python when you try to de-pickle it. However, if you are doing your own pickle writing and reading, you're safe (provided no one else has access to the pickle file, of course.) 6

6 https://wiki.python.org/moin/UsingPickle.

- “Pickle is a protocol which allows the serialization of arbitrarily complex Python objects. As such, it is specific to Python and cannot be used to communicate with applications written in other languages. It is also insecure by default: deserializing pickle data coming from an untrusted source can execute arbitrary code, if the data was crafted by a skilled attacker.” 7

7 https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files.

We do not recommend using pickle, but it's been used for many years, so you're likely to encounter it in legacy code—old code that's often no longer supported.

## 9.7 ADDITIONAL NOTES REGARDING FILES

The following table summarizes the various file-open modes for text files, including the modes for reading and writing we’ve introduced. The writing and appending modes create the file if it does not exist. The reading modes raise a FileNotFoundError if the file does not exist. Each text-file mode has a corresponding binary-file mode specified with b, as in 'rb' or 'wb+'. You’d use these modes, for example, if you were reading or writing binary files, such as images, audio, video, compressed ZIP files and many other popular custom file formats.

| Mode | Description |
|---|---|
| 'r' | Open a text file for reading. This is the default if you do not specify the file-open mode when you call open. |
| 'w' | Open a text file for writing. Existing file contents are deleted. |
