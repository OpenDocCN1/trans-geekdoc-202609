be uploaded to Google Drive. So, for the moment, it is safe to assume that these three files have been wrongly labeled as JPEG files containing malware.

Now that we have the EXIF tags from all the JPEG files in our dataset, we will form a string of all the EXIF tags in a JPEG and store it as a record in a data frame. Once we finish this exercise, we will have a data frame containing a string of all the EXIF tags in each JPEG file. Also, we will label each record as whether it is a clean JPEG file or a JPEG file containing malware. This way, we will create our labeled data which can be used for building a supervised learning model.

The function fillDataInDataFrame() takes a list of dictionaries as returned by the function extractTagsFromAD() and creates a data frame. The data frame will contain two columns – one having all the EXIF tags in a JPEG file and another stating the associated string is from a clean JPEG file or a JPEG file containing malware.

import pandas as pd

from tqdm import tqdm

```
def fillDataInDataFrame(featureDictionary, extractionDescription, fileType):

# Create an Empty DataFrame
df = pd.DataFrame()

for record in tqdm(featureDictionary, desc = extractionDescription):
    # Create an empty Dictionary
    oneRecord = {}

    # Create an empty string
    recordString = ""

    # Loop through all the features in a record
    for k in record.keys():
        # Extract the value for the key and append it to the record
        
```