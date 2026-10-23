We will use the whole image for training.
path = untar_data(URLs.PETS)

If we want to be able to recreate the same results, we should set a random-seed value:
np.random.seed(2)
After downloading all the images we see that path contains a list of POSIX-Path objects to all the images:
path.ls()[ :2]

(#2) [Path('/home/bmayr/.fastai/data/oxford-iiit-pet/
→ crappy'),Path('/home/bmayr/.fastai/data/oxford-iiit-pet/ → images')]

Let’s analyze how many image folders our data set contains:
len(path.ls())
5
path.ls()

(#5) [Path('/home/bmayr/.fastai/data/oxford-iiit-pet/
→ crappy'),Path('/home/bmayr/.fastai/data/oxford-iiit-pet/
→ images'),Path('/home/bmayr/.fastai/data/oxford-iiit-pet/
→ models'),Path('/home/bmayr/.fastai/data/oxford-iiit-pet/
→ image_gen'),Path('/home/bmayr/.fastai/data/oxford-iiit-pet/ → annotations')]

The fastai library is not just an add on on top of pytorch. Fastai comes with many more features and implements state-of-the-art techniques from deep learning science with the goal to provide a very smart abstraction layer for building rich, performance models with four to five lines of codes.

But you are also able to dig deep into the basics and use fastai for building your own, more sophisticated models. For this reason, fastai comes with a three tier architecture that we have already discussed above.

Just a quick reminder:
On top there are the four different applications (Vision, Text, Tabular, Colab).