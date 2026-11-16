can be more useful. There are other places we can go to get lists of people who belong to a target organization. Again, there are utilities we can use to help us gather this information. One of them is theHarvester. This is a script that will search through different sources to locate contact information based on a domain name provided to the program. In the following code, you can see the output from theHarvester run against the domain wiley.com, using Google as the search source.

# theHarvester Output

```
$ theharvester -d wiley.com -b google
*********************************************************************************
*
*   |  _| |_   _____  /\ /\__   ____ _  ___ ___  /_  __/__   ____ | |_ _   _  *
*   |  _| ' \/ / _ \ \/ // '_ \ / _` |/ __/ _ \ \ \/ / '_ \ / _ \| __| | | | *
*   | |_| | | |  __/\ V /| | | | (_| | (_|  __/  >  <| | | | (_) | |_| |_| | *
*   \__|_| |_|\___| \_/ |_| |_|\__,_|\___\___| /_/\_\ |_|\___/ \__|\__,_|    *
*                                                                              *
*   TheHarvester Ver. 2.7.2                                                   *
*   Coded by Christian Martorella                                             *
*   Edge-Security Research                                                     *
*   cmartorella@edge-security.com                                             *
*********************************************************************************

[+] Starting harvesting process for domain: wiley.com
[-] Searching in Google:
    Searching 0 results...
    Searching 100 results...
    Searching 200 results...
    Searching 300 results...
    Searching 400 results...
    Searching 500 results...

Harvesting results

[+] Emails found:
----------------------------------
hbaumgar@wiley.com
respinosa@wiley.com
cs-journals@wiley.com
cochrane@wiley.com
sciencenewsroom@wiley.com
```