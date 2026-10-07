# Chapter 12 ■ Document Metadata 255

Each module has its own set of parameters and descriptions, which you can view by loading the module and using the show info command. Let's get info on the Flickr module:

```
[recon-ng] [default] > use flickr
[recon-ng] [default][flickr] > show info
```

Name: Flickr Geolocation Search
Path: modules/recon/locations-pushpins/flickr.py
Author: Tim Tomes @LaNMaSteR53
Keys: flickr_api

Description:
Searches Flickr for media in the specified proximity to a location.

Options:

| Name Current Value Required Description |
| --- | --- | --- | --- |
| RADIUS | 1 | yes | radius in kilometers |
| SOURCE | default | yes | source of input (see 'show info' for details) |

```
Source Options:
default SELECT DISTINCT latitude || ',' || longitude FROM locations WHERE latitude IS NOT NULL AND longitude IS NOT NULL
<string> representing a single input
<path> path to a file containing a list of inputs
<query sql> database query returning one column of inputs
```

Comments:

+   * Radius must be greater than zero and less than 32 kilometers.

We can see from the module's information page that we need to have the coordinates of an address as well as the address before we can use the module. Plenty of free tools are available to do this. One example is https://www.mapdevelopers.com/geocode_tool.php. After visiting the website, enter your desired address, and it will return your latitude and longitude coordinates. For example, I used the coordinates of St. Louis, MO. The MapDeveloper .com returned the following:

```
Latitude 38.633716
Longitude -90.2416548
```

Now that we have location coordinates, let's see what kind of information we find in the Pushpin module.
First, we need to add the location to Recon-NG using the add locations command:

```
[recon-ng] [default][geocode] > add locations
latitude (TEXT): 38.633716
```