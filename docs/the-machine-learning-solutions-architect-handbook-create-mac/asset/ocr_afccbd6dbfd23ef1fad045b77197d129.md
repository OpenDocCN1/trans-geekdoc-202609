```
data = json.loads(request_body)
if isinstance(data, str):
    data = [data]
elif isinstance(data, list) and len(data) > 0 and
isinstance(data[0], str):
    pass
else:
    raise ValueError("Unsupported input type. Input type can be a string or a non-empty list. \
    I = got("{}").format(data))
```

```
tokenizer = BertTokenizer.from_pretrained("bert-uncased", lower_case=True)
```

```
input_ids = [tokenizer.encode(x, add_special_tokens=True) for x in data]
```

```
# pad shorter sentence
padded = torch.zeros(len(input_ids), MAX_LEN)
for i, p in enumerate(input_ids):
    padded[i, :len(p)] = torch.tensor(p)
```

```
# create mask
mask = (padded != 0)
```

```
return padded.long(), mask.long()
raise ValueError("Unsupported content type: {}")\n    format(request_content_type)
```

The following predict_fn() function takes input_data returned by input_fn() and uses the trained model to generate the prediction. Note that we will also use a GPU if a device is available on the server:

```
def predict_fn(input_data, model):
    device = torch.device("cuda" if torch.cuda.is_available()\n    else "cpu")
    model.to(device)
    model.eval()
```