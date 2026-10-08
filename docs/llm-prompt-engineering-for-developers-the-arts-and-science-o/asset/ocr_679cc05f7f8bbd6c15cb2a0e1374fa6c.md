```
eeds.wiki/golden-retriever

- The Rottweiler is a breed of domestic dog, regarded as medium-to-larg\e or large. The dogs were known in German as Rottweiler Metzgerhund, meaning Rottweil butchers' dogs, because their main use was to herd lives\tock and pull carts laden with butchered meat to market. Read more here: https://dogbreeds.wiki/rottweiler
""
```

```
print(pipeline_prompt.format(
	role_description=role_description,
	instruction_details=instruction_details,
	examples=examples
))
```

This is its output:

Role: You are a You are a smart bot specialized in answering questions about dogs breeds..

Instructions:
Write the characteristics of the following dog breed: "German Shepher d".

Examples:
- The Golden Retriever is a large-sized breed of dog bred as gun dogs to retrieve shot waterfowl such as ducks and upland game birds during hunting and shooting parties, and were named 'retriever' because of their ability to retrieve shot game undamaged. Read more here: https://dogbreeds.wiki/golden-retriever

+   - The Rottweiler is a breed of domestic dog, regarded as medium-to-large or large. The dogs were known in German as Rottweiler Metzgerhund, meaning Rottweil butchers' dogs, because their main use was to herd livestock and pull carts laden with butchered meat to market. Read more here: https://dogbreeds.wiki/rottweiler