2. We need to provide the new notebooks with permission to access AI services. To do this, find the Studio execution role for the Studio environment and attach the AdministratorAccess IAM policy to it. We will use this policy for simplicity here. In a complete environment, you would need to design a policy to provide the specific permissions needed to access different services.

3. Clone https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook into your environment using the git clone https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook command if you have not already done so.

4 Run NLP tasks using Comprehend:

+   A. Open the comprehend.ipynb notebook in the Chapter12 directory. This notebook performs a list of ML tasks using Comprehend, including language detection, entity detection, sentiment detection, PII detection, key phrases detection, and syntax analysis.

+   B. Create some sample entities you would like to run NLP analysis on and save it as comprehend_sample.txt in the data directory.

+   C. Run the following code in the notebook to import the library and set up the boto3 client for Comprehend:

```
from pprint import pprint
import boto3 items_to_show = 10
with open('data/comprehend_sample.txt') as sample_file:
    sample_text = sample_file.read()
comprehend_client = boto3.client('comprehend')
```

+   D. Run the following code in the notebook to detect the dominant language in the text:

```
print("detecting dominant language")
languages = comprehend_client.detect_dominant_language(
    Text=sample_text)
lang_code = languages['Languages'][0] ['LanguageCode']
print(lang_code)
```

+   E. Run the following code in the notebook to detect entities:

```
print("Detecting entities using the pre-trained model.")
entities = comprehend_client.detect_entities(
```