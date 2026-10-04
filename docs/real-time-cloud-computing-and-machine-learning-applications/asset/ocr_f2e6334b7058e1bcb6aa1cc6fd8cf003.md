# Server and Servlet Architectures for a Cloud-Based Real-Time ... 715

The SimpleRegression class estimates an ordinary least squares regression model with one independent variable. Observations are added one at a time into the simple regression model using the addData () method.

The codes for the Regression class are given in Listing 7.12.

# Listing 7.12. Regression Class

```
import org.apache.commons.math3.stat.regression.OLSMultipleLinearRegression;
import org.apache.commons.math3.stat.regression.SimpleRegression;

import java.util.Arrays;

/**
* Uses Common Math library from Apache for model creation.
* This class is responsible for generating either:
* - Multiple Linear Regression model or
* - Polynomial Regression Model-based for prediction.
*/
public class Regression {

    //define window size & degree for polynomial regression
    private int window, degree;
    //String to check regression type
    private String type;

    /**
     @param type sets the type of the regression model
    */
    public void setType(String type) {
        this.type = type;
    }

    /**
     @param degree sets the degree of the Polynomial Regression Model
    */
    public void setDegree(int degree) {
        this.degree = degree;
    }

    /**
     @param window Sets the window size for the regression model
    */
    public void setWindow(int window) {
        this.window = window;
    }
```