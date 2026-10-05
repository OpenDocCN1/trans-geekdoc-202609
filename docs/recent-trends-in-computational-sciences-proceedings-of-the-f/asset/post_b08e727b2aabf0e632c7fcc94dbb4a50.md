
# Implementation of reverse geocoding using Python and C# tools

R. Jyothi
Global Academy of Technology

K. Janani
Koneru Lakshmaiah Educational Foundation

R. Varshinee
Global Academy of Technology
ORCID ID: 0000-0002-4050-8322

ABSTRACT: Reverse geocoding is a process in which a location is accessed using latitude and longitude coordinates. Reverse Geocoding helps lot of people in locating addresses. It helps industries, postal department, transport and communication. Traffic police officers often have great difficulties in locating places where traffic rules are violated. Traffic violators take this lapse to escape from scene of crime. Reverse Geocoding provides a paramount role in locating the place quickly so that the traffic police can catch the culprits without any hassles or delay. We propose to develop an application by providing the latitude and longitude coordinates to a place, a map consisting of the location of the place is displayed using python modules. We implemented Reverse Geocoding using Python and C# tools. Implementation using C# tools is better without internet connection. This notably less connectivity issues during the usage of the system in remote areas.

Keywords: Basemap, Reverse Geocoding, matplotlib, geopy, Coordinates based service

## 1 INTRODUCTION

The world has become a global Village due to the digital revolution. The internet provides service in connecting people all over the world. People over the world speak different languages. The rapid technological development in the field of digital communication led to connection of people all over the world. It has paved the way for industrial development. It plays a vital role in ecommerce. It has become a paramount power in economic growth of both individuals and countries.

Reverse Geoc acts as a very useful tool in detection of places just by providing coordinates of the place. It is a unifying mechanism that helps people of different places speaking different languages to locate easily.

Reverse Geocoding can be implemented using various tools for effortless detection of places using coordinates. Certain tools may rely on internet infrastructure and may not. The use of tools online and offline is the advantage of a system that works both online may depend upon variations of applications. The application does not require prerequisites such as knowledge about software. Another benefit of such a system is rapid yielding of results. A drawback of the application obtained by Python tools could be internet. This means that the application requires internet for its successful implementation. However it does not yield the output. This may be a disadvantage for places lacking internet connection. To overcome that one can use the application obtained by C# tools which is memory for reading the map data becomes the database. For sharing the cache with multiple users secondary cache database with SQL server can be used. The GPS coordinates can be converted into human readable Street addresses easily swiftly. It also helps people to find the nearby location of their places.

Reverse geocoding is highly useful in remote place of districts and other areas. [3] It is also used in governmental bodies for security reasons.
Reverse geocoding is of immense help to army, navy, police department. It paved the way for more exploration and research on unknown places. It acts a bridge between human and landscape of the earth. [2] There is a possibility of unravelling many mysteries to reduce crime rate. The role played by reverse geocoding is laudable in the time of natural disasters such as floods, earthquakes, cyclone, etc. Reverse geocoding helps in rescuing stranded people with python tools:

- 1. The Python module geopy this tool helps to locate latitude and longitudes of addresses, cities, across the globe. It uses geocoders and other data sources. It is also used to calculate the distance between different places.
- 2. Nominatim This tool helps to search street map data. The process involves using address or location. Nominatim is included in the geopy library. mpltools is a python package for plotting the multiple vectors of geometric algebra using matplotlib. [8] It is numerical-mathematical extension for NumPy which is used for working with arrays, domain of linear algebra and mathematics. [1] Pyplot is a state-based interface to a matlab module. It can be used in line plot, histogram, 3-D plot, etc.
- 4. Basemap is an import for creating maps using Python without any hassles. It is a matlab extension. It got all features to create data visualizations to plot coastlines, countries, etc.

C# tools used:
GMap.Net Windows Forms & Presentation is a free and powerful open cross-platform.NET control. We downloaded the package via nuget as we used as package manager. GMap.Net can be used to place a map on a form and it is also used to initialize the map to show the desired coordinates. It also the functionality of adding markers and polygons to the map. We created a new C# Forms project in Visual Studio 2019. In GMap.Net download, DLLs named GMap.Net.Core.dll and GMap.Net.Forms.dll can be found. They have to be in a subfolder of the project, and a reference must be added to it. It allows maps from Google, Yahoo!, Bing, OpenStreetMap, ArcGIS, Pergo, Yandex, Mupy.cy, Maps.lt, iKarte.lv, NearMap, HereMap, CloudMade, It is also used for routing, geocoding, etc.

## 2 WORKING METHODOLOGY

With Python implementation, using Basemap, different maps can be used for the display of location. We used a Miller cylindrical projection map. The size and resolution of the map can be altered. Basemap includes coastline dataset as well as datasets for rivers, state and country boundaries from GMT. These datasets can be used to draw coastlines, river and political boundaries at different resolutions.

The address on the map is printed using annotate() method in the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.
To display the address of the map the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.
To display the address of the map the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.

Reverse geocoding is highly useful in remote place of districts and other areas. [3] It is also used in governmental bodies for security reasons.
Reverse geocoding is of immense help to army, navy, police department. It paved the way for more exploration and research on unknown places. It acts a bridge between human and landscape of the earth. [2] There is a possibility of unravelling many mysteries to reduce crime rate. The role played by reverse geocoding is laudable in the time of natural disasters such as floods, earthquakes, cyclone, etc. Reverse geocoding helps in rescuing stranded people with python tools:

- 1. The Python module geopy this tool helps to locate latitude and longitudes of addresses, cities, across the globe. It uses geocoders and other data sources. It is also used to calculate the distance between different places.
- 2. Nominatim This tool helps to search street map data. The process involves using address or location. Nominatim is included in the geopy library. mpltools is a python package for plotting the multiple vectors of geometric algebra using matplotlib. [8] It is numerical-mathematical extension for NumPy which is used for working with arrays, domain of linear algebra and mathematics. [1] Pyplot is a state-based interface to a matlab module. It can be used in line plot, histogram, 3-D plot, etc.
- 4. Basemap is an import for creating maps using Python without any hassles. It is a matlab extension. It got all features to create data visualizations to plot coastlines, countries, etc.

C# tools used:
GMap.Net Windows Forms & Presentation is a free and powerful open cross-platform.NET control. We downloaded the package via nuget as we used as package manager. GMap.Net can be used to place a map on a form and it is also used to initialize the map to show the desired coordinates. It also the functionality of adding markers and polygons to the map. We created a new C# Forms project in Visual Studio 2019. In GMap.Net download, DLLs named GMap.Net.Core.dll and GMap.Net.Forms.dll can be found. They have to be in a subfolder of the project, and a reference must be added to it. It allows maps from Google, Yahoo!, Bing, OpenStreetMap, ArcGIS, Pergo, Yandex, Mupy.cy, Maps.lt, iKarte.lv, NearMap, HereMap, CloudMade, It is also used for routing, geocoding, etc.

## 2 WORKING METHODOLOGY

With Python implementation, using Basemap, different maps can be used for the display of location. We used a Miller cylindrical projection map. The size and resolution of the map can be altered. Basemap includes coastline dataset as well as datasets for rivers, state and country boundaries from GMT. These datasets can be used to draw coastlines, river and political boundaries at different resolutions.

The address on the map is printed using annotate() method in the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.
To display the address of the map the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.
To display the address of the map the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.

The use of tools online and offline is the advantage of a system that works both online may depend upon variations of applications. The application does not require prerequisites such as knowledge about software. Another benefit of such a system is rapid yielding of results. The drawback of the application obtained by Python tools could be internet. This means that the application requires internet for its successful implementation. However it does not yield the output. This may be a disadvantage for places lacking internet connection. To overcome that one can use the application obtained by C# tools which is memory for reading the map data becomes the database. For sharing the cache with multiple users secondary cache database with SQL server can be used. The GPS coordinates can be converted into human readable Street addresses easily swiftly. It also helps people to find the nearby location of their places.

Reverse geocoding is highly useful in remote place of districts and other areas. [3] It is also used in governmental bodies for security reasons.
Reverse geocoding is of immense help to army, navy, police department. It paved the way for more exploration and research on unknown places. It acts a bridge between human and landscape of the earth. [2] There is a possibility of unravelling many mysteries to reduce crime rate. The role played by reverse geocoding is laudable in the time of natural disasters such as floods, earthquakes, cyclone, etc. Reverse geocoding helps in rescuing stranded people with python tools:

- 1. The Python module geopy this tool helps to locate latitude and longitudes of addresses, cities, across the globe. It uses geocoders and other data sources. It is also used to calculate the distance between different places.
- 2. Nominatim This tool helps to search street map data. The process involves using address or location. Nominatim is included in the geopy library. mpltools is a python package for plotting the multiple vectors of geometric algebra using matplotlib. [8] It is numerical-mathematical extension for NumPy which is used for working with arrays, domain of linear algebra and mathematics. [1] Pyplot is a state-based interface to a matlab module. It can be used in line plot, histogram, 3-D plot, etc.
- 4. Basemap is an import for creating maps using Python without any hassles. It is a matlab extension. It got all features to create data visualizations to plot coastlines, countries, etc.

C# tools used:
GMap.Net Windows Forms & Presentation is a free and powerful open cross-platform.NET control. We downloaded the package via nuget as we used as package manager. GMap.Net can be used to place a map on a form and it is also used to initialize the map to show the desired coordinates. It also the functionality of adding markers and polygons to the map. We created a new C# Forms project in Visual Studio 2019. In GMap.Net download, DLLs named GMap.Net.Core.dll and GMap.Net.Forms.dll can be found. They have to be in a subfolder of the project, and a reference must be added to it. It allows maps from Google, Yahoo!, Bing, OpenStreetMap, ArcGIS, Pergo, Yandex, Mupy.cy, Maps.lt, iKarte.lv, NearMap, HereMap, CloudMade, It is also used for routing, geocoding, etc.

## 2 WORKING METHODOLOGY

With Python implementation, using Basemap, different maps can be used for the display of location. We used a Miller cylindrical projection map. The size and resolution of the map can be altered. Basemap includes coastline dataset as well as datasets for rivers, state and country boundaries from GMT. These datasets can be used to draw coastlines, river and political boundaries at different resolutions.

The address on the map is printed using annotate() method in the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.
To display the address of the map the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.
To display the address of the map the address addressed on the street, latitude and longitude coordinates and the size specifications are as arguments.

![img/a35f8e852e0ee65e28c95ad0821783b_263_0.png](img/a35f8e852e0ee65e28c95ad0821783b_263_0.png)

![img/a35f8e852e0ee65e28c95ad0821783b_263_1.png](img/a35f8e852e0ee65e28c95ad0821783b_263_1.png)
