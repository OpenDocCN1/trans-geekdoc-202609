# Image Captioning

# Chapter 7

This visualization is generated using TensorBoard. The words with similar semantic meanings or different parts of speech appear together.

We have learned how to train a caption representation for text to be used for generation. Next, we will see approaches for image captioning.

# Approaches for image captioning and related problems

Several approaches have been suggested for captioning images. Intuitively, the images are converted to visual features and text is generated from the features. The text generated will be in the form of word embedding. Some of the predominant approaches for generating text involve LSTM and attention. Let’s begin with an approach that uses an old way of generating text.

# Using a condition random field for linking image and text

Kulkarni et al., in the paper http://www.tamarberg.com/papers/generation_cvpr11.pdf, proposed a method of finding the objects and attributes from an image and to generate text with a conditional random field (CRF). The CRF is traditionally used for a structured prediction such as text generation. The flow of generation is shown here:

| Object(s)/Stuff | Attr | Prepositions | Constructed CRF | Generated Sentences |
|---|---|---|---|---||
| dog | brown, striped, feathered | near,1, beside,1, against,2, beside,3, beside,4, beside,5 | [image] | This is a photograph of one person and one dog. The person is against the brown sofa and the dog is near the person, and beside the brown sofa |
| person | brown, striped, wooden, feathered | near,1, beside,1, against,2, beside,3, beside,4, beside,5 | [image] | |
| sofa | brown, striped, wooden, feathered | near,1, beside,1, against,2, beside,3, beside,4, beside,5 | | |

![](bbox=[0.285, 0.765, 0.715, 0.835])

5) Predicted Labeling
<<null,person,b,against,brown_sofa,c>>
<<null,dog,a,beside,brown_sofa,c>>

[ 186 ]