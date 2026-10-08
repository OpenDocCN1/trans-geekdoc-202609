```
prompts: prompts.txt
providers: exec:python lc.py
tests:
  - vars:
    fn: translate(Hi, en, dk)
    assert:
      - type: is-json
      - type: contains
        value: "\"translation\""
      - type: contains
        value: "\"from_lang\""
      - type: contains
        value: "\"to_lang\""
      - type: contains
        value: "\"sentence\""
  - vars:
    fn: translate(Hi, en, fr)
    assert:
      - type: is-json
      - type: contains
        value: "\"translation\""
      - type: contains
        value: "\"from_lang\""
      - type: contains
        value: "\"to_lang\""
      - type: contains
        value: "\"sentence\""
  - vars:
    fn: translate(Hi, en, ar)
    assert:
      - type: is-json
      - type: contains
        value: "\"translation\""
      - type: contains
        value: "\"from_lang\""
      - type: contains
```