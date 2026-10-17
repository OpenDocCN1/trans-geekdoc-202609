
### Transformer 和 Mask 填充任务

[Listing 11.4](#ch11.xhtml#list11.4) 显示了 `hf_transformer_mask.py` 的内容，该文件展示了如何使用 HuggingFace Transformer 完成 Mask‑Filling 任务。

***LISTING 11.4: hf_transformer_mask.py***

```python
from transformers import pipeline
nlp = pipeline('fill-mask')
result = nlp("I hope that you <mask> the movie")
print("result:", result)
```

[Listing 11.4](#ch11.xhtml#list11.4) 以导入语句开头，随后初始化变量 `nlp` 为 `pipeline` 类的实例，参数为 `fill-mask`。随后，`nlp` 被调用并传入一个固定的示例句子，输出被赋值给变量 `result`。 
