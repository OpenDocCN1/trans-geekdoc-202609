# FIGURE 2.20 Page structure that includes dynamic form generation

![](bbox=[0.22, 0.11, 0.85, 0.26])

# FIGURE 2.21 Including an action object and specialised server pages

![](bbox=[0.22, 0.32, 0.85, 0.52])

it possible for the server to guarantee that it can handle the client's session, and it is also possible for the server page to build, and rebuild, the form page so that, if the user makes a mistake when filling in the form, a new form page can be provided that contains the data they have already entered along with the necessary error messages, to help them to correct their entries.

Now, the server page dynamically generates a client page with a form, which submits back to the same server page until the next client page can be generated. Although this is a somewhat simple model, it provides the basic static structure that can provide the foundation for a dynamic webflow. There is a problem, however in that the server page is now tasked with making decisions about the webflow and generating one of two possible pages, either an updated form or the next client page. To provide a better separation of concerns a common architectural approach is to include an action object that takes responsibility for webflow decisions. The action object can then delegate to further server pages to either regenerate the form page or build the next client page (Figure 2.21).

# Modelling dynamic webflow

The diagrams we have used so far are static diagrams showing the relationships between different web components. In order to visualise the dynamic webflow that these components contribute to, it can be useful to sketch some sequence diagrams. The sequence diagram in Figure 2.22 includes some of the participating components from the static model in Figure 2.21, identifying the messages that pass between them over time. In this case, we are only modelling the situation where the original form does not have to be regenerated, but this can easily be added to the diagram using a condition, as we did in Figure 2.16.

The diagram in Figure 2.22 represents the typical interactions in one request–response cycle for a web application. However, before digging any deeper into our own designs we