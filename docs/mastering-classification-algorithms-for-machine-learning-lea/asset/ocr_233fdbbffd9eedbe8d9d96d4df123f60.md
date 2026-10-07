extractInformationFromADirectory(“Data/TestData/Benign*/)"

```
print("BENIGN Files:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d\n "
```

```
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader,nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# BENIGN FILES:

Valid - 222

Invalid - 10

No File Header - 0

No Program Header - 0

No Sections - 5

extractInformationFromADirectory(“Data/TestData/Backdoor*/)",

```
print("BACKDOOR FILES:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d\n \
```

```
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader,nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# BACKDOOR FILES:

Valid - 62

Invalid - 2

No File Header - 0

No Program Header - 0

No Sections - 4