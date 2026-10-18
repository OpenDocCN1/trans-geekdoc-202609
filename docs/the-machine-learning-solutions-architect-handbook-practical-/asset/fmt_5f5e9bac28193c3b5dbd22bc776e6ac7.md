
Amazon Comprehend can be a good fit for building intelligent document processing solutions and other NLP products. It can also serve as a good baseline tool that can be compared with custom NLP models.

## Amazon Textract

Many business processes, such as loan application processing, expense processing, and medical claim processing, require extracting text and numbers from images and documents. Currently, many organizations largely handle these processes manually and the processes can be highly time-consuming and slow.

`Amazon Textract` is an `optical character recognition` (`OCR`) AI service that’s primarily used for extracting printed text, handwritten text, and numbers from images and PDF documents. Textract is normally used as a processing step for downstream tasks such as document analysis and data entries. The core Textract functionalities are as follows:

*   `OCR`: OCR is a computer vision task that detects and extracts text data from PDF documents and images. The OCR component in Textract extracts raw text from the input documents and provides additional structural information about the documents. For example, the Textract output contains hierarchical structural relationships for the different objects in a document such as pages, paragraphs, sentences, and words. Textract also captures the positional information of the different objects in the input document. The hierarchical structural information and object positional data are useful when you’re extracting specific information from different locations in the documents. The OCR APIs are `DetectDocumentText` for detecting text synchronously and `StartDocumentTextDetection` for detecting text asynchronously.

*   `Table extraction`: Many documents contain tabular data structures and need to be processed as a table. For example, you might have an insurance claim document that contains a list of claim items and their details in different columns, and you may want to enter these claim items into a system. The table extraction component in Textract can extract tables and cells in the tables from a document. To use the table extraction feature, you can use the `AnalyzeDocument` API for synchronous operations and `StartDocumentAnalysis` for asynchronous operations.

*   `Form extraction`: Documents such as paystubs and loan application forms contain many name-value pairs whose relationships need to be preserved when they’re processed automatically. The form extraction component in Textract can detect these name-value pairs and their relationships for downstream processing, such as entering the names in those documents into a system. The form extraction component shares the same `AnalyzeDocument` and `StartDocumentAnalysis` APIs as the table extraction component.

*   `Signature in document analysis`: Textract can detect signature locations in documents, returning bounding boxes specifying signature positions and confidence scores. Signature detection can run independently or alongside other features like forms, tables, and custom queries. When combined with forms or tables, Textract relates detected signatures to corresponding cells or key-value pairs.

*   `Queries in document analysis:` Textract allows adding custom queries to extract specific information from documents. A query like “What is the applicant’s address?” will return just that data point from the analyzed document in a separate response structure.

Textract also has features for analyzing a specific kind of documents such as invoices and identity documents. For example, Textract can extract relevant data such as vendor and receiver contact information from an invoice or receipt without the need for any templates or configuration. Similarly, it can extract relevant information from passports, driver’s licenses, and other identity documentation issued by the US Government.

The Textract APIs are supported in the `boto3` library. The following code sample shows how to detect text using the `boto3` library. The full list of Textract APIs for `boto3` can be found at [https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/textract.html](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/textract.html).

```
import boto3
client = boto3.client('textract')
response = client.detect_document_text(
        Document={
            'Bytes': b'bytes',
            'S3Object': {
                'Bucket': '<S3 bucket name>',
                'Name': '<name of the file>'}
})
```

Textract also integrates with the `Amazon Augmented AI` (`A2I`) service to enable human-in-the-loop workflow integration for reviewing low-confidence prediction results from Textract. You can find more information about the A2I service at [https://aws.amazon.com/augmented-ai](https://aws.amazon.com/augmented-ai).

## Amazon Rekognition

`Amazon Rekognition` is a video and image analysis AI service. It supports a range of use cases, such as metadata extraction from images and videos, content moderation, and security and surveillance. The core capabilities of Rekognition are as follows:

*   `Label or object detection`: Label detection can be applied to use cases such as media metadata extraction for search and discovery, item identification and counting for insurance claim processing, and brand and logo detection. Rekognition can detect different objects, scenes, and activities in images and videos, and assign labels to them such as `soccer`, `outdoor`, and `playing soccer`. For the common objects that are detected, it also provides bounding boxes for the objects to indicate their specific positions in the image or videos. To use Rekognition for label detection, you can call the `DetectLabels` API. If Rekognition cannot detect specific objects in your images, you can also train a custom label detector with your training data using the `CreateProject` API. Once the model has been trained, you have the option to deploy a private prediction endpoint using the `StartProjectVersion` API.

*   `Facial analysis and recognition`: Facial analysis and recognition are useful for use cases such as video surveillance and security, automatic people labeling in images and video for content search, and understanding demographics. Rekognition can identify and analyze faces in images and videos. For example, you can perform analysis on faces to detect gender, age, and sentiment. You can also build an index of faces and assign names to them. Rekognition can map a detected face to a face in the index if a match is found. The main APIs for facial analysis and recognition are `DetectFaces`, `SearchFaces`, `IndexFaces`, and `CompareFaces`.

*   `Content moderation`: Rekognition has APIs (`StartContentModeration`) for detecting images and videos with explicit content and scenes, such as violence. Organizations can use this feature to filter out inappropriate and offensive content before making the content available to consumers.

*   `Short text detection`: Rekognition can detect short text in images and provide bounding boxes around the detected text using its `DetectText` and `StartTextDetection` APIs. This feature can be used to detect street names, the names of stores, and license plate numbers.

*   `Personal protection equipment (PPE) detection`: Rekognition provides a built-in feature for detecting PPE in images and videos using the `DetectProtectiveEquipment` API. This feature can be used for automated PPE compliance monitoring.

*   `Celebrity identification`: Rekognition also maintains a celebrity database that can be used for identifying known celebrities in images and videos. It has a list of APIs for this feature, including `RecognizeCelebrities` and `GetCelebrityInfo`.
