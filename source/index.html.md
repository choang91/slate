---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - json
  - java
  - javascript

# toc_footers:
#   - <a href='#'>Sign Up for a Developer Key</a>
#   - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Welcome to Ansel Adams API

Welcome to the Ansel Adams API! You can use our API to access Ansel Adams API endpoints, which can get information on various users, locations, regions, and images in our database.

We have language bindings in Shell, Java, and sample JSON response! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Core API Endpoints

BaseUrl: `34.204.68.134:9090/anseladams`

## Get User Info from Google
`GET http://[BaseUrl]/google/user/detail`

### Description
Retrieve user info from Google, register info to the database if user does not exist

### Request headers
Parameter | Description | Required?
-------------- | -------------- | --------------
idToken | Google login token | Yes

### Request parameters
N/A

### Sample response

## Get User Info from Facebook
`GET http://[BaseUrl]/facebook/user/detail`

### Description
Retrieve user info from Facebook, register info to the database if user does not exist

### Request headers
Parameter | Description | Required?
-------------- | -------------- | --------------
userAccessToken | Facebook login token | Yes

### Request parameters
N/A

### Sample response
```json
{
  "userId": 3,
  "name": "John Doe",
  "email": "jdoe@yahoo.com",
  "userAccessToken": "EAACDY0zCZBiMBAJSh3I...",
  "provider": "facebook",
  "providerId": "148...",
  "imageUrl": "https://scontent.xx.fbcdn.net/v/t1.0-1/..."
}
```


## Get the Front Image
`GET http://[BaseUrl]/front-image`

### Description
Retrieve the front image (displayed after user logs in)

### Request headers
N/A

### Request parameters
N/A

### Sample response
```json
{
    "frontImageId": 1,
    "s3Key": "misc/1513282549_Ansel-Adams-Portrait-Inner-Banner1.png",
    "url": "https://anseladams-samples.s3-us-west-1.amazonaws.com/misc/1515189041_Ansel-Adams-Portrait.jpg"
}
```

## Get All Albums
`GET http://[BaseUrl]/albums`

### Description
Retrieve all albums

### Request headers
N/A

### Request parameters
N/A

### Sample response
```json
[
  {
    "albumId": 4,
    "name": "Yosemite",
    "defaultImageUrl": "https://anseladams-samples.s3-us-west-1.amazonaws.com/albums/Yosemite/1513309458_HD%20Blowing%20Snow%20AA.jpg"
  },
  {
    "albumId": 7,
    "name": "My Ansel Album",
    "defaultImageUrl": null
  }
]
```

## Get Images from an Album
`http://[BaseUrl]/albums/{albumId}/images`

### Description
Retrieve images belonging to an album

### Request headers
N/A

### Path variables
Variable | Description | Required?
-------------- | -------------- | --------------
albumId | Album ID | Yes

### Sample response
```json
[
  {
    "imageId": 6,
    "name": null,
    "description": null,
    "latitude": 0,
    "longitude": 0,
    "s3Key": "albums/My Album/1513281804_Jeffrey Pine, Sentinel Dome.jpg",
    "url": "https://anseladams-samples.s3-us-west-1.amazonaws.com/albums/My%20Album/1513281804_Jeffrey%20Pine%2C%20Sentinel%20Dome.jpg",
    "album": {
        "albumId": 5,
        "name": "My Album",
        "defaultImageUrl": "https://anseladams-samples.s3-us-west-1.amazonaws.com/albums/My%20Album/1513310867_Jeffrey%20Pine%2C%20Sentinel%20Dome.jpg"
    },
    "location": null,
    "region": null,
    "createdDate": -1,
    "modifiedDate": -1
  }
]
```
<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->
## Get All Locations
`GET http://[BaseUrl]/locations`

### Description
Retrieve all locations

### Request headers
N/A

### Request parameters
N/A

### Sample response
```json
[
  {
    "locationId": 1,
    "name": "Yosemite National Park",
    "defaultImageUrl": "https://anseladams-samples.s3-us-west-1.amazonaws.com/locations/Yosemite%20National%20Park/1513285458_Yosemite_map.png",
    "latitude": 37.859481,
    "longitude": -119.533293
  }
]
```

## Get Images from a Location
`GET http://[BaseUrl]/locations/{locationId}/images`

### Description
Retrieve images from a location

### Request headers
N/A

### Path variables
Variable | Description | Required?
-------------- | -------------- | --------------
locationId | Location ID | Yes

### Sample response
```json
[
  {
    "imageId": 6,
    "name": null,
    "description": null,
    "latitude": 0,
    "longitude": 0,
    "s3Key": "albums/My Album/1513281804_Jeffrey Pine, Sentinel Dome.jpg",
    "url": "https://anseladams-samples.s3-us-west-1.amazonaws.com/albums/My%20Album/1513281804_Jeffrey%20Pine%2C%20Sentinel%20Dome.jpg",
    "album": {
        "albumId": 5,
        "name": "My Album",
        "defaultImageUrl": "https://anseladams-samples.s3-us-west-1.amazonaws.com/albums/My%20Album/1513310867_Jeffrey%20Pine%2C%20Sentinel%20Dome.jpg"
    },
    "location": null,
    "region": null,
    "createdDate": -1,
    "modifiedDate": -1
  }
]
```

<!--  -->
## Get All Region
`GET http://[BaseUrl]/regions`

### Description
Retrieve all regions

### Request headers
N/A

### Request parameters
N/A

### Sample response
```json
[
  {
    "regionId": 3,
    "name": "California",
    "defaultImageUrl": "https://anseladams-samples.s3-us-west-1.amazonaws.com/regions/California/1515109591_AA%2C%20Lone%20Pine%20Peak%20%26%20Rocks.JPG",
    "imagesCount": 5,
    "latitude": 36.522,
    "longitude": -121.922
  }
]
```

## Get Images from a Region
`GET http://[BaseUrl]/regions/{regionId}/images`

### Description
Retrieve images from a region

### Request headers
N/A

### Path variables
Variable | Description | Required?
-------------- | -------------- | --------------
regionId | Region ID | Yes

### Sample response
```json
[
  {
    "imageId": 1024,
    "name": "Bridal Veil Fall",
    "description": null,
    "latitude": 37.717475,
    "longitude": -119.650078,
    "s3Key": "regions/Yosemite/1515191111_IMG_3557.jpg",
    "url": "https://anseladams-samples.s3-us-west-1.amazonaws.com/regions/Yosemite/1515191111_IMG_3557.jpg",
    "album": null,
    "location": null,
    "region": {
      "regionId": 7,
      "name": "Yosemite",
      "defaultImageUrl": "https://anseladams-samples.s3-us-west-1.amazonaws.com/regions/Yosemite/1515191111_IMG_3557.jpg",
      "imagesCount": 7,
      "latitude": 37.716,
      "longitude": -119.646
    },
    "createdDate": 1515191112447,
    "modifiedDate": 1515191112447
  }
]
```

# Admin API Endpoints
BaseUrl: `34.204.68.134:9090/anseladams`

## Create an Album
`POST http://[BaseUrl]/albums`

### Description
Create a new album

### Request headers
Parameter | Description | Required?
-------------- | -------------- | --------------
albumName | New album name | Yes

### Request parameters
N/A

### Sample response

## Create a Location
`POST http://[BaseUrl]/location`

### Description
Create a new location

### Request headers
Parameter | Description | Required?
-------------- | -------------- | --------------
locationName | New location name | Yes
latitude | Location latitude | Yes
longitude | Location longitude | Yes

### Request parameters
N/A

### Sample response

## Create a Region
`POST http://[BaseUrl]/regions`

### Description
Create a new region

### Request headers
Parameter | Description | Required?
-------------- | -------------- | --------------
regionName | New region name | Yes
latitude | Region latitude | Yes
longitude | Region longitude | Yes

### Request parameters
N/A

### Sample response