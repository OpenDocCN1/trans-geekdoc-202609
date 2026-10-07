# Machine Learning

# Chapter 15: Natural Language Transformation, Part 1

![](bbox=[0.383, 0.107, 0.616, 0.532])

The Sound of MusicKit
Normalmente no me gustan los musicales. Pero
El Sonido de Música me sorprendió. Fácilmente
una de mis películas favoritas. ¡la recomiendo!

Translation:
I don't feel made of money. It Kound Tom's family
completed. Show me a lot of friends are my
The restaurant!

Night of the Living Deadlocks
Muy mala. ¡Muy aburrido! No dejes
hablar de cerradas actuaciones. Es mi peor
pesadilla hecha película. Tengo suficientes
problemas de código. No necesito una película
para recordar. Fue una tortura.

Translation:
My mother is very much. My broken Don't
me stop single and story. It's my favorite
time to the discount. I have enough party and
control. I don't need a real movie to remember.
This was a strange.

The iPhone Sense
Increíble. ¿Pensabas que Apple ya no pudiera
sprender? Esta vez te sorprenderá.

# SMDB app with translated reviews

Yikes! Even if you don't know Spanish, it's pretty clear these translations aren't good. Does that mean there's no hope for this model?

# Let's talk translation quality

Judging before you give up, one would blame you for thinking this seq2seq models, let's try to explain this performance as well well as some possible solutions.

First, this chapter described the most basic version of a seq2seq model — the encoder and decoder each consist of just a single LSTM layer. LSTMs don't stack as well as convolutional layers do, but you can still see improvement more than one. In the next chapter, you'll try a slightly different encoder that should improve things a bit.

Secondly, we performed absolutely no hyper tuning. How would it perform if the LSTMs have more units, like 512 instead of 256? What about different