# Server and Servlet Architectures for a Cloud-Based Real-Time ... 759

The response (int r_window, int ptime) method is responsible for calculating prediction using all the four machine learning algorithms. The only difference, in this case, is that data can be fetched from a local database or the Cloudant platform. The results are concatenated together in a String. The codes for the response() method are given in Listing 7.26. The codes for performing prediction using the four algorithms have already been explained in Section 7.1.13.

Listing 7.26. response (i) method that performs prediction using all ML algorithms

```
public JSONObject response(int r_window, int ptime, String source) {
    // Data Window for Neural Network
    int window = 4 * 24 * 7;
    int tf = 4 * 24;
    int tn = 1;
    // Data Window for Regression Model
    int pred_t = r_window + ptime;
//////////// RETRIEVE DATA FROM CLOUD ///////
    // Create a DataRetriever Object to fetch data from the cloud
    DataRetriever dataRetriever = new DataRetriever();
    // Create a DataRetriever Object to fetch data from the cloud
    SQLConnector sqlConn = new SQLConnector();
    double[][] network_data, regress_data;
    // Initializes to store values
    if (source.equals("cloud")) {
        System.out.println("Using data from cloudant...");
        // extract the data
        network_data = (double[][])dataRetriever.getDataArray("",
window[0]);
        regress_data = (double[][])dataRetriever.getDataArray("",
r_window[0]);
    } else {
        System.out.println("Using data from MySQL...");
        network_data = (double[][])sqlConn.fetchLast(window)[0];
        regress_data = (double[][])sqlConn.fetchLast(r_window)[0];
    }

    // convert the data array to float
    float[][] converted = convertFloat(network_data);
```