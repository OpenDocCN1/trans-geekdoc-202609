```
15.
16. # STEP 6: Install required python dependencies from the requirements file
17. RUN pip install -r requirements.txt
18.
19. # STEP 7: Run the train.py file
20. ENTRYPOINT ["python"]
21.
22. CMD ["train.py"]
```

When you have all the files at one place, you can start building the Docker image using the docker build command, as shown in the following figure:

![](bbox=[0.13, 0.39, 0.86, 0.59])

Figure 6.8: Docker image build started

This may take a few minutes to complete. After completion, you should see the last message, as shown in the following figure:

![](bbox=[0.3, 0.69, 0.68, 0.75])

Figure 6.9: Docker image built

The next step is to run the image to start the Docker container instance using the docker run command. Finally, it’s time to make the prediction. Add a brief description before taking the input from the user and, in this case, input data needs to pass in the sequence given in the description.

Execute the docker run command with the -it flag to run the image in an interactive mode, as shown in the following figure: