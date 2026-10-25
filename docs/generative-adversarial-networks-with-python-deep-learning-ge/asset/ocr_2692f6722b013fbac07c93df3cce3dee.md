```
```python
# upsample to 14x14
gen = Conv2DTranspose(128, (4,4), strides=(2,2), padding='same')(gen)
gen = LeakyReLU(alpha=0.2)(gen)
# upsample to 28x28
gen = Conv2DTranspose(128, (4,4), strides=(2,2), padding='same')(gen)
gen = LeakyReLU(alpha=0.2)(gen)
# output
out_layer = Conv2D(1, (7,7), activation='tanh', padding='same')(gen)
# define model
model = Model(in_lat, out_layer)
return model
```
```

```
```python
# define the combined generator and discriminator model, for updating the generator
def define_gan(g_model, d_model):
# make weights in the discriminator not trainable
d_model.trainable = False
# connect image output from generator as input to discriminator
gan_output = d_model(g_model.output)
# define gan model as taking noise and outputting a classification
model = Model(g_model.input, gan_output)
# compile model
opt = Adam(lr=0.0002, beta_1=0.5)
model.compile(loss='binary_crossentropy', optimizer=opt)
return model
```
```

```
```python
# load the images
def load_real_samples():
# load dataset
(trainX, trainy), (_, _) = load_data()
# expand to 3d, e.g. add channels
X = expand_dims(trainX, axis=-1)
# convert from ints to floats
X = X.astype('float32')
# scale from [0,255] to [-1,1]
X = (X - 127.5) / 127.5
print(X.shape, trainy.shape)
return [X, trainy]
```
```

```
```python
# select a supervised subset of the dataset, ensures classes are balanced
def select_supervised_samples(dataset, n_samples=100, n_classes=10):
X, y = dataset
X_list, y_list = list(), list()
n_per_class = int(n_samples / n_classes)
for i in range(n_classes):
# get all images for this class
X_with_class = X[y == i]
# choose random instances
ix = randint(0, len(X_with_class), n_per_class)
# add to list
[X_list.append(X_with_class[j]) for j in ix]
[y_list.append(i) for j in ix]
return asarray(X_list), asarray(y_list)
```
```

```
```python
# select real samples
def generate_real_samples(dataset, n_samples):
# split into images and labels
```
```