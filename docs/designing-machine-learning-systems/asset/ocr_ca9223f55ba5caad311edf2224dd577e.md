If the position in which a prediction is shown affects its feedback in any way, you might want to encode the position information using *positional features*. Positional features can be numerical (e.g., positions are 1, 2, 3,...) or Boolean (e.g., whether a prediction is shown in the first position or not). Note that “positional features” are different from “positional embeddings” mentioned in Chapter 5.

Here is a naive example to show how to use positional features. During training, you add “whether a song is recommended first” as a feature to your training data, as shown in Table 8-1. This feature allows your model to learn how much being a top recommendation influences how likely a song is clicked on.

# Table 8-1. Adding positional features to your training data to mitigate degenerate feedback loops

| ID | Song | Genre | Year | Artist | User | 1st Position | Click |
|---|---|---|---|---|---|---|---|
| 1 | Shallow | Pop | 2020 | Lady Gaga | listenr32 | False | No |
| 2 | Good Vibe | Funk | 2019 | Funk Overlord | listenr32 | False | No |
| 3 | Beat It | Rock | 1989 | Michael Jackson | fancypants | False | No |
| 4 | In Bloom | Rock | 1991 | Nirvana | fancypants | True | Yes |
| 5 | Shallow | Pop | 2020 | Lady Gaga | listenr32 | True | Yes |

During inference, you want to predict whether a user will click on a song regardless of where the song is recommended, so you might want to set the 1st Position feature to be False. Then you look at the model’s predictions for various songs for each user and can choose the order in which to show each song.

This is a naive example because doing this alone might not be enough to combat degenerate feedback loops. A more sophisticated approach would be to use two different models. The first model predicts the probability that the user will see and consider a recommendation taking into account the position at which that recommendation will be shown. The second model then predicts the probability that the user will click on the item given that they saw and considered it. The second model doesn’t concern positions at all.