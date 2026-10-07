```
except:
validELFFile = False
```

```
finally:
elfffile.close()
```

```
except:
pass
```

return (returnValue, validELFFile, hasFileHeader, hasProgramHeader, hasSections)

The function ExtractFile() is used to extract all the information from the File Header of an ELF File.

```
from elftools.elf.elffile import ELFFile
```

```
def ExtractFileHeader(elffile):
returnValue = {} Dictionary to hold the unique attributes of the header
```

+   # The header information can be obtained as a dictionary.

+   # However, there are some dictionaries inside this dictionary.

+   # So, we create a flat structure taking out all the unique attributes and forming a dictionary.

for key, value in elffile.header.items():

+   # If the value for the key is a dictionary, then loop through all the attributes of this dictionary to collect the features.

+   # The approach is simplistic as I do not go for a recursive function as it is known that there can be only one additional level of the dictionary.

```
for insideKey, insideValue in value.items():
```