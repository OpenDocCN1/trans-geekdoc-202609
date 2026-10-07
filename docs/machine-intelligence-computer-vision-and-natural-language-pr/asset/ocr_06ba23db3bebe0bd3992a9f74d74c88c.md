# 118 Machine Intelligence

and make that a digital equation. Then we have to confirm that with the user, so that it is the same equation which is uploaded by the user. After receiving confirmation from the user, we can put that digital equation into our pretrained model and obtain the results. That result will be moved to the python backend. Again, with the help of Flask microservices we can give response to the user through our user interface.

The visual part of our web-based computer application is the part through which a user interacts with Diabetes Web. It determines how commands are given to the system or the program and how data is displayed on the screen. Our website will be a single page website where the user can input the images onto our site. Figures 6.3 and 6.4 show two pages of the dashboard of the Diabetes Web.

After loading an image as an input to the system, the user will be able to see the result on the same page. Also, the user will be able to download the solution as a pdf, by clicking the print button. Figure 6.5 shows the diabetes prediction page. On this page, the user can input the necessary basic details to the site and get an instant result (diabetic or not) on the same page. Figures 6.6 and 6.7 show the diabetes retinopathy prediction page and how to choose an image.

# 6.4 Diabetic Retinopathy Detection

# 6.4.1 Vertical and Horizontal Flip in Image Augmentation

An image flip reverses the rows or columns of pixels in the case of a vertical or horizontal flip respectively. The flip augmentation is specified by a Boolean horizontal flip or vertical flip argument to the Image Data constructor class. For photographs like the bird photograph, horizontal flips may make sense, but vertical flips would not. For other types of images, such as aerial photographs, cosmology photographs, and microscopic photographs, vertical flips may make sense (Gondhalekar, 2020).

# 6.4.2 Random Rotation Augmentation

A rotation augmentation randomly rotates the image clockwise by a given number of degrees from 0 to 360. The rotation will likely rotate pixels out of the image frame and leave areas of the frame with no pixel data that must be filled. In example this https://machinelearningmastery.com/how-to-configure-image-data-augmentation-when-training-deep-learning-neural-networks/ demonstrates random rotations via the range argument, with rotations to the image between 0 and 90 degrees. For random brightness augmentation, the brightness of the image can be augmented by either randomly darkening images, brightening images, or both. The aim is to allow a model to generalize across images trained on different lighting levels. This can be achieved by specifying the brightness range argument to the