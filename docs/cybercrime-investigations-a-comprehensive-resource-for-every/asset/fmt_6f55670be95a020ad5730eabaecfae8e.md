
## 11.7 Records Evidence

The crux of a cybercrime investigation often comes down to records – the information compiled and stored by Internet service and communication providers, financial institutions, merchants, and other businesses and organizations documenting the trail of crime online. One set of records generates leads that require more sets of records, starting a continuing cycle of seeking and analyzing records until the crime is solved and the criminal identified.

Because records are often the most important type of evidence in a cyber case, this chapter focuses on the two key aspects of handling records evidence. First, we will look at methods for gathering and organizing records evidence to efficiently keep track of the information coming in to the investigation. And second, we will discuss techniques for analyzing records to get the most information and evidence possible.

### 11.7.1 The Workflow for Records Evidence

The workflow for seeking and reviewing records looks something like this:

*   Start a Grand Jury investigation, civil suit, or administrative case
*   Send a Letter of Preservation (if warranted)
*   Determine what legal tool should be used to get the needed information
*   Obtain that legal process (subpoena, search warrant, etc.)
*   Serve the legal documents
*   Await response
*   Analyze records
*   Repeat

1.  **Start a Grand Jury investigation, civil suit, or administrative case**. Investigators seeking records from a business or organization usually get them using some form of legal demand in connection with an official case or investigation. In most criminal cases, the process starts with opening a Grand Jury investigation through the prosecutor’s office that has jurisdiction. For private sector investigations, issuance of legal process (subpoenas) may require filing a civil lawsuit. Government agencies with administrative subpoena authority will create a case or investigation within their internal system.

2.  **Send a letter of preservation if warranted**. When an account or event connected to the case is identified, investigators should consider sending a letter of preservation to the company holding the relevant records. As we learned in [Chapter 7](#chapter07.xhtml), this letter alerts the company that the designated records should be found and maintained pending the receipt of future legal process compelling their disclosure (such as a subpoena or search warrant). When there is a delay in starting a case or obtaining legal process, the letter of preservation may ensure records are not deleted.

3.  **Determine what legal tool should be used to get the records.** In earlier chapters, we learned about the legal tools available to private, regulatory, and law enforcement investigators to compel individuals and businesses to produce records. Which tool to use depends upon the type of investigation, the nature of records, the type of entity that possesses them, and the pertinent laws and statutes regulating law enforcement or other parties’ access. Remember that consent is often an option to consider. Occasionally, records can be obtained just by asking for them.

4.  **Obtain the necessary legal process**. Once investigators have determined what tool should be used, they must take the necessary steps to obtain the subpoenas or court orders.

5.  **Serve the legal documents**. Legal process needs to be served properly according to federal or state rules, though many organizations and individuals will waive some of these requirements. Most Internet and phone service providers, financial institutions, and retail chains have dedicated units for receiving subpoenas, search warrants, and other court orders.

6.  **Await the response**. When the subpoena or court order is properly obtained and served, the person or entity to which it is directed has a specified timeframe within which to comply. The timeframe may depend upon relevant state or federal law, and would be indicated on the document.

7.  **Analyze the records**. We will cover more details on how to conduct the analysis later, but here we state the obvious – there is no point going through the trouble of obtaining records if they are not carefully reviewed for evidence and new leads.

8.  **Repeat**. The process of obtaining records through legal process is cyclical, and likely will involve many iterative rounds.

#### Starting Out on the Records Trail

A rookie cybercriminal used a stolen credit card to make a purchase online from `Cybrseller.com`. To do this, he accessed the Internet, opened his web browser, then typed “`Cybrseller.com`” into the address bar. The domain name system routed him to the server where the Cybrseller website was hosted. He then conducted the fraudulent transaction with the stolen credit card data.

A law enforcement investigator receives a report about this crime from the credit card’s owner. The investigator asks the local District Attorney’s office to open an investigation in the Grand Jury, and then obtains a Grand Jury subpoena directed to Cybrseller, demanding all information about the purchase, all information provided by the purchaser, and any IP addresses used.

Cybrseller responds with the information requested. The company’s records indicate that the fraudulent purchase was made on December 1, 2019, at 4:45 pm EST by a user with IP address `71.123.165.147` (a public IP address, of course).

Now a new round of records work begins. The investigator needs to find out who was using that IP address at that specific date and time. First, the investigator has to figure out which Internet service provider (ISP) has been assigned this IP address. There are several open source (free) and reliable IP address look-up services online, such as the `ARIN Whois IP Address Database search tool` and the website `search.org`. The investigator types in the IP address supplied by Cybrseller and the search tool provides the name of the Internet service provider to which the IP address has been assigned.

The investigator sees that IP address `71.123.165.147` is administered by Great Cable LLC, and prepares a Grand Jury subpoena for Great Cable, asking for all subscriber information about the customer who was using that particular IP address at that date, time, and time zone.

When this IP address information is gathered, it will inevitably create new questions and data points that require another round of investigation and records – and the hunt will continue as the circle closes.

### 11.7.2 Tracking Records Requests

With the first inkling that records are going to be needed in an investigation, it is incredibly helpful to create a simple system that organizes the requests made and responses received. Without a system, investigators can quickly lose track of these requests or inadvertently request the same material twice. A tracking system is especially important when more than one investigator or staff member is working on obtaining records evidence. It can be amazing how quickly one subpoena for some subscriber information or credit card transactions quickly turns into a dozen follow-up requests, and on and on.

Tracking can be as easy as creating a spreadsheet, a log, or even a poster on the wall. Some key details to include in the tracking system are:

*   **Description of the information sought in each records request**
    *   Account names, type of information sought, date range, etc.
*   **Entity/person providing the requested records/items**
    *   The email provider, phone service provider, bank, etc.
*   **Letters of Preservation sent and date**
*   **Type of legal tool used**
    *   Subpoena, `2703(d) Order` or search warrant
*   **Date legal process was issued**
*   **Date material due from provider/business**
*   **Date material received from provider/business**
*   **Presence of non-disclosure order**
*   **Expiration date of non-disclosure order**
*   **Continued non-disclosure orders and expiration dates**
