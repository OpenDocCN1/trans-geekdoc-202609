Exec-managerial Adm-clerical Craft-repair
Machine-op-inspct Tech-support Craft-repair
Craft-repair
Transport-moving ?
Other-service relationship race education-num_na age fnlwgt education-num salary Husband White
False 34.000000 158419.999201 13.0 <50k Unmarried White False 38.000000 150601.000243 6.0
<50k Not-in-family White False 56.000000 261232.001670 9.0 <50k Not-in-family Black False
44.000000 721160.993845 10.0 <50k Husband Black False 52.000000 321958.996919 10.0 >=50k
Other-relative White False 30.000000 158002.000589 10.0 <50k Not-in-family White False 24.000001
162282.000054 9.0 <50k Husband Black False 24.000001 291407.000489 9.0 <50k Husband White
False 63.000001 83042.997601 13.0 <50k Own-child Black False 32.000000 249409.001923 9.0 <50k

# **Second attempt: Create two dataloaders for training and validation:** We can also create two DataLoaders (one for training and one for validation).

One great reason why we prefer this way of implementation is **we can pass in different batch sizes into each TabDataLoader**, along with changing options like shuffle and drop_last (at the bottom I’ll show why that’s super cool).

So how do we use it?

Our training and validation data live in to.train and to.valid right now. So we specify that along with our options. When you make a training DataLoader, you want shuffle to be True and drop_last to be True. This way the last incomplete batch will be dropped.

For the validation-dataloader, we use all the data from to.valid and a higher batch-size of 128 (because we have less data and can go through faster). We do not shuffle the data and keep the last smaller batch.

Then we just call DataLoaders and pass in our two dataloaders.

```
trn_dl = TabDataLoader(to.train, bs=64,
shuffle=True, drop_last=True)
val_dl = TabDataLoader(to.valid, bs=128)
```

```
dls = DataLoaders(trn_dl, val_dl)
dls.show_batch()
```

workclass education marital-status occupation relationship race education-num_na age fnlwgt education-num salary