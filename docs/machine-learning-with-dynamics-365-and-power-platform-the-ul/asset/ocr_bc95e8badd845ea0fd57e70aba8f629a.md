+   iii. When you post a prepayment invoice, the system creates a voucher, recorded as a liability in vendor transactions.
+   
+   iv. The system uses settings in the accounts payable parameters to specify which profile must be linked to the prepayment invoice.
+   
+   v. Once the prepayment invoice is created, the system links the profile with it.
+   
+   vi. Now to pay a prepayment invoice, you can use payment proposals.

Now that we have understood some essential functions of the Accounts Payables module in Dynamics 365 Finance, let us see how this system automates vendor invoices processes.

Vendor invoices are like a request or a bill produced to initiate the payment process for provided ongoing services and for specific items and services. It is generated when a purchase order placed with a vendor for services or products is fulfilled. The vendor invoice comprises a header and one or multiple lines for products and services. A vendor invoice can be created with the following steps:

+   1. If your purchase orders are confirmed, you can use Open vendor invoices and Pending vendor invoices pages to create Vendor Invoice.

+   2. Use invoice register to enter invoices that are not in reference to any specific purchase order so that you can accrue the expense. Later you can use the vendor invoice approval journal to post them to the vendor balance to reverse the accrual.

Once created, vendor invoices must go through a review process wherein the invoice header, the invoice line, or both are reviewed. Some scenarios can prevent your vendor invoice from being submitted to a workflow:

# **Scenario 1: When the registered invoice total value and invoice total value is different.** There is a feature on the Feature Management page that enables you to obstruct vendor