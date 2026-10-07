This file will consolidate all the dictionaries returned by the function JPEGFileFeatureExtractorToDictionary() into a list and return the list.

```
import glob
```

```
def extractTagsFromADirectory(inputDirectory):
    # Declare Counters
    numberOfValidFiles = 0
    numberOfInvalidFiles = 0
    numberOffFilesWithoutTags = 0

    # Create an Empty List to hold all the features of all the files
    returnValue = []

    n = 0

    # Loop through all the files in the Input Directory
    for file in glob.glob(inputDirectory):
        # Create an empty Dictionary
        oneFileFeatures = {}

        try:
            # Read the file and extract the features
            fileFeatures = JPEGFileFeatureExtractorToDictionary(file)

            # If the File had some features, then create an entry for the file
            if len(fileFeatures.keys()) > 0:
                # Write the File Name
                oneFileFeatures[FILE_NAME_COLUMN_NAME] = file
```