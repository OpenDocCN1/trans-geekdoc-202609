```
import json
from collections import namedtuple
import matplotlib.pyplot as plt

plt.rcParams["font.family"] = "TeX Gyre Heros"
history = namedtuple("history", ["history"])
with open("./ml-1m/keras_dfm_history.json", "r") as fid:
    history.history = json.load(fid)

fig, axs = plt.subplots(1, 2, figsize=(10, 4))
n_epochs = len(history.history["loss"])
epochs_arr = np.arange(1, n_epochs)
ax = axs[0]
ax.plot(epochs_arr, history.history["loss"][1:], label="train")
ax.plot(
    epochs_arr, history.history["val_loss"][1:], ls="--", label="test"
)
ax.legend()
# ax.set_yscale('log')
ax.set_xlabel("epoch")
ax.set_ylabel("Loss")
ax.set_title("Loss")
ax.set_xticks(epochs_arr[::2])
ax = axs[1]
ax.plot(epochs_arr, history.history["mse"][1:], label="train")
ax.plot(
    epochs_arr,
    history.history["val_mse"][1:],
    ls="--",
    label="test",
)
ax.legend()
# ax.set_yscale('log')
ax.set_xlabel("epoch")
ax.set_ylabel("MSE")
ax.set_title("MSE")
_ = ax.set_xticks(epochs_arr[::2])
plt.savefig("dfm-train.svg")
```

# 6.6 Regular Expressions (Regex)

Aside from simple native Python string methods and corresponding vectorized methods implemented by NumPy, Pandas, and Tensorflow, regular expression offers a versatile and elegant way to process large amounts of text data. Speaking of my personal experiences using regex: when I started my PhD program in 2014, I rotated in one of the genetics labs whose main focus of the study was human cancer genomics. The human genome has about 3 billion base pairs, and since DNA is a double helix, this is about 6 billion letters of “A,” “T,” “C,” and “G” stored in the text file, making each data file gigabytes in size! Trying to search for