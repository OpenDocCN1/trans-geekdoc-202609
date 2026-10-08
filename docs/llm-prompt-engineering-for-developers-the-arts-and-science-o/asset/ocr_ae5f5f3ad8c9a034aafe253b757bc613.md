When the [insert] is over, the world will be a better place.

The prompt is incomplete, and the model will complete it by generating the missing part. The result will be a complete sentence that makes sense in the context of the prompt. The prompt is limited to one insert parameter.

# ## 4.15 - Edit (Deprecated)

The edit endpoint¹⁹ is used to edit existing text. This endpoint requires two prompts:

+   - The input prompt
- The instruction prompt

The first prompt is used to provide the initial text, and the second prompt is used to provide the instructions for editing the text.

Here’s an example of an input prompt:

When the moon sets, all the birds fly back to their nests.

Here’s an example of an instruction prompt:

```
Delete the word "moon" and replace it with "sun". Delete the word "fly"\n and replace it with "return".
```

Here’s an example of a result:

When the sun sets, all the birds return to their nests.

The model will edit the text according to the instructions provided in the instruction prompt.

Instructions can be used to perform various operations on the text. For example, you can use instructions to delete, replace, or insert text, and even to change the formatting of the text or translate it into another language.

¹⁹https://platform.openai.com/playground/?mode=edit