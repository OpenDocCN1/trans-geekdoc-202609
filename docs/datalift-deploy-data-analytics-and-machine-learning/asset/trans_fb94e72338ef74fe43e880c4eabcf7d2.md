

Some challenges that we have addressed include the scalability of the service for peak traffic and cost. By hosting the production infrastructure internally at OLX (utilizing, for example, Kubernetes and TensorFlow-Serving), we reduced cost by more than 50%. We deployed queues between the metadata service and the models, enabling us to react gracefully to traffic peaks and scale out with the increasing traffic. Adding buffer queues resulted in an asynchronous service. Sometimes, asynchronicity is not fast enough, e.g., for preventing the listing of illegal sales. So we moved to deploy the wrappers to image modeling services (IMS). In sum, the simplified and synchronous infrastructure for deploying Deep Learning models looks like this. ![](Image00008.jpg) To solve the peak traffic requirements, we have more instances than required. Some instances are idle until traffic demand activates them. From the Q&A “How do you go about making results and predictions available to data analysts?” “We decouple the analytical from the operational workload by providing a replica database and Athena tables.” “How was the training data for image quality detection curated?” “We crowdsourced via mechanical turk by showing the same picture to 10 people and working with the average.”

For open positions see [www.olxgroup.com/careers](https://www.olxgroup.com/careers)

# Deploying the first Neural Network in energy transmission service

## The Elia Group TSO use case

**Rachel Berryman**, Data Scientist, AI Center of Excellence, Elia Group  
Moderated by **Promit Ray**

How the Elia Group managed to, in less than half a year, deploy a neural network for predicting grid losses that saved 1% in grid loss cost cover in the first year in production. Enabling “citizen development” allowed for such a quick deployment of the model to production.

The Elia Group manages the electricity transmission systems in Belgium and eastern Germany with a reliability level of 99.999%. As the responsible transmission system operator (TSO) for these regions, the Elia Group is also responsible for integrating the increasing share of renewable energy into the grid. Energy is not like any other product. It can't be stored at scale, meaning that every second demand has to match supply. Electricity typically is not generated where it's used. It is a long distance from the offshore wind farm, the solar park, and the power plant to your house and various businesses. The TSO has the responsibility that demand equals supply constantly. AI is an essential tool in meeting this challenge, but it can be difficult to roll out AI projects in such a highly regulated environment.

### Energy transition to renewables

The electricity and energy system is transitioning to renewable energy. This is necessary for mitigating climate change. Our TSOs are at the center of shifting from the old paradigm where generation follows consumption to the renewables paradigm where demand follows generation. It means we're moving toward much more intermittent energy generation, including people generating energy themselves with their own solar panels or with flexibility from their devices.

“This is great for decarbonizing our world, helping reach Europe’s climate goals. But for us it means changing how business is done, how we keep the lights on. We have to increase scalability and our ability to manage complexity, intermittency and uncertainty.”

**Rachel Berryman**, Data Scientist

“The use case is an ideal example of how AI can meet our sustainability goals. Energy concerns everybody as does climate change, so the talk really helps us connect the dots between data science, technology and life.” **Promit Ray**, Data Scientist

### Energy data

The energy transition means more data, for example, from smart meters, connected devices, real-time markets. Let’s tap into that data. We need better predictions, especially as supply is more intermittent and uncertain. Predictive modeling is a mandatory tool for the new electricity paradigm.

As a data science team in the energy space, we use data to reduce complexity and increase scalability. Energy problems tend to be more difficult than other data science problems. Some of the data is highly sensitive since our core mission is reliability. Making sure that everything is running smoothly also means things are failsafe and for that, you really have a lot of processes in place. Safety and reliability issues often make it difficult to access data and make it available to the data team. Also, energy has a time series component to it, which adds another layer of complexity.

#### What is the challenge in accessing data?

There are different security zones where sourcing systems are located. Moreover, you need different technologies to access the data. Data governance may diverge too. Sometimes the data is readily available, and sometimes we need to extract it. If you can streamline data availability and access, then you have more time for things like exploration and analysis.

50 Hertz, the east German TSO in the Elia Group, has an energy data cloud. It is an easy-to-use, functional data access platform. It gives all 50 Hertz employees the ability to explore energy-relevant data.

The energy data cloud standardizes permission, including APIs for accessing data from various sources. Users need only one permission to access data. Additionally, every dataset has a listed owner.

### Predicting grid losses with a neural network

Standardized data access is critical for rolling out use cases, giving people access to the data they need. It enabled rapid machine learning implementations.

One example is the use case of forecasting grid losses. Whatever energy is generated and transported, it is not possible to get every single electron that was generated to the final destination. Some of it is lost, in the form of heat, because transmission is at very high voltages. And the amount that is lost is generally around two percent of what is generated. But it can be only one percent if the energy doesn't have to travel very far or is at a lower voltage. It can be up to five percent if energy is transmitted very far.

The business case is that a TSO needs to cover grid losses, and this means often having to purchase electricity at the last minute for a much higher cost. In 2018, 50 Hertz spent €70m on grid loss cover. The energy transition means that grid losses are increasing (e.g. from offshore wind parks) and that the grid loss range is more volatile.

In other words, when you have more renewables, this increases loss, and the intermittency of energy generation compounds the issue. It is a master of great importance that a TSO is able to predict grid loss. If we don't have an accurate prediction ahead of time, we have to spend more money on grid loss cover.

#### Image: Energy Data Analytics

A TSO is a government-regulated monopoly. It's in the interest of all consumers to improve forecasts. The data science team did this once they could get access to the energy data cloud. The team was able to integrate a lot more data points than previously. For example, data from 70 weather stations all around Germany. The initial model was a simple feedforward neural network with just one hidden layer.

### Deployment

The data science team realized quickly that the feedforward neural network provided more accurate predictions than the classical time-series model. Next, they were able to deploy quickly, and on their own, on the Agile Apps Platform. It runs on OpenShift, and this open-source container application platform makes deployment easy for anyone.

The Day-Ahead forecast is operative since December 2019. The feedforward neural network has over 100 inputs and a hidden layer with 50 nodes. From start to finish, this project took less than half a year. Furthermore, once everything is deployed on the agile platform, it makes it easy to update the model with new versions.

#### Image: Energy Data Ecosystem

