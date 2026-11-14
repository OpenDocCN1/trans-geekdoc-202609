# 12 Extended Deductive

DEDUCTIVE analysis entails searching for a meaning in our corpora. We'll already have a sense for the pattern we seek. Is this tweet about a celebrity wedding? Does this speech bring up welfare reform? Is this news article discussing conspicuous consumption?

To answer questions like these, researchers commonly hand-label a manageable random sample of documents. The key question is whether these labels are used to build classifiers, validate classifications, or both. Here, we'll discuss using labels to build classifiers (i.e. supervision) and use these labels to validate classifications. We'll also explore using pre-trained models to classify documents.

These methods build on both supervised and unsupervised methods discussed previously and, specifically, extend dictionary-based approaches discussed in Core Deductive. The techniques we discuss here are helpful when our classifications are not discrete, we have two or more categories, or when a unique lexicon does not clearly distinguish categories.

# SUPERVISION AND VALIDATION

Let's assume we already have a classification scheme. Let's also assume we have unread, unlabeled documents that are too numerous to read and label. Say we label 5% of our corpus. We could then try to predict those labels. This is called supervision because we know the intended labels and our model predicts those labels. As a result, any supervised classifier is only as good as those labels—and ultimately learns the labeler's interpretation.

Once trained, we can reuse our model on unlabeled data. We've already used many of these pretrained models. Optical character recognition (OCR) research, for instance, played a significant role in advancing such classifiers. We don't need to retrain OCR models each time because characters do not usually change much.1

In contrast, we may jump right to automatically classifying without first labeling. We covered a version of this in Core Deductive with

1 Although, recall Tesseract allows fine-tuning a model to recognize a specific person's handwriting.