# # 6 Making Up Your AI's Mind
Decision-Making Architectures

Tobias Karlsson

# ## 6.1 INTRODUCTION

One of the first and most fundamental decisions you must make when you are creating an AI to control a creature in a game is what decision-making architecture to use. The decision-making architecture is the framework within which your AI decides what behaviour to execute and then executes that behaviour at any given moment. This chapter explores the more popular options available, their respective strengths and weaknesses, and under what circumstances you would choose one over the other.

For this chapter, a behaviour is defined as a set of actions an AI can take to achieve a specific goal or to react to a specific situation. The granularity of each behaviour is up to the implementer, for instance, you could choose to have a behaviour for combat or to have many behaviours for different aspects of combat, such as a behaviour for reloading the AI’s weapon and one for throwing grenades. The granularity you choose depends on what makes sense for the AI in your game. The AI for an individual creature is created by giving it a set of behaviours and the information needed to select the appropriate behaviour at runtime.

# ## 6.2 IMPORTANT CHARACTERISTICS

There are many different characteristics of decision-making architectures, and which are more important in a given situation depends on the exact nature of the problem you are trying to solve; however, for most projects, many of the following characteristics will have some relevance.

# ## 6.2.1 PREDICTING BEHAVIOUR SELECTION

Every agent will have a set of behaviours. Some of these behaviours may be quick reactions to a surprising event, whereas others might be a fallback behaviour that is only active if no other good behaviour can be found. It is important to be able to reason about when and under what circumstances a particular behaviour will become