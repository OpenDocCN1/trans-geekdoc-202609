# Mastering Classification Algorithms for Machine Learning

```
returnValue[key] = segment.header[attribute]
```

```
return returnValue
```

ExtractSectionDetails() extracts all the information from all sections in an ELF File.

```
from elftools.elf.elffile import ELFFile
```

```
def ExtractSectionDetails(elffile):

    returnValue = { }

    # ELF Files with malware contain Section Names which have been
    # tampered.

    # If such a Section Name is found, then we store the tampered
    Section Name as a feature.

    # To be able to store these in unique attributes, we set a counter
    across the file.
    malwareSectionNameCounter = 0

    # Check if any section information exists in the file
    # If it does, collect all the information of all the attributes in
    all the sections
    if(elffile.num_sections() > 0):
        # Iterate through all the sections and gather the attributes.
        for section in elffile.iter_sections():
            # Every section has a name.
            # Section Name to be a valid ASCII string.
            # If the Section Name contains non-ASCII characters, then
            the file has been tampered.
            if all((ord(char) > 32 and ord(char) < 128) for char in
            section.name):
```