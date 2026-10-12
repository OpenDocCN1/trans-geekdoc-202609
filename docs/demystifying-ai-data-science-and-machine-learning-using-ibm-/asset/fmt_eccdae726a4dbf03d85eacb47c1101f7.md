
# Appendix A: Bank Marketing Data—Variable Descriptions

| Variable Name | Description | Scale | Role |
|---|---|---|---|
| INAREA | Local Address | Binary (Flag) | Input |
| INCOME | Income | Continuous | Input |
| INV | Investment | Binary (Flag) | Input |
| INVBAL | Investment Balance | Continuous | Input |
| IRA | Retirement Account | Binary (Flag) | Input |
| IRABAL | IRA Balance | Continuous | Input |
| LOC | Line of Credit | Binary (Flag) | Input |
| LOCBAL | Line of Credit Balance | Continuous | Input |
| LORES | Length of Residence | Continuous | Input |
| MM | Money Market | Binary (Flag) | Input |
| MMBAL | Money Market Balance | Continuous | Input |
| MMCRED | Money Market Credits | Continuous | Input |
| MOVED | Recent Address Change | Binary (Flag) | Input |
| MTG | Mortgage | Binary (Flag) | Input |
| MTGBAL | Mortgage Balance | Continuous | Input |
| NSF | Number Insufficient Fund | Binary (Flag) | Input |
| NSFAMT | Amount NSF | Continuous | Input |
| PHONE | Number Telephone Banking | Continuous | Input |
| POS | Number Point of Sale | Continuous | Input |
| POSAMT | Amount Point of Sale | Continuous | Input |
| RES | Area Classification | Nominal | Input |
| SAV | Saving Account | Binary (Flag) | Input |
| SAVBAL | Saving Balance | Continuous | Input |
| SDB | Safety Deposit Box | Binary (Flag) | Input |
| TELLER | Teller Visits | Continuous | Input |
| CRSCORE | Credit Score | Continuous | Target |

# Appendix B: Airline Passengers Data—Variable Description

| Variable Name | Description | Scale | Role |
|---|---|---|---|
| Gender | Gender | Binary (Flag) | Input |
| Customer_Type | Customer type | Nominal | Input |
| Age | Age | Continuous | Input |
| Type_of_Travel | Type of travel | Nominal | Input |
| Class | Ticket class | Nominal | Input |
| Flight_Distance | Flight distance | Continuous | Input |
| Inflight_wifi_service | Passenger evaluation of inflight Wi-Fi service | Continuous | Input |
| Departure_Arrival_time_convenience | Passenger evaluation of departure/arrival time convenience | Continuous | Input |
| Ease_of_Online_booking | Passenger evaluation of ease of online booking | Continuous | Input |
| Gate_location | Passenger evaluation of gate location | Continuous | Input |
| Food_and_drink | Passenger evaluation of food and drink | Continuous | Input |
| Online_boarding | Passenger evaluation of online boarding | Continuous | Input |
| Seat_comfort | Passenger evaluation of seat comfort | Continuous | Input |
| Inflight_entertainment | Passenger evaluation of inflight entertainment | Continuous | Input |
| On_board_service | Passenger evaluation of on-board service | Continuous | Input |
| Leg_room_service | Passenger evaluation of legroom service | Continuous | Input |
| Baggage_handling | Passenger evaluation of baggage handling | Continuous | Input |
| Checkin_service | Passenger evaluation of check-in service | Continuous | Input |
| Inflight_service | Passenger evaluation of inflight service | Continuous | Input |
| Cleanliness | Passenger evaluation of cleanliness | Continuous | Input |
| Departure_Delay_in_Minutes | Departure delay in minutes | Continuous | Input |
| Arrival_Delay_in_Minutes | Arrival delay in minutes | Continuous | Input |
| Return | Passenger decision in returning to the same airline in the next flight (0—No; 1—Yes) | Binary (Flag) | Target |

# Appendix C: Boston Housing Data—Variable Descriptions

| Variable Name | Description | Scale | Role |
|---|---|---|---|
| CrimePC | Crime rate per capita | Continuous | Input |
| ZonePr | Proportion of residential land zoned for lots over 25,000 sq.ft. | Continuous | Input |
| IndustPr | Proportion of non-retail business acres. | Continuous | Input |
| Charles_River | Charles River dummy variable (1 if tract bounds river; 0 otherwise) | Continuous | Input |
| NiOxSQ | Nitric oxides concentration (parts per 10 million) | Continuous | Input |
| RmSQ | Average number of rooms per dwelling | Continuous | Input |
| AgePre40 | Proportion of owner occupied units built prior to 1940 | Continuous | Input |
| LogDisstance | Weighted distances to five Boston employment centers | Continuous | Input |
| LogAccess | Index of accessibility to radial highways | Continuous | Input |
| Tax | Full value property tax rate per $10,000 | Continuous | Input |
| PtRatio | Pupil-teacher ratio | Continuous | Input |
| B | 1,000(Bk − 0.63)^2 where Bk is the proportion of blacks by town | Continuous | Input |
| Lstat | Percentage of lower status of the population | Continuous | Input |
| Imv | Median value of owner-occupied homes in $1,000s | Continuous | Target |

# Term Definitions

| Terms | Definitions |
|---|---|
| Activation function | An activation function is a function that determines the output of a neuron based on the weighted sum of its inputs. Common activation functions include sigmoid, ReLU (Rectified Linear Unit), and tanh (hyperbolic tangent). |
| Actual by predicted chart | The actual by predicted chart compares the actual values with the predicted values, showing us how well the trained model fits the data. |
| Adaptive stepwise | Adaptive stepwise is a forward stepwise method that allows removing a variable currently in the model but no longer significant. It is adaptive. |
| Aggregation methods | Ensemble models combine the predictions of base learners using aggregation methods. Common aggregation methods include averaging, voting, and weighted voting. The aggregated result is often more accurate and reliable than the predictions of individual models. |
| Artificial Intelligence (AI) | AI is the simulation of human intelligence in machines, enabling them to perform tasks that typically require human cognition, such as learning, reasoning, problem-solving, perception, and language understanding. |
| Association model | A predictive model with an interval target variable. |
| Backward propagation (or backpropagation) | Backward propagation is the process of adjusting the weights and biases in the network based on the prediction error. It involves calculating the gradients of the loss function and adjusting the parameters to minimize the error. |
| Backward stepwise | Backward stepwise is the method in which the model starts with all predictor variables, and at each step, the variable that contributes the least to the model's performance is removed until no further improvement is achieved or a predefined stopping criterion is met. |
| Bagging | Bagging is an ensemble method that involves training multiple base learners independently on different random subsets of the training data (sampling with replacement). The final prediction is typically an average or voting over the predictions of all the base learners. |
| Bar chart | A bar chart is a graphical representation of categorical data that use rectangular bars of varying lengths to visualize the frequency or count of each category. |
| Base learners (individual models) | Base learners are the individual models that constitute the ensemble. Base learners can be any machine learning algorithm, such as decision trees, support vector machines, neural networks, etc. |
| Bayes’ theorem | Bayes’ theorem is a fundamental equation used in Bayesian networks to update probabilities based on new evidence. It calculates the posterior probability of an event given prior knowledge and observed evidence. |
