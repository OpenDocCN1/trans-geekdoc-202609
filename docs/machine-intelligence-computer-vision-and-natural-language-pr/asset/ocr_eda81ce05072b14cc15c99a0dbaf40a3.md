# DR Detection Using Machine Learning Algorithms

Tele-Ophthalmology Symposium has provided eye fundus images under a variety of imaging conditions with labels to detect the DR level in retinal images. Each image is rated on a scale of 0–4: 0 = No DR; 1 = Mild; 2 = Moderate; 3 = Severe; 4 = Proliferative DR. You can detect the locations of DR on retinal images and scale DR levels from 0–4. The website has certain non-functional requirements, such as the website will be highly responsive and fast. It should be user-friendly and simple. There should be only a single retina per patient. Multiple retinas on a single page are not allowed. The image which is going to be uploaded should be a jpeg or png file and the maximum size of the image should be less than 50 nb. Basically, there are different kinds of users who may access the system:

+   - Clinicians: Clinicians can make use of Diabetes Web to check the diabetes results of the patients. They can confirm their results in comparison with the results they obtained through Diabetes Web.
- Ophthalmologists: Ophthalmologists can make use of Diabetes Web to predict the different levels of DR by uploading the fundus image of the patient’s retina.
- Doctors: Doctors can also make use of this website for prioritizing their patients based on the severity of their DR.

Figure 6.2 shows the flow of the research work carried out. Figure 6.2 helps to explain the sub-systems making up the system and the framework for sub-system control and communication. From Figure 6.2, we can see the user will be giving the input (in the form of an image which will contain the images of the retina) through our user interface.

With the help of Flask microservices we put the image into our python backend. From there the actual computation starts. As the first stage of processing we take the image into the image processing unit. In this module we extract the necessary information from the image, then, using a model, we ordered the extracted symbols

![](bbox=[0.121, 0.715, 0.879, 0.883])

Figure 6.2 Framework of the research work.