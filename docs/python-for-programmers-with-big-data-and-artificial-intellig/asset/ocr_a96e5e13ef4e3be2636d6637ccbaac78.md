ou try to de-pickle it. However, if you are doing your own pickle writing and reading, you're safe (provided no one else has access to the pickle file, of course.) 6

6 https://wiki.python.org/moin/UsingPickle.

+   - “Pickle is a protocol which allows the serialization of arbitrarily complex Python objects. As such, it is specific to Python and cannot be used to communicate with applications written in other languages. It is also insecure by default: deserializing pickle data coming from an untrusted source can execute arbitrary code, if the data was crafted by a skilled attacker.” 7

7 https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files.

We do not recommend using pickle, but it's been used for many years, so you're likely to encounter it in legacy code—old code that's often no longer supported.

# 9.7 ADDITIONAL NOTES REGARDING FILES

The following table summarizes the various file-open modes for text files, including the modes for reading and writing we’ve introduced. The writing and appending modes create the file if it does not exist. The reading modes raise a FileNotFoundError if the file does not exist. Each text-file mode has a corresponding binary-file mode specified with b, as in 'rb' or 'wb+'. You’d use these modes, for example, if you were reading or writing binary files, such as images, audio, video, compressed ZIP files and many other popular custom file formats.

| Mode | Description |
|---|---|
| 'r' | Open a text file for reading. This is the default if you do not specify the file-open mode when you call open. |
| 'w' | Open a text file for writing. Existing file contents are deleted. |