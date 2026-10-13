
The Enterprise Agreement (EA) is a special-purpose contract intended for larger businesses that are willing to commit to a three-year Azure subscription. Microsoft offers EA customers special discounts on Azure services and provides them a special management portal for analyzing spending, creating budgets, tracking use, and so forth.

Under EA, you pay your yearly fee up front and must use it or lose it. If you commit to $12,000 for the first year and spend only $9,000 by December 31, for example, you lose the remaining $3,000. At the end of each contract year, however, you can adjust your fee for the upcoming year to better match your use and expectations.

Several other Azure subscription offers grant recurring monthly credits, including these:

*   **Visual Studio:** Given to those who have a Visual Studio Online subscription
*   **Action Pack:** Given to Microsoft Partner Network members
*   **Azure for Students:** A free credit ($100) over 12 months for students with a verified academic email address
*   **Azure Pass:** Normally granted by Microsoft to Azure user groups and educational institutions, and intended for free distribution

### Creating a free Azure account

To sign up for an Azure free account, you need an Internet connection and any modern web browser.

![Tip](images/tip.png) I suggest that you perform this procedure (and all procedures in this book) on a desktop or laptop computer rather than a tablet or smartphone. Microsoft makes the Azure portal as mobile-friendly as possible but given the amount of typing you’ll be doing, I recommend using a larger computer.

Follow these steps to create your account:

1.  **Browse to** [`https://azure.microsoft.com/en-us`](https://azure.microsoft.com/en-us/) **and look for a free-account.**

    Microsoft changes the Azure website regularly, so I hesitate to ask you to look in a particular spot for the link or a button. Somewhere on the page, you’ll find the link or button to click.

2.  **Sign in with your Microsoft account, or create a new one.**

    The Azure free account is a Microsoft account, which powers all of the company’s online services, including Xbox and Office 365. If you already have a Microsoft account, however, you may want to create a new one exclusively for Azure use. I suggest this because you probably want to keep your Azure business completely isolated from, say, your Xbox leisure.

3.  **In the About You section, provide your contact details, and click Next.**

    Microsoft needs this information to set up your Azure subscription. It also uses your telephone number, email address, and payment details to verify your identity.

4.  **In the Identity Verification by Card section of the next page, provide valid credit card details.**

    Note that you can’t use a prepaid credit card or gift card; the card has to be a legitimate credit or debit card with your name and billed to your address. Microsoft won’t charge your account unless you upgrade to a paid subscription offer. That said, Microsoft may put a $1 verification hold on your credit card account; this hold is lifted within three to five business days.

    You can have only one Azure free account, and Microsoft performs the identity verification in part to prevent fraud.

5.  **In the Agreement section, confirm that you agree to the subscription agreement, offer details, and privacy statement; then click Sign Up.**

6.  **On the You’re Ready to Start with Azure page that appears, click Go to the Portal.**

    You’re done and ready to rock. That was easy, wasn’t it?

You should now see the Azure portal, along with a Welcome to Microsoft Azure message, as shown in [Figure 1-6](#c01.xhtml#c01-fig-0006).

![FIGURE 1-6: Signing in to the Azure portal for the first time.](images/9781119612148-fg0106.png)

[FIGURE 1-6:](#c01.xhtml#rc01-fig-0006) Signing in to the Azure portal for the first time.

I formally introduce the Azure portal in [Chapter 2](#c02.xhtml). For now, bookmark this address ([`https://portal.azure.com`](https://portal.azure.com)), because you’ll be using it a lot from now on.

Click Start Tour to take a spin around the Azure portal. In the background of [Figure 1-6](#c01.xhtml#c01-fig-0006), you see the Quickstart Center; you can return to this blade at any time by typing **quickstart center** in the Search box on the top navigation bar. The Quickstart Center contains links to the documentation and to Microsoft Learn, Microsoft’s free Azure education portal.

![Remember](images/remember.png) The windows in the Azure portal are called *blades*.

### Viewing subscription details

Follow these steps to view your Azure free-account subscription details:

1.  **Type** `subscriptions` **in the Search box in the Azure portal.**

    The Subscriptions option should appear almost instantly. (I’m a huge fan of the global search feature in the Azure portal, and I hope you’ll become one too.)

2.  **In the Subscriptions blade, select your Free Trial subscription.**

    Before you click Free Trial, notice the information that the Subscriptions blade gives you: Your account role is Account Admin, and the status of the account is Active. So far, so good.

3.  **Examine the various subscription management tools.**

    [Figure 1-7](#c01.xhtml#c01-fig-0007) shows the following tools:

    *   **A:** The Overview setting shows you the Essentials panel (shown on the right side of the figure), where you see details on your subscription status and metadata.
    *   **B:** The Cost Management settings enable you to report on the Azure service you’ve consumed and/or are currently consuming.
    *   **C:** The Payment Methods setting enables you to change the payment method associated with your subscription.
    *   **D:** Upgrade Subscription enables you to convert your free trial to a PAYG subscription. If you convert before you spend the $200 or reach the 30 days, you keep your credit before the cost meter starts ticking.
    *   **E:** The Manage button takes you to the Azure Account Center, where you can print past service invoices, set billing alerts, and change the account that owns the subscription. ![FIGURE 1-7: Viewing your Free Trial subscription in the Azure portal.](images/9781119612148-fg0107.png)

        [FIGURE 1-7:](#c01.xhtml#rc01-fig-0007) Viewing your Free Trial subscription in the Azure portal.

    *   **F:** The Cancel Subscription button enables you to … well, cancel your subscription. What else?
    *   **G:** The Rename button enables you to change the logical name of your subscription from Free Tier to something more meaningful to you and your organization.

If you decide to upgrade your subscription, Microsoft asks whether you want to buy a monthly support plan. As with the PAYG subscription, you can cancel a support plan at any time with no penalty. The three support tiers, each of which has a fixed monthly cost, are

*   **Developer plan:** Support for trial and nonproduction environments. You can interact with Azure support staff members from 9 a.m. to 5 p.m. in your time zone, with an initial response time of less than 8 business hours. As of this writing in November 2019, the monthly cost is $29.
*   **Standard plan:** Support for production environments. You receive 24/7 technical support and a response within 2 hours. As of this writing, the Standard plan costs $100 per month.
*   **Professional Direct plan:** Support for businesses that rely heavily on Azure. You get 24/7 technical support and a response for critical issues within one hour. As of this writing, Microsoft charges $1,000 per month for this support plan.
*   **Premier plan:** This support tier is aimed at businesses that want not only lightning-fast technical support but also architectural guidance from Microsoft Azure solutions experts. You need to contact Microsoft to get a Premier plan price quote.
