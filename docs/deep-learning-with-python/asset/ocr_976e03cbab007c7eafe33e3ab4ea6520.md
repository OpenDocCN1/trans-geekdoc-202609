+   - Predicting display ad click-through rate to decide which ad to serve to a given user at a given time.
+   - Flagging anomalous cookies on the conveyor belt of a cookie-manufacturing line.
+   - Using satellite images to predict the location of as-yet unknown archeological sites.

> **Note on ethics**
> 
> You may sometimes be offered ethically dubious projects, such as “building an AI that rates the trustworthiness of someone from a picture of their face.” First of all, the validity of the project is in doubt: it isn’t clear why trustworthiness would be reflected on someone’s face. Second, such a task opens the door to all kinds of ethical problems. Collecting a dataset for this task would amount to recording the biases and prejudices of the people who label the pictures. The models you would train on such data would merely encode these same biases into a black-box algorithm that would give them a thin veneer of legitimacy. In a largely tech-illiterate society like ours, “the AI algorithm said this person cannot be trusted” strangely appears to carry more weight and objectivity than “John Smith said this person cannot be trusted,” despite the former being a learned approximation of the latter. Your model would be laundering and operationalizing at scale the worst aspects of human judgement, with negative effects on the lives of real people.
> 
> Technology is never neutral. If your work has any impact on the world, this impact has a moral direction: technical choices are also ethical choices. Always be deliberate about the values you want your work to support.

It would be very convenient if you could import the correct dataset from `keras.datasets` and start fitting some deep learning models. Unfortunately, in the real world you’ll have to start from scratch.

In this chapter, you’ll learn about a universal step-by-step blueprint that you can use to approach and solve any machine learning problem, like those in the previous list. This template will bring together and consolidate everything you’ve learned in chapters 4 and 5, and will give you the wider context that should anchor what you’ll learn in the next chapters.

The universal workflow of machine learning is broadly structured in three parts:

+   1. **Define the task**—Understand the problem domain and the business logic underlying what the customer asked for. Collect a dataset, understand what the data represents, and choose how you will measure success on the task.
+   2. **Develop a model**—Prepare your data so that it can be processed by a machine learning model, select a model evaluation protocol and a simple baseline to beat, train a first model that has generalization power and that can overfit, and then regularize and tune your model until you achieve the best possible generalization performance.
+   3. **Deploy the model**—Present your work to stakeholders, ship the model to a web server, a mobile app, a web page, or an embedded device, monitor the model's