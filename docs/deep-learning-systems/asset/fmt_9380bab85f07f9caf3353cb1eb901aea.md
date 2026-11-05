
The Hugging Face Transformers, Facebook Fairseq, and AWS Sockeye 2 libraries contain several transformer-based models to facilitate wider adoption \[DDV+20\]. Future models are likely to compromise between prodigious costly models and smaller efficient models, trained and adopted by medium-size companies and universities, with smaller serving latencies. These include smaller BERT-like models, such as `ALBERT` by Google, `DistilBERT` by Hugging Face, and `Q-BERT` by UC Berkeley. Other solutions are replacing computationally expensive layers with light convolutions, adapting the number of attention layers, or removing most attention layers during inference to reduce serving latency \[LCG+19, SDC+19, SDY+19, WFB+19, SGB+19, MLN19\].

## 3.3.2 SPEECH RECOGNITION

Automatic speech recognition (`ASR`) is the task of converting acoustic sound waves into written text. `ASR` differs from voice recognition, where the task is to identify a person based on their voice. One of the main `ASR` challenges is the combinatory space of various aspects of speech, such as pace, accent, pitch, volume, and background noise. Also, serving an `ASR` model requires decoding acoustic signals in real-time with reliable accuracy. Neural `ASR` approaches have successfully overcome these challenges with large datasets without pronunciation models, `HMMs`, or other components of traditional `ASR` systems. Nassif et al. provide a systematic review of various neural `ASR` systems \[NSA+19\].

![image](images/fig3_21.png)

Figure 3.21: Multiple transformer-based models and their respective number of parameters across time. Based on \[San19\].

`ASR` systems and other speech-related systems often transform the acoustic sound waves into a spectrogram or Mel-spectrogram representation. A spectrogram is a 2D frequency-time representation of the acoustic signal that uses frequencies across short-time intervals, as shown in [Figure 3.22](#13_Chapter03.xhtml#fig3-22). In the figure, the color represents the amplitude of a particular frequency at a specific time interval. The Mel-spectrogram is a spectrogram where the frequencies are scaled using the mel-scale to better match the frequency resolution of the human auditory system.

`Deep Speech 2 (DS2)` was developed by Baidu and is the first major neural `ASR`. It provides a baseline for other models. `DS2` uses a spectrogram as the input to a series of `CNN` and `RNN` layers \[AAB+15\]. The `CNN` layers treat the spectrogram input as an image.

![image](images/fig3_22.png)

Figure 3.22: A spectrogram is a 2D frequency-time representation of the acoustic signal where the frequencies for short time intervals are captured. Source: \[Wik18\] (CC BY-SA 4.0).

`Listen, Attend, and Spell (LAS)` was developed by Google. This model uses `SpecAugment` for data augmentation. `SpecAugment` uses image augmentation techniques on the spectrogram \[CJL+16, PCZ+19\]. The `LAS` system has an encoder and decoder. The encoder is a pyramid `RNN`. The decoder is an attention-based `RNN` that emits each character conditioned on all previous characters and the entire acoustic sequence.

`RNN-Transducer (RNN-T)` processes the input samples and streams alphabetical character outputs. It does not use attention. For mobile devices, Google developed a quantized `RNN-T` model that runs in real-time on a Google Pixel device and is deployed with the `Gboard` app with 80 MB memory footprint \[HSP+19, Sch19\].

`Wav2letter++` is an open-source neural `ASR` framework developed by Facebook; it uses the fully convolutional model `ConvLM` \[PHX+18, ZXL+18\]. Facebook also demonstrated the use of transformers for `ASR` \[WML+19\].

## 3.3.3 TEXT-TO-SPEECH

Text-to-speech (`TTS`) is the task of synthesizing speech from text. The most well-known `TTS` system is probably the one used by the late Prof. Stephen Hawking. A `TTS` system is typically composed of three stages: (1) a text-analysis model, (2) an acoustic model, and (3) an audio synthesis module known as a vocoder. Traditionally, audio synthesis modules combined short-speech fragments collected from a user to form complete utterances. Using these fragments makes it difficult to modify the tone or voice characteristics and results in a robotic-like synthesis.

Neural `TTS` systems are now able to generate human-like speech as measured by the `MOS` (Mean Opinion Score), a human evaluation of the quality of voice. A neural `TTS` model can learn to generate voices with different characteristics. They can also be adapted to generate music and speech from an image. Facebook uses automatic captioning to help visually impaired users browse their News Feed and hear a machine-generated caption of each image \[WWF+17\]. Google Duplex uses neural `TTS` models on Pixel phones, for example, to contact restaurants to make reservations \[LM18\].

The primary neural speech synthesis systems deployed in production are `WaveNet`, `Parallel WaveNet`, and `WaveRNN` and require a text-to-linguistic features preprocessing step. `Tacotron 2` provides a full end-to-end text-to-speech generator. `Deep Voice 3` and `ClariNet` are speech synthesizers (not end-to-end `TTS`) developed by Baidu that have been influential and may be used in production. `GAN`-based `TTS` is starting to gain traction in academia despite the earlier unknowns of how to use `GANs` with discrete values \[BDD+20\].

`WaveNet` by Google is a vocoder autoregressive model based on the `PixelCNN` model \[vDZ+16\]. It predicts a distribution for each audio sample conditioned on all previous audio samples and the input linguistic features. These features are derived from the input text and contain phoneme, syllable, and word information. To deal with long-range temporal dependencies needed for raw audio generation, `WaveNet` uses a stack of dilated causal convolutions to allow their receptive fields to grow exponentially with depth.

`WaveNet` suffers from high serving latency due to the sequential generation of audio samples. `WaveNet` uses an 8-bit integer value timestep (rather than a 16-bit, as is typical in audio) to reduce the latency and make the `softmax` output more tractable.

`Parallel WaveNet` by Google uses knowledge distillation to train a feedforward network with `WaveNet` \[vLB+17, HVD15\]. Knowledge distillation (detailed in [Section 6.4](#16_Chapter06.xhtml#sub6-4)) uses a teacher model to train a smaller, more efficient student model. The `FFNN` is easily parallelizable and generates speech samples in real-time with minimal accuracy loss compared to `WaveNet`. Google Assistant uses `Parallel WaveNet`.

`Tacotron 2` by Google is a generative end-to-end model trained with audio and text pairs that synthesizes speech directly from characters and combines the methodologies of the popular `WaveNet` and `Tacotron` to generate human-like speech \[SPW+17, WSS+17\]. Specifically, `Tacotron 2` uses `CNN` and `LSTM` layers to encode character embeddings into Melspectrograms, capturing audio with various intonations. This Mel-spectrogram is then converted to waveforms using a `WaveNet` model as a vocoder. This system can be adapted to generate speech audio in the voice of different speakers \[JZW+18\]. A speaker encoder network can generate a vector representation for a given speaker using seconds of reference speech from a target speaker. The `Tacotron 2` network is adapted to generate speech conditioned on this vector representation.

`WaveRNN` by Google uses a dual `softmax` layer to predict 16-bit audio samples efficiently; each `softmax` layer predicts 8 bits. For real-time inference in mobile CPUs, the small model weights are pruned (removed or forced to zero) \[KES+18\]. `LPCNet` is a `WaveRNN` variant that achieves higher quality by combining linear prediction with the `RNN` \[VS19\].
