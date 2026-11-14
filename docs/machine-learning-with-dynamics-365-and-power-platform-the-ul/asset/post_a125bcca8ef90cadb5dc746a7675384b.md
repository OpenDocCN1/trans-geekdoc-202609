
efficient, and more informed. Power Apps now includes a Mixed Reality component (see Figure 3.6).

## Microsoft HoloLens

> Microsoft HoloLens is the world's first untethered holographic computer that takes on Mixed Reality.

To understand HoloLens you need to know the meaning of hologram. Holograms are the objects that appear around you as real objects and are made up of sound and light. You can interact with these objects in the real world through voice commands, gestures, and gaze.

What HoloLens does is enables you to create holograms or objects that become part of your physical environment. HoloLens consists of multiple sensors, advanced optics, and holographic processing, which are used to create holograms that seamlessly blend with your environment.

## Dynamics 365 Mixed Reality Apps

Dynamics 365 Mixed Reality apps need HoloLens in a tangible way, as it has several optical sensors to understand the environment and sense it. It has a main camera pointing downward that picks up on hand motions and a techno-specific speaker that accumulates sound from all over the room. The HoloLens also consists of multiple microphones, one ambient light sensor, one HD camera, and Microsoft's custom Holographic Processing Unit that contains more processing power than the average laptop. Having all of this together in one device makes HoloLens compatible with the spatial bearings of the unit in the room, able to track walls and objects in the room, and able to incorporate holograms into the environment.

## Dynamics 365 Remote Assist

The Dynamics 365 Remote Assist application empowers employees to connect with both customers and on-site technicians to solve issues occurring in real time. The application uses HoloLens to make and receive video calls. HoloLens uses an augmented reality interface and voice commands to connect with the customers; this way, employees don't have to hold any device in their hands. Employees of either side can create or interact with the AR content that is visible through a HoloLens wearer's space. The off-site employee can easily visualize what the HoloLens wearer is seeing. The HoloLens wearer can point out the problem area by creating a circle or arrow around it, which will then become a hologram object. The off-site employee will troubleshoot the problem around this object and can offer guidance step by step to resolve the issue. This is how Dynamics 365 Remote Assist efficiently solves problems in real time with the help of employees available on the remote locations.

## Dynamics 365 Guides

The major challenge businesses are facing today is the lack of experience of new employees. Training people requires experts to guide them all the way through the work process and prepare them for all scenarios. But it's not as effective as it needs to be because experienced people are retiring every day. So what can be done for new employees, so that they can work as efficiently as experienced people? With this concept in mind, Microsoft introduced Dynamics 365 Guides.

Dynamics 365 Guides, as the name suggests, is a Mixed Reality learning app with the simple step-by-step instructions written on your system. Businesses provide new employees with the HoloLens, which can be used to pick holographic parts, text, diagrams, 3D visuals, and icons that can be placed on an actual machine for learning, to prepare them for real-world situations without the risk or the expense of having them work with actual assets. It helps new employees to get the job done from the very first day. This application enables new employees to work with existing processes with the right guide. The step-by-step instructions move with employees, pointing to the exact tools and parts they need and where they should apply them. What's a better way of learning than practically performing tasks without any risk factor involved? This way, employees can learn faster with fewer errors and more confidence without having to rely on other employees to teach them every step. The app also provides managers a report on how well the new employee has been working and learning. Employees make continuous improvement by adapting faster and becoming more adept at supporting complex aspects of the business, making them more valuable and competitive.

These Mixed Reality applications can make a difference in various industries like automotive, manufacturing, sales, energy, and more by enhancing customer experiences, encouraging employees to be more productive, and helping businesses to reduce costs.

## CHAPTER 4 Dynamics 365 and Custom ML Models Using Azure ML

> “It’s the choices you make that determine your future.”
> – Donny Ingram

With innovations in machine intelligence making ML capable of delivering– and sometimes exceeding – human-level performance in perceptual and cognitive tasks, organizations are increasingly evaluating how artificial intelligence can be applied to derive new business value and change the world for the better. It is fair to assume that soon the companies that are using the technologies to automate all the regular and routine work will progress faster than those that aren’t.

Technologies like artificial intelligence are transforming the way businesses are operating these days. It is the most trending technology of today and along with Azure cloud-based services, it’s doing miracles for organizations small and large, at scale.

### AZURE MACHINE LEARNING

Azure Machine Learning is a cloud-based environment that:

- Enables you to use cloud-based storage services such as Azure Blob, Azure Data Lake (including Gen2), Azure SQL Database, Azure Synapse Analytics (Modern Data warehouse), PostgreSQL, Databricks, and MySQL. Datasets can also be created from local files, public URLs, or Azure Open Datasets.

- Provides a managed cloud-based workstation optimized for your machine learning development environment called Azure Compute Instances. For more demanding or production grade model training, you can use an Azure Machine Learning compute cluster for additional capabilities.

- Allows you to designate a compute target, which is a designated compute resource or environment where you run your training script or host your service deployment. You can deploy these compute targets as a web service to call for real-time inference, periodically as a batch service, or deployed to an IoT device via a Docker container by using Azure IoT Edge.

- Adds flexibility to build and train models in authoring experiences such as Automated ML, or a visual drag-and-drop Designer, or code-first Notebooks with built-in support for open-source tools and frameworks, IDEs like Jupyter and command-line interfaces, or languages such as Python or R.

- Is a pay-per-use facility, which means you only have to pay for the services you use.

Azure ML can optimize business processes because it:

- Accelerates the end-to-end machine learning cycle. Azure ML services enable users to recognize the ideal algorithm by taking advantage of automated tools that aid in building predictive models faster, consuming less time.

- Supports multiple frameworks. Azure ML allows users to choose from a variety of frameworks to create AI models. Some of them are scikit-learn, PyTorch, MXNet, TensorFlow, Chainer, and Keras.

- Offers skill independent experience. Users can build models using a no-code designer, the Python SDK, Jupyter notebooks, VS Code, or their favorite IDE based on the skill level they possess or the authoring experience they prefer.

- Uses MLOps for communication between data scientists and the operations team. It is used to automate plenty of processes and produce more valuable insights by eliminating waste.

- Is compatible with container orchestration services. ML services are compatible with Docker, Azure Kubernetes Service, and Azure Container Instances, so it's easy to deploy models to platforms that support the most mission-critical workloads.

As of now, we have determined why Azure Machine Learning solutions are important for business growth. Let's learn about some concepts of Azure Machine Learning.

Many organizations are taking the first step toward implementing machine learning into their business practices. But they face some potential challenges like difficulty in collecting scattered data that lies all over the organization and difficulty in accessing it from wherever you desire. To overcome these hurdles, businesses need to deploy new machine learning models that could take months of engineering investments. Besides that, implementing machine learning in your business flow requires thorough training and the expertise of data specialists to scale, manage, and monitor machine learning systems.

So, to solve these problems, Microsoft combined machine learning with cloud computing and created a machine learning solution called Microsoft Azure Machine Learning. Azure Machine Learning empowers businesses with the add-on benefit of the cloud to build data-driven applications that can predict, forecast, and enhance several business processes.

### Azure Machine Learning Concepts

- **Models.** A model is a piece of code that is trained to identify specific patterns from the input and produce output. To create a model, you need to select an algorithm, provide it with data, and tune hyperparameters. It is basically a representation of what was learned by the machine learning algorithm. Once your model is created, you can use the selected algorithm to learn from the set of data. For example, creating a model that can recognize users' facial expressions and identify human emotions requires supervised learning. In this case, you need to train your model by providing example images with different facial expressions, each manually tagged with a specific emotion for it to learn from these images. This is how supervised learning
