# 6. Run computer vision with Rekognition:

A. Open the rekognition.ipynb notebook in the Chapter12 directory. This notebook runs a list of text extraction tasks, including text extraction, table extraction, and form extraction.

B. Save a sample image for analysis as textract_sample.jpeg in the data directory. Try to use a sample image with text, tables, and forms in it.

C. Run the following code in the notebook to set up a boto3 client for Textract:

```
from pprint import pprint
import boto3
textract_client = boto3.client('textract')
```

D. Run the following code in the notebook to load the image:

```
document_file_name = 'data/textract_sample.png'
with open(document_file_name, 'rb') as document_file:
    document_bytes = document_file.read()
```

E. Run the following code in the notebook to detect tables and forms:

```
print('Detecting tables and forms')
feature_types = ['TABLES', 'FORMS']
tables_forms = textract_client.analyze_document(
    Document={'Bytes': document_bytes},
    FeatureTypes=feature_types)
blocks_to_show = 10
print(tables_forms['Blocks'][:blocks_to_show])
```

F. Run the following code in the notebook to detect text:

```
print('Detect text')
text = textract_client.detect_document_text(
    Document={'Bytes': document_bytes})
blocks_to_show = 20
print(text['Blocks'][:blocks_to_show])
```