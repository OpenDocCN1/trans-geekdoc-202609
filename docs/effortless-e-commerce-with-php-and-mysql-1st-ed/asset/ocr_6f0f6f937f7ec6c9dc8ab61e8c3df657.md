# PROCESSING CREDIT CARDS

The next step in the checkout sequence is to actually process the payment (this is number 3 in Figure 10.14). To do so, the customer information, payment data, and order specifics need to be sent to the payment gateway, and the returned response needs to be confirmed. With the Authorize.net system, this really isn’t that difficult. The site just needs to establish the right settings and use libcurl to contact Authorize.net.

I’ve broken the gateway communication into two scripts: one that establishes the particulars to be sent to Authorize.net for a new order and another script that performs the actual communication. I separated the functionality this way because the administrative pages will also communicate with Authorize.net, passing along slightly different information. After completing Chapter 11, “Site Administration,” there will be two setup scripts and one process script:

+   - gateway_setup.php establishes new order parameters.
+   - gateway_setup_admin.php establishes existing order parameters.
+   - gateway_process.php establishes common parameters and performs the request.

After defining two of these here, billing.php will need to be updated to use them.

# Creating gateway_setup.php

The payment gateway needs to receive a large number of name=value pairs in each request. These pairs communicate to the gateway everything required to process the transaction:

+   - The site's merchant information
+   - The customer's billing information
+   - The order information
+   - How data should be returned
+   - And more

Each payment gateway differs as to what information needs to be transferred and under what naming scheme. For Authorize.net, each name begins with x_.

The easiest way to start this process is to create an array, which will later be turned into the name=value pairs. The gateway_setup.php should create the