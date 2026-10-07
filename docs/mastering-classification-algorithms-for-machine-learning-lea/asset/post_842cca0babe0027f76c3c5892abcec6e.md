
# Section information in the ELF File.

There are many sections in the ELF File. Each Section is for a specific type of information. The types of sections can be program data, symbol table, string table, symbol hash table, dynamic linking information, dynamic linker symbol table, array of constructors, array of destructors, etc.

For each section, there is information regarding whether the section is writable or executable, may be merged, contains null-terminated strings, etc.

Then, there is information regarding the various addresses for the different information.

So, this is a section where malware makers can alter various information.

# About the data

The dataset contains types of files, as provided in Table 7.1:

| File type | Number of files |
|---|---|
| Benign | 2,315 |
| Malicious | Backdoor | 744 |
| | Botnet | 782 |
| | DDOS | 799 |
| | Trojan | 508 |
| | Virus | 595 |
| TOTAL | 3,428 |

Table 7.1: Distribution of Input ELF Files

So, the data set contained 2,315 benign ELF Files and 3,428 malicious ELF files. We see that there are a reasonable number of files in each category. Based on this data, 90% of the data will be used as the training and 10% as the test sets. The distribution of files used for training and testing the model is given in Table 7.2. To create training and test datasets, files are picked at random.

| File type | Training set | Test set |
| --- | --- | --- |
| Benign | 2,078 | 237 |
| Backdoor | 676 | 68 |
| Botnet | 713 | 69 |
| DDOS | 725 | 74 |
| Malicious Trojan | 461 | 47 |
| Virus | 539 | 56 |
| TOTAL | 3,114 | 314 |

Table 7.2: Distribution of ELF Files after creating the Training Set and Test Set

# Building and testing the model

Before we build the model for malware detection from ELF Files, we need to be able to read the ELF Files and extract features based on which the model will be made. To read ELF Files using Python programming, we can use the library pyelftools. We will have to install this package on our machine before we can proceed. The following code installs the pyelftools package:

```python
!python3 -m pip install pyelftools
```

The following is the code for declaring the constants we will use to build this model. The use of these constants will become clear as we discuss the rest of the code. Avoid using literal values in my programs as much as possible because using literal values makes maintaining the program difficult.

# Constants

```
EMPTY_SECTION_NAME_SUBSTITUTE = "S"
FILE_NAME_COLUMN_NAME = "FileName"
FILE_TYPE_COLUMN_NAME = "FileType"
NUMERIC_COLUMN_IDENTIFIER = "N"
MALWARE_SECTION_NAME_PREFIX = "M"

BENIGN_FILE = 0
BACKDOOR_FILE = 1
BOTNET_FILE = 2
DDOS_FILE = 3

TROJAN_FILE = 4

VIRUS_FILE = 5
```

# Extracting data from ELF files

We will write a series of functions to extract information from the ELF Files. The first function extractInformationFromDirectory() is used for extracting details of all the ELF Files stored in a directory. Note that we have six types of files, 1 type of file is the benign ELF file, and the other five are the malicious ELF files containing different types of malwares. So, the strategy is to keep all the files of one type in a separate directory, and we will read the files from this directory, and based on what type of files the directory contains, we will label the records accordingly.

This function calls the function isELFFile(), which detects whether a file provided to this function is a valid ELF file.

This function calls the function ExtractFileDetails(), which extracts the details from a single ELF file.

```python
import glob
```

def extractInformationFromDirectory(inputDirectory):
    # Declare Counters
    NumberOfValidFiles = 0
    NumberOfInvalidFiles = 0
    NumberOfFilesNoFileHeader = 0
    NumberOfFilesNoProgramHeader = 0
    NumberOfFilesNoSections = 0

    # Create an Empty List to hold all features of all files
    returnValue = []

    # Loop through all the files in Input Directory
    for file in glob.glob(inputDirectory):
        # Create an empty Dictionary
        oneFileFeatures = {}
        try:
            # Read the file and extract the features
            validFlag, hasFileHeader, hasProgramHeader, hasSections = ExtractFileDetails(file)
            if validFlag and len(oneFileFeatures.keys()) > 0:
                getNumberOfValidFiles += 1
                # Add the File Features to the main Dictionary
                oneFileFeatures.update(fileFeatures)
                # Add the entry to the return value
                returnValue.append(oneFileFeatures)
            else:
                if hasFileHeader == False:
                    getNumberOfFilesNoFileHeader += 1
                else:
                    if hasProgramHeader == False:
                        NumberOfFilesNoProgramHeader += 1
                    else:
                        if hasSections == False:
                            NumberOfFilesNoSections += 1
                        else:
                            getNumberOfInvalidFiles += 1
        except:
            # Check if the file is a valid ELF
            if isELFFile(file):
                pass
            else:
                getNumberOfInvalidFiles += 1
    return (returnValue, getNumberOfValidFiles, getNumberOfInvalidFiles, getNumberOfFilesNoFileHeader, getNumberOfFilesNoProgramHeader, getNumberOfFilesNoSections)

The following function ExtractDetails() is used to extract the details of an ELF file's information. An ELF file's information is stored as File Header, Program Header, and Section Information. There is one set of information for the File Header and Program Header. However, there can be many sections in an ELF File.

This function calls ExtractFileHeader() to extract the information of the File Header. The function ExtractSegmentDetails() is called to extract information about the program header of ELF File. ExtractSectionDetails() is called to extract the information from all the sections in an ELF File.

```python
def ExtractFileDetails(file):
    returnValue = {}
    validELFFile = True
    hasFileHeader = True
    hasProgramHeader = True
    hasSections = True
    try:
        with open(file, 'rb') as elfile:
            try:
                eFile = ELFFile(elffile)
                # Extract the File Header Information
                fileHeader = ExtractFileHeader(eFile)
                if len(fileHeader) > 0:
                    returnValue.update(fileHeader) # Add the attributes to dictionary
                else:
                    hasHeader = False
                    raise Exception()

                # Extract the Program Header Information
                segmentDetails = ExtractSegmentDetails(eFile)
                if len(segmentDetails) > 0:
                    returnValue.update(segmentDetails) # Add the attributes to dictionary
                else:
                    hasProgramHeader = False
                    raise Exception()

                # Extract the Section Information
                sectionDetails = ExtractSectionDetails(eFile)
                if len(sectionDetails) > 0:
                    returnValue.update(sectionDetails) # Add the attributes to dictionary
                else:
                    hasSections = False
                    raise Exception()
            except:
                validELFFile = False
            finally:
                elffile.close()
        except:
            pass
    return (returnValue, validELFFile, hasFileHeader, hasProgramHeader, hasSections)
```

The function ExtractFileHeader() is used to extract all the information from the File Header of an ELF File.

```python
from elftools.elf.elffile import ELFFile

def ExtractFileHeader(elffile):
    returnValue = {} # Dictionary to hold the unique attributes of the header
    # The header information can be obtained as a dictionary.
    # However, there are some dictionaries inside this dictionary.
    # So, we create a flat structure taking out all the unique attributes and forming a dictionary.
    for key, value in elfile.header.items():
        # If the value for the key is a dictionary, then loop through all the attributes of this dictionary to collect the features.
        # The approach is simplistic as I do not go for a recursive function as it is known that there can be only one additional level of the dictionary.
        for insideKey, insideValue in value.items():
            if insideKey == "EI_MAG":
                pass
            else:
                returnValue[insideKey] = insideValue
        else:
            returnValue[key] = value
    return returnValue
```

# ExtractSegmentDetails() is used to extract all the information from the Program Header of an ELF File.

```python
from elftools.elf.elfile import ELFFile

def ExtractSegmentDetails(elffile):
    returnValue = {} # Dictionary to hold the unique attributes of the segments
    # Check if any segment information exists in the file
    # If it does, collect all the information of all the attributes in all the segments
    if(elffile.num_segments() > 0):
        prefixDict = {} # Dictionary to hold the unique segment attributes for all the segment names
        # Each ELF File may have one or more number of segments
        # Loop through all the segments
        for segment in elfile.iter_segments():
            prefix = ""
        # In each segment, there can be one or more number of attributes
        # The attribute "p_type" contains the segment name
```
