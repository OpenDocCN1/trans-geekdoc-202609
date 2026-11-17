# RESULTS AND DISCUSSION

In this section, we present the results of the federated learning experiments on a test dataset. The results are generated on a local device i.e. client-side and on the aggregated server model. The procedure is demonstrated in Fig. (2). The models trained on the client devices are aggregated and the global server model is updated. Here, we use the “FedAvg” algorithm to aggregate the local models by averaging their model parameters.

Categorical cross-entropy is used to evaluate the loss of the models. Categorical cross-entropy is suited for multi class classification as one image can belong to one category with a probability of 1, while other categories are given a probability of 0.

![](bbox=[0.216, 0.37, 0.776, 0.67])

Fig. (2). Procedure followed for updating the server model.

In the table above, each model is subdivided into- client 1, client 2, client 3, and server. Here, each client is the local hospital/organization and the server is the final global aggregated server. First, each client is given the deep learning model which is trained on their individual dataset. The clients are evaluated locally and then they communicate the model parameters to the server. Each client sends its model parameters to the server, here we have 3 models, so there will be 3 model parameters that will be aggregated by the FedAvg algorithm on the server.