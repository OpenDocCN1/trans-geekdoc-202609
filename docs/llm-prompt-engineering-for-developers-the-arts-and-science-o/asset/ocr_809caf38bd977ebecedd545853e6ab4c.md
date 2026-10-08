```
- vars:
    fn: translate(Hi, en, fr)
  assert: *default_assertions

- vars:
    fn: translate(Hi, en, de)
  assert: *default_assertions

- vars:
    fn: translate(Hi, en, it)
  assert: *default_assertions
EOF
```

Another possible solution, though not as elegant as the previous one, is to use the $ref property:

```
assertionTemplates:
  isJson:
    type: is-json
  containsTranslation:
    type: contains
    value: "\\translation\\"
  containsFromLang:
    type: contains
    value: "\\from_lang\\"
  containsToLang:
    type: contains
    value: "\\to_lang\\"
  containsSentence:
    type: contains
    value: "\\sentence\\"

prompts: prompts.txt
providers: exec:python lc.py
tests:
- vars:
```