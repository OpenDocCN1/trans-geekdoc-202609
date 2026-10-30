
```
st.image(input_img, use_column_width=True)
st.write("**Output Pencil Sketch**")
```

```
st.image(final_sketch, use_column_width=True)
```

Now, open Bash or Terminal, wherever the code is, and then run Streamlit run Then, open the following link in your browser:

![](img/8f8a671916d96b455297952d0f37b96c_509_0.png)

Figure 8.13: OpenCV Pencil Sketch Output

### STEP 5: Now, let’s build the second model for the OpenCV cropping and changing pixel. If we gave the condition that if you want to select the model from Step 2 here, then it will be the Cropping Image. The st.file_uploader() function will return a BytesIO object. However, Image.open() accepts a string to read an image. Next, we will use the st.sidebar.slider() function for selecting the pixel coordinates from the slider for all the coordinates. We have added one if condition – either you want to crop or not. After that, we will do the necessary OpenCV image cropping operations and pixel change. The st.image() will dump the image and show the input and output image in the browser.

```
if model == "Crop Image":
st.subheader("Crop your Image app to your size")
if file_image is None:
st.write("You haven't uploaded any image file")
else:
input_img = Image.open(file_image)
image = np.array(input_img)
x, y = image.shape[:2]
height, width = image.shape[:2]
print(height,width)
st.sidebar.subheader("Choose Pixel for image")
# Let's get the starting pixel coordinates (top left of cropping rectangle)
startrowper=st.sidebar.slider("Start Row", min_value=0., max_value=1.0)
startcolper=st.sidebar.slider("Start Column", min_value=0., max_value=1.0)
endrowper=st.sidebar.slider("End Row", min_value=0., max_value=1.0)
endcolper=st.sidebar.slider("End Column", min_value=0., max_value=1.0)
Crop = st.sidebar.selectbox("You want to Crop", ("Yes", "No"))
if Crop=='Yes':
```

```
start_row, start_col = int(height * startrowper), int(width *
startcolper)
# Let's get the ending pixel coordinates (bottom right)
end_row, end_col = int(height * endrowper), int(width * endcolper)

# Simply use indexing to crop out the rectangle we desire
cropped = image[start_row:end_row, start_col:end_col]
row, col = 1, 2
fig, axs = plt.subplots(row, col, figsize=(15, 10))
fig.tight_layout()
axs[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
axs[0].set_title('Original Image')
cv2.imwrite('original_image.png', image)
st.image('original_image.png', use_column_width=True)
axs[1].imshow(cv2.cvtColor(cropped, cv2.COLOR_BGR2RGB))
axs[1].set_title('Cropped Image')
cv2.imwrite('cropped_image.png', cropped)
st.image('cropped_image.png', use_column_width=True)
else:
st.write("You don't want to crop")
```

Now, open Bash or Terminal, wherever the code is, and then run **Streamlit run** Then, open the following link in your browser:

![](img/8f8a671916d96b455297952d0f37b96c_512_0.png)

Figure 8.14: OpenCV Pixel change Output

So, the preceding is the output for the OpenCV pixel changer model in the Streamlit app.

### STEP 6: Now let’s build the third model for OpenCV sharpening our image. If we gave the condition that if you want to select the model from Step 2 here, it will be the Cropping Image. The st.file_uploader() function will return a BytesIO object. However, Image.open() accepts a string to read an image.

Next, we will use the st.sidebar.slider() function for selecting the pixel coordinates from the slider for all the coordinates. After that, we will do the necessary OpenCV image sharpening with the cv2.filter2d kernel and normalization application. st.image() will dump the image and show the input and output image in the browser.

```
if model == "Sharp Image":
 st.subheader("Sharpen your Image")

if st.sidebar.button('Changer'):
 showpred = 1
 if file_image is None:
  st.write("You haven't uploaded any image file")
 else:
  input_img = Image.open(file_image)
  image = np.array(input_img)
  row, col = 1, 2
  fig, axs = plt.subplots(row, col, figsize=(15, 10))
  #fig.tight_layout()
  axs[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
  axs[0].set_title('Original Image')
  # Create our sharpening kernel, we don't normalize since the
  # the values in the matrix sum to 1
  kernel_sharpening = np.array([[-1,-1,-1],[-1,9,-1], [-1,-1,-1]])
  # applying different kernels to the input image
  sharpened = cv2.filter2D(image, -1, kernel_sharpening)
  axs[1].imshow(cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB))
  axs[1].set_title('Image Sharpening')
  st.image(input_img, use_column_width=True)
  cv2.imwrite('sharpen_image.jpg', sharpened)
  st.image('sharpen_image.jpg', use_column_width=True)
```

Now, open Bash or Terminal, wherever the code is, and then run **Streamlit run** Then, open the following link in your browser:

![](img/8f8a671916d96b455297952d0f37b96c_514_0.png)

Figure 8.15: OpenCV Sharpening Output

### STEP 7: Now, let’s build the fourth model for the OpenCV colour space change. If we gave the condition that if you want to select the model from Step 2 here, it will be the Cropping Image. The **st.file_uploader()** function will return a BytesIO object. However, **Image.open()** accepts a string to read an image. Next, we have added the **st.sidebar.selectbox()** function on the sidebar for UI; here we have different OpenCV colour changing options like “bw”, ”hsv”, and so on. Then, if the condition matches the option which we chose, it will do the necessary operations, and at last **st.image()** will show the image inside the browser.

```
if model == "Color Spacer":
st.subheader("Sharpen your Image")
cs = ["bw","hsv","yuv","lab"]
color_space = st.sidebar.selectbox("Pick a space.", cs)

if st.sidebar.button('Changer'):
showpred = 1
if file_image is None:
st.write("You haven't uploaded any image file")
else:
input_img = Image.open(file_image)
st.write("**Input Photo**")
st.image(input_img, use_column_width=True)
src = np.array(input_img)
if color_space == "bw":
image = cv2.cvtColor(src, cv2.COLOR_BGR2GRAY)
if color_space == "hsv":
image = cv2.cvtColor(src, cv2.COLOR_BGR2HSV)
if color_space == "yuv":
image = cv2.cvtColor(src, cv2.COLOR_BGR2YUV)
if color_space == "lab":
image = cv2.cvtColor(src, cv2.COLOR_BGR2LAB)
st.write("**Output Pencil Sketch**")
st.image(image,use_column_width=True)
```

Now, open Bash or Terminal, wherever the code is, and then run **Streamlit run** Then, open the following link in your browser:

![](img/8f8a671916d96b455297952d0f37b96c_516_0.png)

Figure 8.16: OpenCV Colour Changer Output

So, the preceding is the output for the OpenCV model components in Streamlit.

We composed all the models under a function like the following:

```
def main():
{
CODE
}
```

```
if __name__ == '__main__':
main()
```

To locally debug the test, we run the command, Streamlit run

```
You can now view your Streamlit app in your browser.

Local URL: http://localhost:8501
Network URL: http://192.168.29.199:8501
```

Figure 8.17: Local Host URL for App

## 8.5 Creating the components for Heroku Deployment

![](img/8f8a671916d96b455297952d0f37b96c_518_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_518_1.png)

The build stage is a transform which converts a code repo into an executable bundle known as a slug by fetching and vendoring dependencies and compiling binaries and assets.

The release stage then takes the build and combines it with the deploy's current config. The resulting release contains both the build and the config and is ready for immediate execution.

Figure 8.18: Heroku Architecture

Now, create the Python Script for your application, containerize your whole Framework with Docker, release the build to App inside Heroku, and then host the application inside and deploy it there, which will generate a host URL.

Now, we will build the Docker image; for that, make sure you start the Docker, after which you will see the Docker is activated on the top. In the following screenshot, we can see that the first icon Docker is started. You can stop or restart from that icon.
