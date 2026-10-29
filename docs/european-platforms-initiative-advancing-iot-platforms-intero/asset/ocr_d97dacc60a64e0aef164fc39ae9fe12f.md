**_Hosted in a third party IoT platform:_** this scenario integrates TagItSmart functionality in an already existing IoT platform. Components implementation might need some adaptation to comply with the existing platform, yet they should be interoperable by following the correspondent API. Infrastructure needs are set up by the third party IoT platform provider.

**_Shared and hosted externally:_** this scenario considers TagItSmart as a standalone set of services that expose an open API and that can be accessed from different platforms simultaneously. Deployment and infrastructure needs are handled independently from the IoT Platform.

The components defined in Figure 4.12. are the set of components needed to fulfil the requirements extracted from the different use cases, while enabling creation and lifecycle management of the SmartTags. Based on the chosen integration strategy, mapping of some of the components to real implementations and deployments in a specific IoT platform will be different.

# Table 4.2. TagItSmart APIs example

| OPERATION | API | DESCRIPTION |
|---|---|---|
| SmartTag activation | POST /product/set-smart-tag-date | This method is used to activate the SmartTag to be enable it use in the system. |
| SmartTag scan | POST /product/product-context | This method is used to POST the location where the product was scanned and returns all related context for the product including reviews and sensor states. |
| SmartTag recycle | POST /recycl3r/api/v1/recycling_info | This method is used to get information about sorting and location for product recycling. |