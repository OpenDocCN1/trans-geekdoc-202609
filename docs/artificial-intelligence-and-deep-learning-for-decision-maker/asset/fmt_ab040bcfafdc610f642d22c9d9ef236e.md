
Uber works as a location-based startup from day one. To create the model of Uber, manufacturers need to understand the specifics of iOS and Android geolocation features. Let us go through the important features that should be considered:

* **Identifying a device's location:** The Uber app that works on iOS system uses the `Core-Location` framework to find a user's device. The `Core-Location` framework provides protocols to configure and schedule the location delivery and send back location events to the server. The `Core-Location` framework also helps Uber to define geographic locations and monitor a device's movements as it crosses the boundaries. For Android version of the Uber app, geolocation was implemented using Google's `Location APIs` that can manage location technology and meet various other development needs when implementing location-based features.
* **Providing driving directions to the driver:** To display point-to-point directions on a map, developers of the Uber app used `MapKit` for the iOS version. Registering the app as a routing application makes routes available to the Maps application and all other mapping software on a user's device. In Android, routes and directions are made possible by the `Google Maps Android API`.
* **Integrating Wi-Fi mapping software:** As `Google Map` is integrated with Uber; it helps Uber find the location for both iPhone and Android versions of their application. But `Google Maps` is not the only service that Uber uses. To avoid paying Google for access to their solutions, Uber buys mapping technology companies to solve their logistics issues.
* **Push notifications and SMS:** The user can receive these messages as SMS or push notifications. After a client books a ride, Uber sends some notifications such as:
  * when a driver accepts your request
  * when the driver is about to reach its destination
  * when a ride has been canceled due to some reason
* **Payment integration:** Uber prefer to make their system cashless. The user can pay cash, pay via debit or credit card, or use a promo code; these modes of payment remove any human-to-human transactions. When accepting card payments, there are specific requirements that companies must comply with. Uber can also use PayPal's `Cardio` service for the scanning of credit cards on iOS. In Android, users need to manually enter credit card data to link a card to their Uber account.
* **Transportation with DL and AI at Uber:** Recently, Uber has started using **machine learning (ML), artificial intelligence (AI),** and advanced technologies to create positive experiences for users. They introduced a Bayesian neural network architecture that can estimate trip growth more accurately. Among other areas, they use ML to enable an efficient ride-sharing marketplace, identify suspicious accounts, and suggest optimal pickup and drop off points.
* **Problem space:** Uber's problem is new and rapidly evolving, especially at the scale and intersection of dimensions:
  * **Temporal:** From seconds to years.
  * **Spatial:** At both micro levels (riders, cars, and goods) and macro levels (global, regional, and city).
  * **Active:** Immediate impact and response to the system.
  * **Human:** Involved at every stage, starting from decision making to decision receipt.
  * **Scale:** Millions of calculations and thousands of decisions made for riders and drivers every minute.

## Designing Uber maps

Maps represent the physical world that is built on data, and Uber's primary mission is too tied to the ability to use this data to refine the mapping technologies. Aspects such as prediction and destination search, ETAs, generation of map tiles, routing, and fare estimates, maps are essential in every element of a logistics network. They can be represented visually by maps that cover more than 95 percent of pixels on the rider.

Uber uses ML to improve their maps. Destination prediction fulfills problems of all destination entries and tests the accuracy of models:

![](OEBPS/images/Figure-3.6.jpg)

**Figure 3.6:** Flow of designing Uber maps

The destination prediction process consists of five distinct steps:
1. Rider books taxi to ride.
2. The service retrieves details of the rider from the stored feature and ranks them by providing latitude, longitude and time.
3. The system service returns the first seven destination suggestions along with selected candidates from places where people have previously traveled and searched.
4. By using a combination of information about the physical world along with ML, the service produces a list of places along with the set of features, including a histogram of popular destinations with corresponding request times and the current time.
5. A machine-learned scorer then ranks these suggested places, taking feedback from another model that learned to train how to weight all the components separately.

## Uber service architecture

In the marketplace, some models describe the world and the decision engines that act on the models. The following diagram illustrates the architecture of Uber service:

![](OEBPS/images/Figure-3.7.jpg)

**Figure 3.7:** Architecture diagram of Uber service

This architecture diagram shows the working of Uber. On the left-hand side, it's mostly where the data comes from, that is, all the applications, services, and databases. They all go into one central piece, which is `Kafka`. From here, many services pull the data through consumers. `Surge` pulls data to do some fair calculations.

`ELK` (`Elasticsearch`, `Logstash`, and `Kibana`) is the logging stack. It is used to provide real-time reporting dashboards used for debugging, reporting, and auditing. `Samza` and `Flink` pull data to do real-time data processing. The same data is sent to `S3` for cold storage, where it can be kept for archives. The same `Kafka` has `Hadoop` as a consumer. Once information is stored in `Hadoop`, it can be used for batch processing, ad hoc queries, and data exploration. `Hadoop`'s data repository is used to run data science applications.

## Conclusion

After this tour around decision making and human reasoning, we can draw some conclusions. The first is that decision theory and AI are only at the beginning of their mutual cross-fertilization. The decision theory is all about making the best decision, either in a particular or uncertain world with the available choices. AI has focused much attention on diagnosis and human knowledge representing and recording. It is only a few years following its first embraced uncertainty and has practically never dealt with decisions. For some reason, the planning process starts after the decision is made since the result of the decision is the goal. It is indeed possible to ignore the preferences and to help a user find the right path from the current state to their goal, but AI cannot carry out that plan without paying attention to uncertainty. So, AI and decision theory appear to be mainly complementary— diagnosis representation and handling of the recorded states for AI, look-ahead, uncertainty, and preferences for decision theory.

## Questions

1. What are the main steps to solve a problem? Describe each of them briefly.
2. Describe different types of knowledge.
3. What is AI cycle? What are the main steps involved in it? Describe each step briefly.
4. What are the different steps involved in the development cycle of a model? Describe each step briefly.

# Chapter 4

## Intelligent Computing Strategies by Google
