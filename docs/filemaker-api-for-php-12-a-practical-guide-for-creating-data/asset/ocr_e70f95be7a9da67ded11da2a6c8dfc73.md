# Lesson 39: Google Map API Store Locator

**Objective:** In this lesson you will learn how to integrate the Google map API. If you've been trying to integrate Google maps into your FileMaker PHP site I know you've looked at their code and ever gave up or lost of time suffering through countless pages of documentation and JavaScript. As of May 2011 Brad Welled released a phenomenal PHP class that makes Google Maps extremely easy to use. Although it's "officially supported" by Google because it's not an in-house project, they did present it at their conference and provided Brad with a very nice site using their domain. That tells me that Google really likes it and so do I. You can find more information about the class at:

```
http://code.google.com/p/php-google-map-api/
```

**Difficulty:** Difficult

**Sample Files:
PHPFiles/Advanced/Lesson39/GoogleMap.php
PHPFiles/Advanced/Lesson39/JSMIn.php
PHPFiles/Advanced/Lesson39/StoreLocator.php
PHPFiles/Advanced/Lesson39/StoreLocator.f12

This lesson uses a separate database file to demonstrate the lesson. Please upload the StoreLocator.fmp2 database file to your server.

![](bbox=[0.12135, 0.38335, 0.976, 0.43335])

**Page Navigation:**

| List |
|---|

**FileMaker API Methods:
newPerformScriptCommand(
getRecords(
getField(


**Code:**

There are so many features available in Brad's V3 release that I could spend a tremendous time to present a few of the most common requests from developers to cover everything. Rather than that I'm going to acquire and insert it into your own database. My goal is to transform the existing documentation (or lack thereof) and example code into something useful for the FileMaker developer community. The first example will be creating a store locator that utilizes Google's Geocoding service to find and display records from the database with userdefined distance.

The database has fields for name, address, city, and state. Those should be obvious. Next there are fields for the Latitude (Lat) and Longitude (Lon) of the restaurant. I've provided the data for the records. In the next lesson I will show you how to acquire and insert it into your own records. The SearchLocation, and Distance fields are used by the Store locator to find records based on user supplied. The Distance calculation uses the Great Circle Navigation Formula (a.k. Haversine formula) to calculate the distance between the user's location and each of stores. More information about the formula can be found from my article, Map Distance, that I published using FileMaker Pro 9 at:

```
http://www.formulations.com/pages/filemaker/detail.php?id=213
```

or: