![](bbox=[0.36, 0.08, 0.64, 0.31])

FIGURE 2.4 Finding the Industrial Control Systems button within the Shodan page.

From the **Industrial Control Systems** page, several different protocols can be searched. Note in Figure 2.5 that any of the tags in Shodan require an Enterprise account before they can be searched.

![](bbox=[0.1, 0.41, 0.9, 0.76])

FIGURE 2.5 Exploring protocols in the ICS page for Shodan.

In this example, we’ll click on **Explore Modbus** to search for Modbus information indexed by Shodan. This opens a search for TCP port 502, we’ve added the string “Unit” into the search as well to remove any false positives for other services. In our search, we’ve identified over 32,000 systems with Modbus on the Internet! This is represented in Figure 2.6.