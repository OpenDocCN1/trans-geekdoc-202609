And person from the 18-24 in the None class
should be shown nothing but if the person is 25 or
more the Insurance ad should be shown
All this assumed conditions are called
hothesis. So using these hypothesis we can
create a testing dataset with close to accurate
outputs. Let's create them

```
In [3]: import numpy
X = dt.drop(columns='Ad')
y = dt['Ad']

def en(val):
    v = Enc.transform([val])
    return v[]

st_X = numpy.array(
    [21,en('None')],[21,en('Health')]],
    [27,en('None')],[23,en('Automobiles')]],
    [34,en('None')],[34,en('Automobiles')]])
st_y = numpy.array(
    [en('Insurance')],[en('Insurance')]],
    [en('Insurance')],[en('None')]],
    [en('Insurance')],[en('Car')]])
```

First of all we imported the numpy package
create our test data. Then we divided the dataset
to training input and training output
To create the testing set we will use the en()
function which will take the Search or Ad label
and return the encoded value for it. We can
create some testing data based on our hypothesis,
like a 21-years old person of class None ([21,en(
('None')])]) should be shown no advertisements ([en(
('None')])])
As mentioned earlier the training set is built
upon hypothesis. They may be correct or wrong. We
created them for the purpose of testing our
model. We can only use this in situations
where the data is compressed into a small
dataset. We can visualize the dataset using the
pandas data frame