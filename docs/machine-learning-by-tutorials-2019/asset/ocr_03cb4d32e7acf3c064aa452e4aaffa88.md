one character at a time. You'll go over more details about this when you get to the code.

To be thorough, select **Es2EnCharDecoder16Bit.mlmodel** in the Project navigator to view the decoder model:

+   * Machine Learning Model
* Name Es2EnCharDecoder16Bit
* Type Neural Network
* Size 750 KB
* Author unknown
* Description description not included
* License unknown

+   * Model Class
* Es2EnCharDecoder16Bit
* Automatically generated Swift model class

| Model Evaluation Parameters | | Description |
|---|---|---|
| Inputs | | |
| encodedChar | MultiArray (Double 87) |
| decoder_lstm_h_in | MultiArray (Double 256)? |
| decoder_lstm_c_in | MultiArray (Double 256)? |
| Outputs | | |
| nextCharProbs | MultiArray (Double 87) |
| decoder_lstm_h_out | MultiArray (Double 256) |
| decoder_lstm_c_out | MultiArray (Double 256) |

# **Looking at the decoder mlmodel file**

This summary shouldn't hold any surprises for you. Notice again the encoded input claims to be an MLMultiArray with a single dimension. In this case, it's telling you the truth: You actually provide inputs to the decoder one character at a time.

With your models in Xcode, you can finally write some code to use them. The first problem you need to solve is: How to one-hot encode your inputs?

When you use one-hot characters in iOS, you'll need to ensure each character maps to the same integer you used when you trained your model. Fortunately,