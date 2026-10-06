In addition, many organizations default to REST for their API style choice when offering customer- and partner-facing Web APIs. Most select the REST-based API style internally because of the abundance of tooling, infrastructure, operational, and management support. Because REST builds on the patterns of the Web, it is familiar to developers, easily managed by ops teams, and offers an abundance of tools and libraries for producing and consuming APIs.

# REST API Design Process

Now that one or more APIs have been modeled, as described in Chapter 6, “API Modeling,” it is time to start the API design process. While the goal of API modeling is to explore and capture the API requirements into a series of API profiles, the API design process maps the API profiles into HTTP using the REST-based principles discussed earlier in this chapter. Most of the effort involved in API design was focused on modeling the API to produce the API profile, there are five quick steps to a high-level API design.

# Step 1: Design Resource URL Paths

Next, convert each resource name into a URL-friendly name using lowercase letters and hyphens in place of spaces. Start the path with a leading slash, followed by the resource name in pluralized form to denote that this is a collection of resource instances.

| Resource Path |
| Books |
| Book Authors |
| Carts |
| Cart Items |

**Figure 7.3** Begin by migrating the list of resources from the API profile created during modeling into a preliminary API design. Note that Cart Items is a dependent relationship, as detailed in Chapter 6, so it is indented slightly.