```
tf.zeros((4,), dtype=tf.float32),
self.embedding.weights[0].numpy()[[6, 8, 9], :].max(axis=0),
tf.zeros((4,), dtype=tf.float32),
]
assert np.allclose(emb, emb2)
```

# 9.7 Case Study: Vocal Duration Constrained by Note Duration

Singing voice synthesis (SVS) is an extension of the text-to-speech (TTS) problem, where lyrics and notes are converted from texts to artificial singing voices. The notes input dictates the tempo (i.e. speed as well as timing) of the generated vocal singing and provides the SVS model with contextual information to conform the synthesized singing to the musicality of the vocal piece. In one of the SVS projects that I have done previously, my model predicted the duration of each vocal unit at the phoneme level (i.e. one syllable at a time). For example, “I saw you smiling at me. Was it real or just my fantasy” becomes [“I,” “saw,” “you,” “smi,” “ling,” “at,” “me,” “was,” “it,” “real,” “or,” “just,” “my,” “fan,” “ta,” “sy”] (“Eyes on Me” from the main theme of Final Fantasy VIII, by Faye Wong; Figure 9.13), where the duration of each syllable is predicted by the model output. However, due to the nature of music, the singer’s vocal duration and timing need to align with the tempo of the sheet music or sometimes the background music accompaniment. That is to say, if the tempo denoted by the music sheet requires the vocalist to finish the singing of a sentence within 16 beats, then the total duration of all the syllables sung by the vocalist cannot exceed or be less than 16 beats (give or take with some expressiveness allowed). Therefore, there is a temporal constraint that needs to be put on the predicted duration of the phoneme. A simple approach to solve this problem is to predetermine the

![](bbox=[0.105, 0.725, 0.865, 0.865])

Figure 9.13 “Eyes On Me” sheet music from my previous SVS project.