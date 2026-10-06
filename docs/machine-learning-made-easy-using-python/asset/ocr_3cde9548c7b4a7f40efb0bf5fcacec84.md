We also have trained our CModel, and use it to make predictions. So let's create a function to pass the values and return the Genre label

```
In [8]: def recommend(age=18,gnd=0,watched=0,test=False):
    # Getting input is testing
    if test:
        age = int(input("Age:"))
        gnd = int(input("Gender:"))
    for g in Genres:
        print(g,'-',*gnre_enc.transform([g]))
    watched = int(input("Watched:"))
    # Ask the model for recommendation
    pred = CModel.predict([[age,gnd,watched]])
    # Decoding the prediction to Label
    rec = gnre_enc.inverse_transform(pred)
    return rec[0]
```

We defined a recommend() function and defined four parameters i.e. age by default 18, gnd gender by default 0(female), watched genre of the previously watched genre by default 0(Comedy) and test by default False which we can use during testing to pass the input values
If we pass test as True then the function will ask for our input and also display the encoded values for each genre. Then the model will predict using the input values. We will take the output(encoded value) and decode it and finally return it
So's move onto a new cell and call our recommend() function and specify the True for the test parameter

```
In [*]: recommend(test=True)
Age: 18
```

You can see we are prompted to the input prompt called in the recommend() function. So let's pass 18 as the age