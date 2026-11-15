Then, initialize a single-node H2O instance using the h2o.init() function on eight cores and instantiate the corresponding client module on the IP address localhost and port number 54321:

```
# Initialize H2O instance (single node)
localH2O = h2o.init(ip = "localhost", port = 54321, startH2O = TRUE, min_mem_size = "20G", nthreads = 8)
```

# # How to do it...

The section shows how to build neural network using H20.

+   1. Load the occupancy train and test datasets in R:

```
# Load the occupancy data
occupancy_train <-
read.csv("C://occupation_detection/datatraining.txt",stringsAsFactors = T)
occupancy_test <-
read.csv("C://occupation_detection/datatest.txt",stringsAsFactors = T)
```

+   2. The following independent (x) and dependent (y) variables will be used to model GLM:

```
# Define input (x) and output (y) variables
x = c("Temperature", "Humidity", "Light", "CO2", "HumidityRatio")
y = "Occupancy"
```

+   3. Based on the requirement by H2O, convert dependent variables to factors as follows:

```
# Convert the outcome variable into factor
occupancy_train$Occupancy <- as.factor(occupancy_train$Occupancy)
occupancy_test$Occupancy <- as.factor(occupancy_test$Occupancy)
```

+   4. Then convert the datasets to H2OParsedData objects:

```
# Convert Train and Test datasets into H2o objects
occupancy_train.hex <- as.h2o(x = occupancy_train,
```