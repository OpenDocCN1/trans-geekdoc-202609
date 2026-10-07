displayImageList = [None] * len(uniqueLabels)
imageTitleList = [None] * len(uniqueLabels)

```
fig = plt.figure(figsize=(20, 15))
grid = ImageGrid(fig, 111,
    nrows,ncols=(math.ceil(len(uniqueLabels)) / NUM_
    COLUMNS, NUM_COLUMNS),
    axes_pad=0.1, # pad between axes in inch.
    )
```

```
imageNumber = 0
for i in tqdm(range(df)):
    labelForFile = df.loc[i][COLUMN_LABEL]
    if labelForFile in uniqueLabels:
        imageTitleList[imageNumber] = labelForFile
        displayImageList.remove(imageNumber) = getImage(i)
        uniqueLabels.remove(labelForFile)
        imageNumber += 1
```

```
if len(uniqueLabels) < 1:
    break

for ax, im in zip(grid, displayImageList):
    # Iterating over the grid returns the Axes.
    ax.imshow(im)
```

```
plt.show()
```

```
52%|████ | 626/1213 [00:06:00:05, 99.01it/s]
```