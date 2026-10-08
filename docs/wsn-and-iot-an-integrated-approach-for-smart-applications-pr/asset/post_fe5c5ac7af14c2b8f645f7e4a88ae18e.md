
# Privacy-Preserving Machine Learning on Non-Co-Located Datasets

local models are exchanged and integrated to create the finalized global model [6]. The global model is then made available to the participants. This technique minimizes the danger of data leaking by ensuring sensitive data stays on local devices.

Using federated learning on datasets that are not geographically close to one another has a number of advantages. First, it does away the requirement for physical data centralization, which lowers the cost of data transport and storage and enables more effective data integration and analysis. Federated learning generates more and applicable findings by training models on a variety of different data sources [7]. The models are developed to take each dataset's unique characteristics into consideration. Federated learning also protects data privacy by keeping information locally. This helps to protect privacy and lessen the possibility of data breaches.

Federated learning enables collaboration across companies or organizations even when data is stored in different physical locations. By enabling users to train models simultaneously without releasing their data, it promotes knowledge and resource sharing. This collaborative approach may enhance data-driven decision making in various industries, including healthcare, banking, and transportation [8].

The introduction discusses the difficulties of integrating and analyzing datasets that are not physically located in the same location. It advocates using federated learning to address these problems while preserving the security and privacy [9]. Federated learning on remote datasets provides a number of benefits, which are all underlined, including improved model performance, data integration, privacy protection, and cooperation [10]. The technical elements, difficulties, and promise of federated learning on non-co-located datasets will be covered in greater detail in the next sections of the chapter, and this section serves as the foundation for debate [11].

“Federated learning,” a new approach to machine learning (ML), enables users to train a single model utilizing data from several dispersed sources without sharing any of the raw data. This section explores the fundamentals of federated learning as well as several methods for tackling the problem, such as horizontal and vertical federated learning [12].

Federated learning is based on distributed model training and prioritizes protecting users’ private information [13, 14]. The following are some of key ideas:

- i. Local model learning: As of this process, each device or organization trains its own local model using its own data. There are several ways to achieve this. The raw data is never exposed to the outside world because this training is performed internally on the device.
- ii. Model aggregation: We pool and aggregate the modifications made to the local models to produce the global one. This process is known as “model aggregation.” The process of aggregation utilizes a variety of methods, such as secure multi-party computation and homomorphic encryption, while maintaining the privacy of locally updated models.
- iii. Iterative learning: The aggregation procedure is carried out iteratively so that the global model can get better over time. Each step entails trading model updates in a round, collecting those updates, and then distributing the revised global model to the iteration’s participants.

## 14.2.2 HORIZONTAL FEDERATED LEARNING

When several entities share some qualities but have distinct distributions, horizontal federated learning is most useful. Without requesting participants’ raw data, the objective is to jointly train a model that can generalize across all these factors [15]. This is shown in Figure 14.3. The following is a summary of the essential stages of horizontal federated learning:

- i. Data partitioning: Each entity splits its data into sets while simultaneously ensuring that no raw data is sent outside of the device. This partitioning is done using any technique that produces subgroups that are easily discernible.
- ii. Model training: Each organization uses its particular subset of data to train its own local model. This training can be done using common ML techniques or specialized privacy protection strategies like differential privacy.
- iii. Model aggregation: Model changes are frequently transmitted by the entities to a coordinating server model weights or gradients. This process is

![](img/a29e06af76c776aadcc01782d636c0d5_342_0.png)

FIGURE 14.3 Horizontal federated learning.

referred to as “model aggregation.” In order to give a current global model, the server integrates the changes after performing encrypted aggregation algorithms on them.
- iv. Global model distribution: Until convergence is attained, the cycle of local training, model aggregation, and global model distribution is repeated. The updated global model is then disseminated to all entities.

## 14.2.3 Vertical Federated Learning

When several entities join jointly train a model without disclosing their own data and possess features or attributes that are complimentary to one another, vertical federated learning is a viable technique to use [16]. The following list summarizes the main steps of vertical federated learning, as shown in Figure 14.4.

- i. Data preprocessing: Data is generally transformed from each entity’s native format into a common feature space or representation. Even if the raw data is not used, this preparation assures compatibility and enables cooperative training to take place.
- ii. Local model training: Each entity trains its local model utilizing its preprocessed data and focused on its own distinct attributes. The training may make use of several machine learning methods or strategies to handle vertically partitioned data.

![](img/a29e06af76c776aadcc01782d636c0d5_343_0.png)

FIGURE 14.4 Vertical federated learning.
- iii. Model aggregation: Updates to the model, such as model weights and gradients, are sent between the local models and a coordinating server. This process is known as “model aggregation.” In order to make a global model available, the server safely aggregates the modifications.
- iv. Global model distribution: Until convergence is attained, the cycle of local training, model aggregation, and global model distribution is repeated. The updated global model is then disseminated to all entities.

## 14.2.4 Other Approaches to Federated Learning

There are many different methods and federated learning in addition to horizontal and vertical federated learning. These include federated reinforcement learning and transfer learning, which train models through interactions with remote environments and employ previously trained models to improve performance [17]. The applications of federated learning might be considerably expanded by using these strategies in a variety of settings.

Transfer learning advantages are brought to dispersed settings using federated transfer learning. With this configuration, models are initially trained on a sizable common dataset before fine-tuned using data collaboratively. Federated transfer learning is a further development of transfer learning [18]. The pre-trained models’ insights might be used by entities with less data using this method, improving overall performance and generalization.

Federated reinforcement learning is a technique that combines federated learning (RL) strategies with the philosophy and practices of federated learning. Organizations that employ this strategy collaborate with their local communities to acquire data and shape policies. The policies are then compared to one another and compiled into a single document to create a global policy that reflects the expertise of all the relevant organizations. This enables the preservation of private data when group work is being done in a decentralized environment.

As the discipline develops, federated learning continues to take on new forms and application techniques. Skewed data distributions can be a problem, although techniques like model compression and adaptive learning rate scheduling can assist. These strategies all share the desire to make communication easier.

Federated learning is a potential approach for developing ML models on separate datasets while preserving the confidentiality and privacy of data. Federated learning in this situation might be vertical or horizontal. Each method is designed to be effective with a particular set of facts and circumstances. Federated learning has been expanded into different versions using a variety of methodologies, including federated transfer learning and federated reinforcement learning, in order to improve performance and enable collaborative learning to occur in decentralized scenarios [19]. The application of these methodologies will enable fascinating developments in ML and data analytics as federated learning progresses, without the necessity of using physically co-located datasets.
